# Letterboxd-filter-by-lists
 Adds a Letterboxd film filter using lists you choose, with show/hide filters
# Letterboxd Challenge List Filters

A Tampermonkey userscript that lets you filter Letterboxd film listings using one or more lists. Show only films included in your saved lists, or hide those films to focus on everything else.

## Features

- **Show challenge films:** Display only films found in your saved lists.
- **Hide challenge films:** Hide films found in your saved lists.
- **Combine multiple lists:** Add multiple Letterboxd lists and treat their films as one combined collection.
- **Cached list data:** Reuse recently loaded list data to reduce unnecessary requests.
- **Refresh on demand:** Manually refresh cached challenge list data when lists change.
- **Easy list management:** Add or remove individual list URLs through the Tampermonkey menu.
- **Native-style controls:** Add challenge filtering options alongside Letterboxd's existing film-list filters.

## Requirements

- A desktop browser that supports Tampermonkey
- The Tampermonkey browser extension.
- A Letterboxd account.
- Access to the Letterboxd lists you want to use.

The script is designed for Letterboxd film listings, not individual film pages. List access depends on Letterboxd's permissions and your account.

### 1. Add your challenge lists

1. Open Letterboxd.
2. Open the Tampermonkey menu in your browser.
3. Select **Manage challenge list URLs…**.
4. Paste a Letterboxd list URL into the input field.
5. Select **Add URL**.
6. Repeat for any additional lists.

For example:

`https://letterboxd.com/username/list/movie-challenge/`

Use actual Letterboxd list URLs. The script normalizes list URLs by removing detail-page paths, pagination paths, query parameters, and fragments.

Duplicate URLs are not added twice.

### 2. Show challenge films

On a supported Letterboxd listing, find the film-filter menu and select **Show challenge films**.

The listing will display only films found in at least one of your saved challenge lists.

### 3. Hide challenge films

Select **Hide challenge films** to hide films found in your saved lists while keeping other films visible.

### 4. Turn off the filter

Select the currently active challenge filter again, or use the Tampermonkey menu command **Clear challenge filter**.

The script restores the listing and progress information to its unfiltered state.

## Managing your lists

Open the Tampermonkey menu:

| Manage challenge list URLs… | Add or remove saved lists |
| Refresh challenge list data | Discard cached data and fetch the saved lists again |
| Clear challenge filter | Disable the active challenge filter |

Films from all saved lists are combined. A film appearing in multiple lists is counted only once for filtering purposes.

## Cache and performance

List data is cached for approximately 15 minutes. During that period, the script can reuse cached film data rather than fetching every list again.

Use **Refresh challenge list data** when you want to retrieve updated contents immediately.

The script supports up to 200 pages per list as a safety limit. Lists exceeding that limit will produce an error instead of returning a potentially incomplete result.

Large lists can take longer to load because the script retrieves their pages sequentially.

## Watch progress

When a list filter is active, the script updates the visible progress panel to reflect the filtered films:

- Number of watched films in the filtered set.
- Number of films currently visible.
- Percentage watched.
- Original unfiltered list total, when it differs from the filtered total.

Watched status is inferred from Letterboxd's page markup, including watched attributes, account ratings, and watch-button labels. If Letterboxd changes that markup, the progress calculation may need an update.

### Changes to a list do not appear

The script caches list data for approximately 15 minutes. Use the refresh command to clear that cache and fetch the latest contents.

### The filter options are missing

Make sure you are viewing a supported film listing rather than an individual film page. The script relies on Letterboxd's listing and filter-menu structure, which may change over time.

## Privacy

The script stores saved list URLs, cached film slugs, and the selected filter mode using Tampermonkey's local userscript storage.

It fetches list pages from Letterboxd using your browser session. It does not require a separate API key or send your saved lists to a third-party server.

## Compatibility and limitations

- Designed for Letterboxd's current website structure.
- Requires access to the saved lists.
- Filtering applies to the film cards present in the supported listing; it does not modify your Letterboxd account or change the lists themselves.
- Results depend on the film identifiers and page markup provided by Letterboxd.
- Website updates may temporarily break filtering or progress calculations.
- Does not support pagination.

## Version

Current version: **2.0.0**
