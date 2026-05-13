# Webhooks

Webhooks let Quor notify your services automatically whenever something
interesting happens with the container images you subscribe to — no extra
pipeline configuration required. Instead of polling Quor's API, you point
Quor at an HTTPS endpoint you control and Quor calls you when an event
fires.

This page documents every piece of the Webhooks feature available in the UI:
the list page, the creation drawer, the details/edit drawer, validation
rules, delivery semantics, and event types.

> ![PLACEHOLDER: Webhooks page overview — full screenshot of `/webhooks` with several active and disabled webhook cards](./images/webhooks/overview.png)

---

## Accessing Webhooks

Webhooks live in the authenticated area of the app at the route `/webhooks`.
The page is part of the protected layout and requires an authenticated
Quor session.

The page header shows the title **Webhooks** and a primary **Add Webhook**
button on the right side.

> ![PLACEHOLDER: Header area with "Webhooks" title and the "+ Add Webhook" button](./images/webhooks/header.png)

---

## The Webhooks list

The body of the page renders all webhooks belonging to the currently
selected organization in a responsive 3-column grid.

Each webhook is represented by a **card** containing:

- **Name** — the human-readable label you gave the webhook.
- **Status badge** — either a green **Active** badge or a neutral
  **Disabled** badge, depending on whether the webhook is currently
  receiving events.
- **URL row** — the endpoint URL with a one-click copy-to-clipboard
  button.
- **Subscribed images** — a list of image badges showing which
  subscriptions trigger the webhook. If the webhook is subscribed to
  every image in the organization, this collapses into a single
  **All subscribed images** badge.

Clicking anywhere on a card opens the **Webhook details** drawer for that
webhook.

> ![PLACEHOLDER: Single webhook card showing name, Active badge, URL with copy icon, and image badges](./images/webhooks/card.png)

---

## Creating a webhook

Clicking **Add Webhook** opens the **Add webhook** drawer, sliding in
from the right of the screen.

> ![PLACEHOLDER: "Add webhook" drawer fully open with empty form fields](./images/webhooks/create-drawer.png)

The form has four fields, rendered in this order.

### 1. Name

A free-text input. Required. Used as the card title and as the label in
the details drawer.

- Placeholder: *e.g., Platform Team Slack*
- Validation: required — empty submissions show **"Name is required."**

### 2. Select images

A dropdown that controls which subscriptions trigger this webhook.

- The first option is **All subscribed images** — selecting it makes the
  webhook fire for every subscription in the organization (current and
  future).
- The rest of the dropdown lists the organization's subscriptions, one
  per row, each with a checkbox.
- Selecting an individual image while *All subscribed images* is active
  switches the selection to just that image. Selecting *All subscribed
  images* while individual images are selected clears them.
- The dropdown trigger renders selected images as image badges; if
  nothing is selected or *all* is selected, it shows the placeholder
  **All subscribed images**.
- Validation: at least one selection is required.

> ![PLACEHOLDER: "Select images" dropdown opened, showing "All subscribed images" checkbox and a few subscription rows](./images/webhooks/select-images.png)

### 3. Endpoint URL

The HTTPS URL Quor will POST events to.

- Placeholder: *e.g., https://webhook.example.com*
- Validation:
  - Required — **"Endpoint URL is required."**
  - Must match an HTTPS URL pattern — **"Enter a valid HTTPS URL."**
- Below the input there is a green **TLS 1.2+ Required** badge with a
  lock icon and a short note: *"HTTP endpoints are not supported."*

> ![PLACEHOLDER: Endpoint URL input with the green "TLS 1.2+ Required" badge underneath](./images/webhooks/endpoint-url.png)

### 4. Event types

A list of checkboxes describing which events should trigger the
webhook. Today the available events are:

| Event | Status |
|---|---|
| Image updated | Available |
| New vulnerabilities detected | Coming soon |
| New version/tag available | Coming soon |
| Version/tag EOL | Coming soon |

Events marked **Coming soon** are rendered disabled and cannot be
selected. By default, new webhooks are pre-checked with **Image updated**.

Validation: at least one event type must be selected — otherwise the
field shows **"Choose an event type."**

> ![PLACEHOLDER: Event types list with "Image updated" checked and the three "Coming soon" rows disabled with yellow badges](./images/webhooks/event-types.png)

### Delivery info alert

Below the form fields the form renders a neutral info alert with the
heading **How deliveries work**:

> *Your server must respond with a 2xx status within 10 seconds. Failed
> deliveries are not retried.*

If the API returns an error from either the test or the submit action,
this alert is replaced with a red **Error** alert containing the message
returned by the backend.

> ![PLACEHOLDER: Gray "How deliveries work" alert in its default state](./images/webhooks/info-alert.png)

> ![PLACEHOLDER: Red error alert variant after a failed submission](./images/webhooks/error-alert.png)

### Form actions

The action row in the footer of the drawer contains:

- **Test connection** (outline button) — sends a dry-run delivery to the
  endpoint without persisting the webhook. After the request settles,
  a badge briefly replaces the button:
  - Green **Connected!** on success.
  - Red **Connection failed!** on error (the error message also appears
    in the alert area above).
- **Create webhook** (primary) — submits the form. Disabled while a
  *Test connection* request is pending.

> ![PLACEHOLDER: Footer row showing "Test connection" outline button and the primary "Create webhook" button](./images/webhooks/form-actions.png)

> ![PLACEHOLDER: Footer row showing the green "Connected!" success state replacing the test button](./images/webhooks/test-success.png)

On success the drawer closes, a toast reading **"Webhook created
successfully!"** appears, and the list refreshes to show the new card.

---

## Webhook details drawer

Clicking any webhook card opens the **Webhook details** drawer. The
drawer shows a read-only summary of the webhook and exposes
activate/deactivate, edit, and remove actions.

> ![PLACEHOLDER: Webhook details drawer in its default state showing summary card, toggle and action buttons, and the "Recent deliveries" section](./images/webhooks/details-drawer.png)

### Summary card

The top of the drawer renders a card with:

- The webhook **name** in large semibold type.
- The **URL** in a small monospace-style chip.
- The **subscribed images** badges (same logic as the list card).
- A **Last triggered** timestamp with a clock icon. *(Currently displays
  a placeholder of "2 hours ago".)*

### Active / Disabled toggle

Below the summary, a **toggle switch** labeled **Active** controls
whether the webhook is currently receiving events.

- A success toast reads **"Webhook updated successfully."**
- When the webhook is disabled, a small note next to the toggle reads:
  *"(Automatic notifications are no longer being sent.)"*

> ![PLACEHOLDER: Toggle switch in "Active" position next to Edit and Remove buttons](./images/webhooks/toggle-active.png)

> ![PLACEHOLDER: Toggle switch in disabled position with the explanatory text shown next to it](./images/webhooks/toggle-disabled.png)

### Edit action

Clicking **Edit** swaps the summary card for the same form used in
creation, pre-filled with the webhook's current values. The form behaves
identically to the create form, with a few differences:

- The drawer title remains **Webhook details**.
- A **Cancel** outline button is added to the action row; it discards
  changes and swaps back to the summary view.
- The primary button reads **Save changes** and is disabled until at
  least one field differs from its initial value.

On success the drawer closes and the toast reads **"Webhook updated
successfully!"**.

> ![PLACEHOLDER: Details drawer with the edit form expanded inline, all fields pre-populated](./images/webhooks/edit-form.png)

### Remove action

Clicking **Remove webhook** (red outline button) triggers a confirmation
step rendered in-place by sliding the action row up and revealing a
warning row underneath:

- A red quote block: *"Are you sure? This webhook will be permanently
  banned."*
- A **Back** outline button to cancel.
- A red **Remove** button that confirms the deletion.

On success the drawer closes, the webhook list refreshes, and a toast
reads **"Webhook removed successfully."**

> ![PLACEHOLDER: Inline remove-confirmation row with the red "Are you sure?" blockquote and Back/Remove buttons](./images/webhooks/remove-confirm.png)

### Recent deliveries

At the bottom of the drawer there is a **Recent deliveries** section
showing the webhook's delivery history. When no deliveries have been
recorded yet, it displays *"No delivery detected for this webhook."*

> ![PLACEHOLDER: "Recent deliveries" section with the ghost-icon empty state](./images/webhooks/recent-deliveries-empty.png)

---

## Validation reference

| Field | Rule | Message |
|---|---|---|
| Name | Required | *Name is required.* |
| Images | At least one selection | *Images are required.* |
| Endpoint URL | Required | *Endpoint URL is required.* |
| Endpoint URL | Must be a valid HTTPS URL | *Enter a valid HTTPS URL.* |
| Events | At least one selected | *Choose an event type.* |

---

## Delivery semantics

A few important things to surface to integrators:

- **HTTPS only.** Plain HTTP endpoints are rejected client-side and not
  accepted by the backend.
- **TLS 1.2 or higher** is required at the transport layer.
- The receiving endpoint must respond with a **2xx status code** within
  **10 seconds**.
- **Failed deliveries are not retried.** Make your endpoint idempotent
  and resilient; if your service is down when an event fires, that
  delivery is lost.
- **Test connection** sends a real request to your endpoint flagged as a
  test, so make sure your handler tolerates test payloads (or short-
  circuits them) before you point Quor at a production system.

---

## Event types

Only **Image updated** is wired up today. The other three event types
are visible in the UI but disabled with a *Coming soon* badge:

- New vulnerabilities detected
- New version/tag available
- Version/tag EOL

When these become available the *Coming soon* badge will be removed and
the checkbox will become selectable.

---

## Quick reference: end-to-end flow

1. Open `/webhooks`.
2. Click **Add Webhook**.
3. Fill in **Name**, pick **Images** (or leave *All subscribed images*),
   paste an **HTTPS Endpoint URL**, and tick at least one **Event type**.
4. Optionally click **Test connection** to verify your endpoint
   answers with a 2xx in under 10 seconds.
5. Click **Create webhook**. The drawer closes and the card appears in
   the list, marked **Active**.
6. Click the card to view details, toggle it off, edit it, or remove it.

> ![PLACEHOLDER: Side-by-side composite of the three main states — list, create drawer, details drawer](./images/webhooks/flow-composite.png)
