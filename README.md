# Bug report for video resource loading in Google Chrome

This repository documents an apparent regression in Chrome 52 ([released on
2016-07-20](https://chromereleases.googleblog.com/2016/07/stable-channel-update.html)).

Steps to reproduce:

1. Open Chrome's developer tools
2. Open the "Network" tab
3. Activate the "Disable cache" checkbox
4. Navigate to https://bocoup.github.io/chrome-bug-video-resource/src/index.html
5. Note Network log's entries describing a video resource. Note also the state
   of the document, describing 1 "resource" performance entry.
6. Refresh the page
7. Note absence of entries describing any video resources. Note also the state
   of the document, describing 0 "resource" performance entries.

Expected: the video resource should be requested with every navigation and a
corresponding performance entry should be reported.

Actual: the video resource is requested on the initial navigation but not on
any subsequent navigation (and no performance performance entries are
reported).

This behavior may be the cause of [previously-reported inconsistent behavior in
certain
web-platform-tests](https://github.com/web-platform-tests/wpt/issues/14433).

## License

Copyright 2018 Bocoup under [the GNU General Public License
v3.0](https://www.gnu.org/licenses/gpl-3.0.html)
