# Rio math practice (static page)

A static copy of the Rio Math Practice page, served from GitHub Pages instead of script.google.com.
Google blocks under-13 accounts that are signed in on script.google.com. This page is hosted somewhere else and
talks to the Apps Script backend with `fetch(..., { credentials: 'omit' })`, so no Google cookies are sent and
Google can't tell which account (if any) is signed in on the device.

* `index.html` is generated. Don't edit it by hand. Edit `Index.html` in the main project, then run `node dev/build-pages.js`.
* `API_URL.txt` holds the Apps Script `/exec` URL that the page calls (public, no secrets).
* Links: `https://<user>.github.io/rio-math/?date=YYYY-MM-DD`. With no date it shows today's test (Tokyo time).

Answer keys are never in this repo or on the page. The backend only serves questions.

Rio's inbox (top strip: messages from Dad, tokens, certificates, scores) reads `<exec>?format=json&api=rio` and marks messages read with a
text/plain POST `{"action":"markRead","ids":[...]}`, also with no cookies. If the backend doesn't have that API yet, the strip stays hidden.
