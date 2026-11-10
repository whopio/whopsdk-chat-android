# Changelog

## [0.1.1] - 2026-11-10

- `DMChannel.otherUser` and `DMChannel.members`, as `WhopUserSummary` values with each person's username, name and avatar.
- Apps built against 0.1.0 must be rebuilt: the new fields change `DMChannel`'s compiled constructor and `copy()`, so 0.1.0 code that creates or copies a `DMChannel` fails at runtime with 0.1.1. Code that only reads it is unaffected.

## [0.1.0] - 2026-11-09

- First release, for WhopX Android.
- `WhopSDK.configure` with a `WhopTokenProvider`, and `WhopSDK.signOut`.
- `WhopChatView`, `WhopChatThreadView`, `WhopDMsListView` and `WhopSearchView`, with `ChatEvent`, `DMsListEvent` and `SearchEvent`.
- Context menus through `WhopContextMenu`, and theming through `WhopChatTheme` and `WhopChatTint`.
