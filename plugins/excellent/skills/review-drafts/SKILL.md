---
name: review-drafts
description: Gather what is waiting for a person's decision in Excellent — social posts and guest campaigns to approve, thank-you cards and pre-shift notes to publish, replies to inquiries to send, draft invoices, shifts and documents to keep or discard — and give a review link for each, to decide in Excellent. Use for "what's waiting for my approval", "send me the review links", "approve this week's posts", "which drafts are still open".
---

# Review drafts

Read-only. This skill never approves, publishes, sends or discards anything. Each decision is made by the
person on Excellent's own review page, signed in as themselves; the link works only for them.

## 1. Find the drafts

- Social posts and guest campaigns: `marketing` lists both queues with each draft's status.
- Documents: `list_documents` (drafts carry a draft status). Invoices: `list_invoices` with `status: "draft"`.
- Staff shifts: `schedule_week` shows each venue's unpublished changes.
- A draft made earlier in this conversation: use the id its tool returned.

## 2. Get a link for each

Call `get_review_link` with the draft's `kind` (`post`, `campaign`, `card`, `reply`, `invoice`, `preshift`,
`shift` or `document`) and its `id`. The answer gives the link and until when it works when the person may
decide that draft; otherwise it says who can.

## 3. Hand off

One line per draft: what it is, what the person will be asked (approve or reject, publish or discard, send,
keep or discard) and the link. End with: "Nothing is approved, published or sent until you decide it on
Excellent's page."
