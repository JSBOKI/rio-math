# Rio math practice (static page)

A static copy of the Rio Math Practice page, served from GitHub Pages instead of script.google.com.
Google blocks under-13 accounts that are signed in on script.google.com. This page is hosted somewhere else and
talks to the Apps Script backend with `fetch(..., { credentials: 'omit' })`, so no Google cookies are sent and
Google can't tell which account (if any) is signed in on the device.

* `index.html` is generated. Don't edit it by hand. Edit `Index.html` in the main project, then run `node dev/build-pages.js`.
* `API_URL.txt` holds the Apps Script `/exec` URL that the page calls (public, no secrets).
* Links: `https://<user>.github.io/rio-math/` opens Rio's home screen (today's test, calendar, scores, skills, certificates). `?date=YYYY-MM-DD` opens that day's test. Today's test is Tokyo time, or the newest test that isn't in the future.
* `?bonus=YYYY-MM-DD` opens that day's bonus round (make-up questions after grading, each +½ point). It loads `<exec>?format=json&bonus=DATE` (questions + each item's status only) and sends answers as a text/plain POST `{"action":"bonus",...}`, with no cookies.
* Every problem has Scratch paper: a drawing pad saved on the phone (`localStorage`, by date and problem). Attach to my answer sends that drawing with the submission, using the same photo path as camera photos (up to 8 pictures).

Answer keys are never in this repo or on the page. The backend only serves questions. The home screen's skill percentages are his own scores; Dad's per-question notes and coaching summaries are not on this page.

Rio's inbox (top strip: messages from Dad, tokens, certificates, scores) and the home screen read `<exec>?format=json&api=rio` and mark messages read with a
text/plain POST `{"action":"markRead","ids":[...]}`, also with no cookies. If the backend doesn't have that API yet, the strip stays hidden and the home screen still opens today's test, with a simpler calendar until the server is updated.
