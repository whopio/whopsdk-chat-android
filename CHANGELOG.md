# Changelog

## [0.1.2] - 2026-11-12

- Live chat: the SDK now opens its realtime connection while a user is signed in and one of its views is on screen, as the iOS SDK does, so typing indicators, new messages, reactions, read receipts and DM online status update without a refresh. Before this, the SDK never connected, so none of these arrived and the user's own typing was never sent.
- The connection closes a second after the last SDK view leaves the screen, 15 seconds after the app goes to the background, and on `WhopSDK.signOut`. It reopens when a view returns. After a drop it retries after about three seconds, doubling up to a minute between attempts, with each wait randomized. Hosts don't need to call anything.

## [0.1.1] - 2026-11-10

- `DMChannel.otherUser` and `DMChannel.members`, as `WhopUserSummary` values with each person's username, name and avatar.
- Apps built against 0.1.0 must be rebuilt: the new fields change `DMChannel`'s compiled constructor and `copy()`, so 0.1.0 code that creates or copies a `DMChannel` fails at runtime with 0.1.1. Code that only reads it is unaffected.

## [0.1.0] - 2026-11-09

- First release, for WhopX Android.
- `WhopSDK.configure` with a `WhopTokenProvider`, and `WhopSDK.signOut`.
- `WhopChatView`, `WhopChatThreadView`, `WhopDMsListView` and `WhopSearchView`, with `ChatEvent`, `DMsListEvent` and `SearchEvent`.
- Context menus through `WhopContextMenu`, and theming through `WhopChatTheme` and `WhopChatTint`.
