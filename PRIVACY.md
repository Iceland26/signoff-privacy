# SignOff — Privacy Policy

**Effective date: 17 November 2026**

SignOff ("the app") is an Atlassian Forge app that turns Jira and
Confluence specifications into structured acceptance criteria and a test
plan, and exposes those criteria to external coding agents through
Atlassian MCP tools so they can report verification results back into
Jira. This policy describes what the app accesses, what it stores and
where, and the choices available to you.

## What the app accesses

When you use SignOff on a Jira issue, the app reads:

- The **summary and description of that Jira issue**, and
- The **body of a Confluence page**, but only when you explicitly
  provide that page's ID to the app.

The app acts through Atlassian's Forge platform using the permissions
declared in its manifest, either as the invoking user (issue panel and
in-product actions) or as the app itself (MCP tool calls from external
clients an admin has enabled). The app does not access any other issues,
pages, sites, or accounts.

## What the app stores, and where

SignOff stores exactly two kinds of data, and both live **on your own
Atlassian site**, attached to the Jira issue you ran it on, as Jira
issue entity properties:

- `signoff-criteria` — the acceptance criteria extracted from the spec.
- `signoff-vstate` — the verification state (status and evidence text)
  reported for each criterion.

The app also creates content you ask for on your site: test-plan issues,
issue links, verification-report comments, and gap issues for failed
criteria.

SignOff has **no servers of its own** and keeps **no copy** of your data
anywhere else. The developer never receives, sees, or stores your issue
content, criteria, or verification data. The app does not use Forge
hosted storage for this data.

## Third parties

By default, **no data leaves your Atlassian site** and nothing is sent
to the developer or to any third party. The app contains no analytics,
advertising, or tracking.

One optional exception exists:

- **Optional Gemini enrichment.** If — and only if — a site admin
  configures their own Google Gemini API key as a Forge runtime
  variable (`GEMINI_API_KEY`), the app may send the extracted criteria
  text to Google's Gemini API once, to polish criterion wording. The
  key belongs to the admin, the call goes directly from the Forge
  runtime to Google, and any failure simply leaves the deterministic
  output unchanged. The app's core features work fully without this
  enrichment. Google's handling of that request is governed by Google's
  own terms and privacy policy.

## Personal data

SignOff does not collect, sell, rent, or share personal data, and does
not use data for tracking or profiling. The only personal information
the app may incidentally process is what already appears in the spec
text you point it at (for example, a name mentioned in an issue
description); that text stays on your Atlassian site, subject to the
optional Gemini exception above if an admin has enabled it.

## Retention and removal

Criteria and verification state stored as issue entity properties are
retained for as long as the issue exists and are deleted with the
issue. You can remove the app's stored data at any time by deleting the
`signoff-criteria` and `signoff-vstate` properties from the issue via
the Jira REST API, or by uninstalling the app. Issues and comments the
app created remain ordinary Jira content under your site's own
retention controls and can be deleted like any other issue or comment.

## Changes to this policy

If this policy changes, the updated version will be published at this
same location with a new effective date.

## Contact

Questions about this policy or the app: please open an issue on the
project's GitHub repository —
https://github.com/Iceland26/signoff-privacy/issues
