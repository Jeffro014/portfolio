# Portfolio site

Static HTML + one stylesheet. No build step, no dependencies beyond Google Fonts.

## Preview locally
Open `index.html` in a browser.

## Add your headshot
Drop a photo at `assets/headshot.jpg` (portrait, roughly 4:5, at least 600px wide). Until it exists the page shows a navy block with your initials.

## Deploy (GitHub Pages)
1. Create a new **public** repo (e.g. `jeffrolling.github.io`) — keep this job-search repo private.
2. Copy the contents of this `portfolio/` folder into it and push.
3. Settings → Pages → Source: `main` / root. The site appears at `https://<user>.github.io/` within a minute.

Netlify Drop (drag the folder onto app.netlify.com/drop) works too.

## Before it goes public
- Every number on the site traces to the experience library in the ProductManagement repo. If a figure changes there, change it here.
- The phone number is deliberately not on the site.
- Update the "Availability" and "Open to" lines on `contact.html` if they change.
