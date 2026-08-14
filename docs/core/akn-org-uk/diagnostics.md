---
sidebar_position: 4
title: Diagnostics
---

# Diagnostics

Observed conditions and their resolutions.

## Arriving

| Condition | Cause | Resolution |
|-----------|-------|------------|
| The window is filled by the mark and a phrase | The opening animation is running. Scrolling is locked until it ends | Wait three to four seconds |
| The opening animation did not play | It has already played in this browsing session, or reduced motion is set | Open the site in a new tab, or add `?intro=` to the address |
| The opening animation plays on every load | The browser is blocking site storage, so previous arrivals are not recognised | Allow storage for the site, or set reduced motion |
| `?intro=` was added but nothing played | Reduced motion overrides the address | Turn off reduced motion |
| Type renders in a substitute typeface | The typefaces load from an external network | Reload with the network available |

## Navigating

| Condition | Cause | Resolution |
|-----------|-------|------------|
| No section links appear in the header | The window is narrower than 620 pixels | Scroll, or widen the window |
| The header underline sits on **Approach** while reading What AKN does | That section carries no header link of its own | No action required |
| Sections appear without any entrance animation | Animation resources load from an external network and were unavailable | Reload with the network available. All content is present either way |
| A header link jumps rather than scrolling | Reduced motion is set | No action available |

## Products and contact

| Condition | Cause | Resolution |
|-----------|-------|------------|
| A product card opened a tab that will not load | The product runs on its own site, separate from this one | Retry from the footer link, or check https://status.akn.me.uk |
| Selecting a contact control does nothing | No mail application is configured on the device | Send to `enquiries@akn.org.uk` from webmail |
| No contact form is visible | The site publishes none. Contact is by email only | Use `enquiries@akn.org.uk` |
| A product name in the scrolling band cannot be selected | The band is decorative | Use the product cards or the footer links |

## Motion and display

| Condition | Cause | Resolution |
|-----------|-------|------------|
| A panel of sliders appeared unexpectedly | Three clicks within half a second open the artwork tuner | Close it with **✕**, or click three times again |
| Tuner values were lost | Values are held for the current page only | Reapply them. There is no saved setting |
| The hero artwork is not moving | Reduced motion is set, or the artwork is scrolled out of view | Turn off reduced motion, or scroll it back into view |
| Card borders do not light up under the pointer | The window is 900 pixels wide or narrower, or the device uses touch input | Widen the window, or use a mouse or trackpad |
| The page has no dark appearance | One fixed palette is published | No action available |

## Escalation

Conditions not resolved by the above should be reported to
`enquiries@akn.org.uk`. Include the address, the browser, and the time the
condition occurred.

Service availability is published at https://status.akn.me.uk.

## Related

- [Overview](overview.md)
- [Using the site](using.md)
- [Motion and display](motion.md)
