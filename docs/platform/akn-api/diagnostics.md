---
sidebar_position: 9
title: Diagnostics
---

# Diagnostics

Conditions observed while integrating, grouped by task.

## Sessions

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `POST /auth/verify` returns 200 and no cookie is set | The response carried `approved: false` | Read the field. A refusal is not an error status |
| Cookie is set but never sent back | The request omitted credentials, or the origin is outside the allowlist | Send credentials with the request, from an allowed origin |
| Every call answers 401 after two weeks | The session reached its 14-day limit | Sign in again and call `POST /auth/verify` |
| `POST /auth/session/refresh` answers 401 immediately after a successful verify | The cookie was not stored, or is being sent to a host outside `.akn.me.uk` | Call from an akn subdomain over `https` |
| Sessions end sooner than 14 days in one browser only | The cookie was cleared locally, or `POST /auth/logout` was called there | Sign in again. Logout affects only the browser that called it |
| An approved person is refused on one endpoint and accepted on another | The refusing endpoint requires a project grant | Request the grant named on the endpoint's page |
| 503 `Authorization unavailable` | The account lookup failed. The credential is intact | Retry with backoff. Do not sign the person out |

## Sign-in

| Condition | Cause | Resolution |
|-----------|-------|------------|
| A person who signed in before now has a second, pending account | They signed in by a method proving an identifier nobody had claimed | Link the identity to the existing person, then remove the duplicate's grants |
| Phone sign-in answers 403 `phone_not_linked` | The number is on no account. Phone signs in an existing person only | Sign in another way, add the number to the account, then retry |
| Email code never arrives | The address holds no account and the purpose was `signin` | Send with `purpose: request-access`, or sign in another way |
| `POST /auth/otp/send` answers 200 repeatedly with no mail | Sign-in requests for unknown addresses answer identically to a send | Confirm the address is on the account |
| 429 on a code request | A code was sent within 60 seconds, or five were sent within the hour | Wait for the interval stated in the message |
| A correct code is rejected | Five wrong attempts destroyed it, or 10 minutes passed | Request a new code |
| `POST /auth/otp/sign-in` answers 400 after `verify` answered `valid: true` | The code was consumed, or expired between the two calls | Request a new code and call sign-in directly |
| Bridge sign-in answers 400 `Sign-in expired` | The state cookie is missing, altered, or more than 10 minutes old | Start again from `/auth/bridge/:provider/start` |
| Bridge start answers 400 `Bad redirect` | The `redirect` value is not `https` on an akn hostname | Use an allowed destination |
| Bridge errors fail to parse | Bridge errors are HTML pages | Branch on the status code rather than parsing the body |

## Relying party integration

| Condition | Cause | Resolution |
|-----------|-------|------------|
| Discovery answers 404 | The client fetched the well-known path under the issuer host and the request did not reach the root path | Use `https://api.akn.me.uk/.well-known/openid-configuration` |
| `invalid_client` at the authorise request | The client id is not registered | Have the client registered by the site operator |
| `invalid_request` naming the redirect URI | The URI does not match the registered allowlist exactly | Register the exact URI, including scheme, host, path and trailing characters |
| Nothing arrives at the callback and no error appears | The authorise request was refused, and refusals are returned to the caller rather than redirected | Inspect the response to `/auth/oidc/authorize` |
| The person reaches an HTML page saying they have no access | The client requires a project grant the person does not hold | Grant the named project |
| `invalid_grant` on a code issued moments earlier | The code is older than two minutes, already redeemed, or the redirect URI differs from the authorise request | Redeem immediately, with an identical redirect URI |
| `invalid_grant` naming PKCE | A challenge was sent without a matching verifier | Send `code_verifier`, or stop sending a challenge |
| `/auth/oidc/userinfo` answers 401 with a token issued minutes ago | Access tokens do not survive a service restart | Repeat the authorisation code flow |
| Sign-ins in flight fail together, then recover | Pending requests are held for the life of the process | Retry the sign-in |
| An account is matched to the wrong person by email | `email_verified` was false and the client keyed on the address | Key on `sub`, and treat an unverified address as unproven |
| The claims target answers 403 `invalid_signature` | The signature is missing, wrong, or the timestamp is more than 300 seconds out | Correct the shared secret, and the clock |
| A token arrives with no `urn:akn:` claims | No person resolved, or the lookup failed. The two are indistinguishable | Treat missing claims as no access |

## Administration

| Condition | Cause | Resolution |
|-----------|-------|------------|
| A person is missing from `GET /auth/people` | The list returns the 200 most recently created only | Read the person directly by `personId` |
| `PATCH` answers 200 but the person still cannot sign in | An identity update failed. Failures are listed in the response | Read `firebaseSyncErrors` and retry |
| Linking answers 409 | The identity already belongs to another person | Unlink it from that person first |
| An unlinked identity reappears after the person signs in | Unlinking leaves the identifiers that resolve them | Expect re-linking. There is no endpoint to remove an identifier |
| A sync run stops with no response | Runs are sequential per account and exceed the proxy timeout on large directories | Treat partial results as final and rerun |
| A sync attaches accounts to the wrong people | Sync matches by email address alone, unlike sign-in, which requires a proved identifier | Run only against a directory whose addresses are trusted |
| Grants changed but the person still passes the old check | A grant applies from the next request. Tokens already issued carry the old values | Wait for the token to expire, or have the person sign in again |
| An admin is refused by the `/status` endpoints | Those endpoints read a legacy account record rather than the person record | Ask the operator to add the legacy record, or use another administrator account |

## Feeds

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `GET /calendar/events` returns an empty array on a busy week | Upstream failure and an empty week are reported identically | Retry. Escalate if it persists across a known-busy period |
| Notifications repeat on every poll | The poll sent no `since`, so the latest 20 are returned each time | Send `since` set to the newest `created_at` already held |
| Older notifications cannot be reached | Each request returns at most 20 entries and no pagination is offered | Poll continuously rather than backfilling |
| `POST /startpage/notify` answers 401 | The key is absent or wrong | Confirm the key. It is sent in `x-api-key`, not `Authorization` |
| A notification arrives with source `other` | The submitted source was not a recognised value | Send `android` or `openclaw` |
| A status change is lost | Incident and URL edits are read-modify-write against one revision | Reload before each change, and avoid concurrent editing |
| A resolved incident cannot be reopened | Resolution moves it out of the active list with no reverse action | Create a new incident |

## Location

| Condition | Cause | Resolution |
|-----------|-------|------------|
| `location` reads `Location unavailable` | No position could be obtained and nothing is cached | Retry later. There is no error status to trap |
| The same body is returned for 30 minutes | The cached value is served while a refresh runs behind it | Call `/location/live` when the newest fix is required |
| `stale: true` with a plausible city | The position is more than 24 hours old | Present it as a last known place, not a current one |
| `confidence` is `unknown` | A place is known and its time is not | Show the place without a time |
| `historyPast` is short or empty | Positions without a place name are resolved against a geocoder under a per-request budget, and skipped beyond it | Expect gaps |
| An expected trip is missing from `historyFuture` | Places are inferred from calendar text against a fixed list of cities | Expect coverage only for known cities |
| `/location/last-visit` reports `Unknown` | No visit has been recorded, or the stored record was unavailable | Record a visit, then retry |
| A visitor city cannot be removed | One record is retained and overwritten by the next visit. No removal endpoint exists | Record another visit to displace it |

## Escalation

Report unresolved conditions to the site operator with the method, the path, the
status code, the response body, and the time.

Service availability is published at https://status.akn.me.uk.

## Related

- [Overview](overview.md)
- [Authentication](authentication.md)
- [Errors](errors.md)
