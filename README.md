# SharePoint Online: View by Default

![Banner Image](assets/promotional/marquee.png)

A modernised, Manifest V3 (MV3) compliant fork of [spo_view_it](https://github.com/jftuga/spo_view_it).

---

## Overview

SharePoint Online opens documents in **Edit** mode by default. This extension rewrites a URL parameter on navigation to force **View** mode instead, preventing accidental edits.

Switching back to Edit mode works as normal — the extension does not interfere with SharePoint's own mode-switching behaviour.

---

## Implementation

When SharePoint Online loads a document, the URL contains parameters such as: `&action=default&mobileredirect=true`

The extension rewrites these to: `&DefaultItemOpen=1&Action=View`

This is handled entirely by a static `declarativeNetRequest` ruleset — no JavaScript or service worker is required. The rule activates only on URLs matching `https://*.sharepoint.com/*`.

---

## Permissions

| Permission | Reason |
| ---------- | ------ |
| `declarativeNetRequest` | Applies the static URL rewrite rule |
| `https://*.sharepoint.com/*` | Scopes the rule to SharePoint Online only |

No data is read, stored, or transmitted.

---

## Installation

> [!NOTE]  
> This extension is not yet available on the Chrome Web Store  
> Manual installation is required

1. Clone or download this repository.
2. Open Chrome and navigate to `chrome://extensions`.
3. Enable **Developer mode** in the top right.
4. Click **Load unpacked** and select the extension folder.

---

## Acknowledgement

Based on [spo_view_it](https://github.com/jftuga/spo_view_it) by [@jftuga](https://github.com/jftuga).
