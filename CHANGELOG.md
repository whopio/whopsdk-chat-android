# Changelog

## [0.1.4] - 2026-11-22

- Tapping an image or video in chat no longer rotates the screen. The media viewer now keeps the host app's orientation and respects the user's auto-rotate setting. Before this, it asked Android to follow the sensor whatever that setting was. On a phone held off upright with auto-rotate locked, the screen turned to landscape and back. In a host whose activity is recreated on rotation, as WhopX's is, the viewer closed before it appeared.
- The media viewer stays open when the host's activity is recreated, for example when the user rotates the phone with auto-rotate on. Before this, the rotation closed it.
- The video full screen button is hidden in the media viewer, since full screen worked by forcing a rotation. When auto-rotate is on and the host app allows landscape, turning the phone still shows a video full screen. In a host whose activity is recreated on rotation, the video starts again from the beginning.

## [0.1.3] - 2026-11-18

- Channels in `WhopDMsListView` (`showsChannels = true`) show as unread when their latest post from someone else is newer than the user's last view, as the iOS SDK does. Before this, the list used only the server's unread flag and notification badges, which the SDK never loads, so channels rarely showed as unread.
- `WhopChatView` marks a channel read while the user is at the bottom of it, and again as new posts arrive. Before this, only opening a channel from `WhopDMsListView` marked it read.

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
