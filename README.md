# Switch Tabs

A [Raycast](https://raycast.com) extension for Windows that gives you instant keyboard-driven control over every open tab across all your Chromium browsers — switch, search, group, pin, close, control media, manage bookmarks, browse history, track downloads, and more.

> **Requires the companion server + browser extension.**
> Download and set up from the companion repo first: [switch-tabs-companion](https://github.com/your-username/switch-tabs-companion)

---

## How It Works

```
Raycast Extension  ←──WebSocket──→  Bridge Server (.exe)  ←──Native Messaging──→  Browser Extension
```

This Raycast extension is the UI layer. It talks to a local bridge server (`.exe`) which relays commands to and from the browser extension. Both the server and browser extension live in the [companion repo](https://github.com/your-username/switch-tabs-companion).

---

## Setup

### 1. Get the companion repo

Go to [switch-tabs-companion](https://github.com/your-username/switch-tabs-companion) and follow the full setup guide there. You need the server and browser extension set up before this Raycast extension will work.

### 2. Configure extension preferences

Open Raycast → search **Switch Tabs** → press `Cmd + ,` to open Extension Preferences.

| Preference | What to do |
|------------|------------|
| **Server Directory Path** | Point this to the `server` folder you downloaded from the companion repo (e.g. `C:\Tools\switch-tabs-server`) |
| **Browser Extension ID** | If you installed from the **Edge Add-ons Store**, leave the default as-is. If you loaded the extension **unpacked** (manually via `chrome://extensions`), paste your extension's ID here |

### 3. Register the bridge and start the server

Open Raycast → type **Manage Server** → press Enter. Run these in order:

1. **Register Browser Bridge (Native Host)** — one-time only. A PowerShell window opens, registers the server with your browser, and closes automatically.
2. **Watch Bridge Logs** — opens a terminal with real-time WebSocket logs to confirm the connection is live.
3. **Import Edge Workspaces** — only needed if you use Edge Workspaces.

After registration, open **Switch Tabs**. Your tabs should appear within a second or two.

---

## Commands

| Command | Description |
|---------|-------------|
| **Switch Tabs** | Main command — search, filter, and act on all open tabs |
| **Manage Server** | Run setup scripts, watch live logs, import workspaces |

---

## Features

### Tab Switching & Management
- Jump to any open tab across all connected browsers and windows
- Open tabs in the background without leaving Raycast
- Close individual tabs or entire windows
- Pin / unpin tabs
- Rename tabs with a custom local title (persists across SPA navigations on the same domain, resets on domain change)
- Duplicate tabs
- Refresh tabs
- Discard (freeze/suspend) tabs to free memory
- Detach / attach tabs between windows
- Move tabs to a different window or a new window
- Preview a tab's content inline

### Tab Groups
- View all tab groups with color labels
- Create new groups from any tab (with name and color)
- Move tabs into existing groups
- Ungroup tabs
- Edit group name and color
- Collapsed view: browse all groups as folders, expand any group to see its tabs

### Web Search (Search Mode)
- Toggle between **Filter Tabs** and **Web Search** mode with `/`
- Live Google search suggestions with optional rich entity images
- Open results in a new tab, current tab, background tab, or a popup window
- "I'm Feeling Lucky" (Google or DuckDuckGo)
- Set a search result as the current search query without opening it
- Surgical search targeting: scan the active tab for input fields and inject a query directly

### Bookmarks
- Browse the full bookmark tree
- Open bookmarks in a new or current tab
- Create a bookmark from any open tab into a chosen folder
- Move, rename, and delete bookmarks

### History
- Browse recent browser history
- Open entries in a new or current tab
- Delete individual items or all history

### Downloads
- View all downloads with live progress bars for active downloads
- Pause, resume, and cancel in-progress downloads
- Erase download history entries
- Open completed files

### Sessions (Recently Closed)
- Browse recently closed tabs and windows
- Restore any closed session

### Workspaces (Edge)
- Browse Edge workspace tab groups
- Import workspace configurations from Edge sync exports
- Workspace names sync via native messaging even when the WebSocket is offline

### Media Controls
- Play / pause media in any tab
- Seek forward and backward (configurable seconds, default 5s)
- Seek debounce: rapid presses accumulate into one combined seek
- Increase / decrease playback speed
- Real-time status badge showing current time, duration, and speed

### Multi-Browser
- Connects to multiple browsers simultaneously
- Cycle through connected browsers with a hotkey
- Per-browser window filter with smart window naming (uses active tab title or domain)
- Browser icons for Edge, Chrome, Brave, Helium

### Window Management
- Filter tabs by window
- Cycle through windows with a hotkey
- Close windows
- Minimize / restore windows
- Toggle fullscreen
- Toggle Focus Mode (detach tab into a popup window, or re-attach a popup)

---

## All Keyboard Shortcuts

These are the hardcoded shortcuts that are always active. Configurable shortcuts (set in Extension Preferences) are listed separately below.

### Tab Actions

| Shortcut | Action |
|----------|--------|
| `Enter` | Switch to Tab *(configurable)* |
| `Space` | Switch to Tab in Background (Filter Mode) |
| `Ctrl + Shift + Enter` | Switch to Tab in Background (Search Mode) |
| `Ctrl + →` | Preview Tab (inline detail view) |
| `Shift + Enter` | Move Tab to Window (opens submenu) |
| `Ctrl + W` / configurable | Close Tab |
| `Ctrl + X` | Close Window *(configurable, default Ctrl+X)* |
| `Ctrl + M` | Minimize / Restore Window |
| `Ctrl + .` | Pin / Unpin Tab |
| `Ctrl + R` | Refresh Tab |
| `Ctrl + D` | Discard Tab (Freeze) |
| `Ctrl + E` | Rename Tab |
| `Ctrl + L` | Duplicate Tab |
| `Ctrl + O` | Toggle Focus Mode (popup / re-attach) |
| `Ctrl + F` | Toggle Fullscreen |
| `Shift + C` | Copy Tab URL |

### Tab Groups

| Shortcut | Action |
|----------|--------|
| `Ctrl + G` | Create New Group |
| `Shift + Z` | Move to Group (opens submenu) |
| `Shift + A` | Toggle Collapsed / Expanded view |
| `Ctrl + E` | Edit Group (name + color) — on a folder item |

### Media Controls

*(Only visible when the tab has active media)*

| Shortcut | Action |
|----------|--------|
| `Ctrl + ←` | Play / Pause Media |
| `→` | Seek Forward (default 5s) |
| `←` | Seek Backward (default 5s) |
| `Shift + .` | Increase Playback Speed |
| `Shift + ,` | Decrease Playback Speed |
| `Shift + →` | Search in Tab *(when media is present)* |
| `Shift + ←` | Input Search in Active Tab *(when media is present)* |

### Tab Management (no media)

| Shortcut | Action |
|----------|--------|
| `→` | Search in Tab *(when no media)* |
| `←` | Input Search in Active Tab *(when no media)* |

### Search Mode (Web Search)

| Shortcut | Action |
|----------|--------|
| `Enter` | Open in New Tab *(configurable)* |
| `Ctrl + Enter` | Open in Current Tab *(configurable)* |
| `Shift + Enter` | Open in Background |
| `Ctrl + O` | Open in Focus Popup |
| `Shift + S` | Set as Search Query (without opening) |
| `Shift + C` | Copy URL |

### Navigation & Mode Switching

| Shortcut | Action |
|----------|--------|
| `` ` `` | Cycle Browser Filter *(configurable)* |
| `Tab` | Cycle Window Filter *(configurable)* |
| `/` | Toggle Filter ↔ Search Mode *(configurable)* |
| `'` | Clear Search / Filter Text *(configurable)* |
| `Ctrl + Space` | Open History View *(configurable)* |
| `Shift + Space` | Open Bookmarks View *(configurable)* |
| `Ctrl + Backspace` | Open Workspaces View *(configurable)* |
| `Shift + Tab` | Open Downloads View *(configurable)* |
| `Alt + X` | Open Sessions View *(configurable)* |

---

## Configurable Shortcuts

Every shortcut marked *(configurable)* above can be changed in Extension Preferences. Each has a **Modifier** dropdown (None / Windows / Control / Alt / Shift) and a **Key** text field.

| Preference Name | Default | Description |
|-----------------|---------|-------------|
| Switch Tab Modifier + Key | None + *(Enter)* | Switch to a tab |
| Close Tab Modifier + Key | None + *(none)* | Close a tab |
| Close Window Modifier + Key | Ctrl + X | Close a browser window |
| Cycle Browser Modifier + Key | None + `` ` `` | Cycle through connected browsers |
| Cycle Window Modifier + Key | None + Tab | Cycle through windows of current browser |
| History View Modifier + Key | Ctrl + Space | Open the History panel |
| Bookmarks View Modifier + Key | Shift + Space | Open the Bookmarks panel |
| Workspaces View Modifier + Key | Ctrl + Backspace | Open the Workspaces panel |
| Downloads View Modifier + Key | Shift + Tab | Open the Downloads panel |
| Sessions View Modifier + Key | Alt + X | Open the Sessions panel |
| Search Toggle Modifier + Key | None + `/` | Toggle Filter ↔ Search mode |
| Clear Search Modifier + Key | None + `'` | Clear the search/filter bar |
| Search: New Tab Modifier + Key | None + Enter | Open search result in new tab |
| Search: Current Tab Modifier + Key | None + *(Ctrl+Enter)* | Open search result in current tab |

---

## All Preferences

### Search

| Preference | Default | Description |
|------------|---------|-------------|
| Open in Background | Off | Opening a result keeps Raycast open and doesn't focus the browser |
| Clear Search on Enter | Off | Pressing Enter on a web search result clears the search bar |
| Clear Search on Background | Off | Opening a background search clears the search bar |
| Clear Search on Current Tab | Off | Opening a result in the current tab clears the search bar |
| Lucky Search Provider | Google | Search engine for "I'm Feeling Lucky" (Google or DuckDuckGo) |
| Show Entity Images | Off | Rich thumbnails in search suggestions — may slow suggestions |
| Search Mode: Clear via '/' | Off | Typing `/` in Search Mode when there is text clears it first |
| Filter Mode: Clear via '/' | Off | Typing `/` in Filter Mode when there is text clears it first |

### Window Filter

| Preference | Default | Description |
|------------|---------|-------------|
| Show Window Filter | On | Dropdown to filter tabs by browser window |
| Enable Smart Window Naming | On | Windows named by active tab title/domain instead of "Window 1, 2…" |
| Include 'All Windows' View | Off | Adds an "All Windows" option to the window filter dropdown |
| Group Tabs by Domain | Off | Groups tabs by domain in the expanded view |

### Tab Icons & Colors

| Preference | Default | Description |
|------------|---------|-------------|
| Icon: Sleeping Tab | `Icon.Waveform` | Raycast icon name for sleeping/frozen tabs |
| Icon: Discarded Tab | `Icon.LivestreamDisabled` | Raycast icon name for discarded tabs |
| Icon: Pinned Tab | `Icon.Pin` | Raycast icon name for pinned tabs |
| Color: Sleeping Tab | `SecondaryText` | Hex code (e.g. `#FF9F0A`) or Raycast color name |
| Color: Discarded Tab | `SecondaryText` | Hex code or Raycast color name |
| Color: Pinned Tab | `Blue` | Hex code or Raycast color name |

### Media

| Preference | Default | Description |
|------------|---------|-------------|
| Media Seek Amount | `5` | Seconds to seek forward/backward |
| Enable Media Seek Debounce | On | Accumulates rapid seeks into one combined action |
| Seek Debounce Delay (ms) | `500` | Wait time after last seek press before executing |

---

## Project Structure

```
raycast-extension/
├── src/
│   ├── tabSwitch.tsx              # "Switch Tabs" command — main UI entry point
│   ├── manageServer.tsx           # "Manage Server" command
│   ├── constants.ts               # WebSocket message types, browser icon map
│   ├── types.ts                   # Shared TypeScript interfaces
│   ├── utils.ts                   # Cache, shortcut resolver, icon/color helpers
│   ├── components/
│   │   ├── TabItem.tsx                # Individual tab list item + full action panel
│   │   ├── NormalTabsSections.tsx     # Expanded tab list (grouped by window/domain)
│   │   ├── CollapsedTabsSection.tsx   # Collapsed view (groups as folders)
│   │   ├── SearchResultsSection.tsx   # Web search results list
│   │   ├── SearchBarFilter.tsx        # Browser/window dropdown accessory
│   │   ├── SearchModeAction.tsx       # Toggle Filter ↔ Search mode action
│   │   ├── CycleBrowserAction.tsx     # Cycle browser filter action
│   │   ├── CycleWindowAction.tsx      # Cycle window filter action
│   │   ├── ToggleCollapseAction.tsx   # Toggle collapsed/expanded view action
│   │   ├── TabPreview.tsx             # Inline tab detail/preview view
│   │   ├── TabSearchView.tsx          # Navigate tab to a URL
│   │   ├── TargetInputSearchView.tsx  # Surgical input field search targeting
│   │   ├── RenameTabForm.tsx          # Rename tab form
│   │   ├── CreateGroupForm.tsx        # Create tab group form
│   │   ├── EditGroupForm.tsx          # Edit group name/color form
│   │   ├── GroupDetailView.tsx        # Expanded group detail view
│   │   ├── BookmarksAction.tsx        # Bookmarks panel trigger
│   │   ├── BookmarksView.tsx          # Bookmarks browser view
│   │   ├── BookmarkFolderPicker.tsx   # Folder picker for saving bookmarks
│   │   ├── RenameBookmarkForm.tsx     # Rename bookmark form
│   │   ├── BrowserHistoryView.tsx     # History browser view
│   │   ├── HistoryAction.tsx          # History panel trigger
│   │   ├── DownloadsAction.tsx        # Downloads panel trigger
│   │   ├── DownloadsView.tsx          # Downloads browser view
│   │   ├── RecentTabsAction.tsx       # Recent tabs panel trigger
│   │   ├── RecentTabsView.tsx         # Recently closed tabs view
│   │   ├── WorkspacesAction.tsx       # Workspaces panel trigger
│   │   ├── WorkspacesView.tsx         # Workspaces browser view
│   │   ├── StatusViewList.tsx         # Connection error / onboarding views
│   │   └── index.ts                   # Component barrel exports
│   ├── context/
│   │   └── BrowserStore.tsx       # Global browser state, metadata sync, socket ref
│   ├── hooks/
│   │   ├── useBrowser.ts          # Core data hook — tabs, groups, bookmarks, sessions
│   │   ├── useTabActions.ts       # All tab action dispatchers (activate, close, group…)
│   │   ├── useFilterState.ts      # Persistent browser/window filter state
│   │   └── useLocalSearch.ts      # Client-side tab search (O(1) pre-computed index)
│   └── utils/
│       ├── useSearch.ts           # Web search suggestions hook (Google API)
│       └── types.ts               # Search-specific types (SearchResult)
├── assets/
│   ├── command-icon.png
│   ├── all.png / edge.png / chrome.png / brave.png
│   ├── vivaldi.png / arc.png / opera.png / helium.png
│   ├── zen.png / firefox.png
│   └── ext.png / ext2.png
├── package.json
├── raycast-env.d.ts
└── README.md
```

---

## Development

```powershell
npm install       # install dependencies
npm run dev       # start Raycast dev mode (ray develop)
npm run build     # production build
npm run lint      # lint check
npm run fix-lint  # auto-fix lint issues
```

---

## License

MIT
