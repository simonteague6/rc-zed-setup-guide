# Single page with OS-tabbed sections, not separate OS-specific pages

The Setup Guide uses one page with OS-specific sections (macOS, Windows) for pre-Zed steps and a single shared section for everything inside Zed, rather than separate pages per operating system. The pre-Zed steps differ enough to warrant separation; the in-Zed content is identical and duplicating it across pages would create a maintenance burden. A landing page that forces an OS choice was rejected as adding a click without value — both OS sections are visible on the same page, clearly labeled, letting readers scroll past the irrelevant one.

**Considered Options**: Two separate pages per OS (rejected: duplicated content, double maintenance). Landing page with OS fork (rejected: unnecessary click, no added value).

**Consequences**: In-Zed content has one source of truth. When Zed's UI updates, one edit fixes both OS paths. The trade-off is that Windows users scroll past macOS content they don't need — acceptable for a guide this short.
