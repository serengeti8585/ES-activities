# Wetland Rescue 1.0

Wetland Rescue is a 3–5 minute Environmental Science exit ticket. Students answer three questions about wetland hydrology, floodwater storage, and nutrient pollution. Correct answers restore parts of an illustrated Florida freshwater wetland. The recap shows any remaining restoration steps, and the results report the student's score and provide answer review.

## Run or assign

- Download `index.html` and open it in Chrome or Microsoft Edge. The illustration, styles, and activity logic are embedded in the file. No installation, internet connection, or account is required. A school browser policy can block local HTML files. In that case, use the hosted link.
- For Google Classroom, deploy the activity using the steps below and attach the resulting HTTPS URL as a link. Students can complete the activity on their own devices. Scores stay on the results screen during that attempt. The activity does not store student data or send results to Classroom.

## Edit the questions

Open `index.html` in a text editor and search for `TEACHER_CONFIGURATION`. Edit the title and introduction there. In the question bank, enter each question's exact wording, four choices, correct answer index (A = 0, B = 1, C = 2, D = 3), explanation, and concept for the results screen. Add or remove question entries to change the length. Keep at least one question. The optional `restoration` field can connect a question to one of the three existing wetland changes. If omitted, a correct answer triggers the next available change.

The included questions are provisional and have yet to be verified against the Ducks Unlimited assessment bank. Dashboard values are fictional game scores. The animation compresses ecological recovery into a few seconds for the activity.

## Upload to GitHub and deploy on Cloudflare Pages

1. Create a GitHub repository. In the repository, choose **Add file → Upload files**, upload `index.html` and this README at the repository root, and commit to the default branch.
2. In the Cloudflare dashboard, go to **Workers & Pages → Create application → Pages → Connect to Git**. Authorize GitHub and select the repository.
3. Select the default branch as the production branch. Choose **None** for the framework preset. Use `exit 0` as the build command and `.` as the build output directory. Leave the root directory at its default.
4. Deploy. Open the resulting `pages.dev` URL and complete an attempt before sharing the link in Google Classroom.

## Testing

Automated Playwright checks passed in Chromium with networking disabled. They covered the initial SVG with JavaScript disabled, each answer choice, correct and incorrect feedback, scoring, locked submissions, restoration timing and skipping, the all-missed path, review, and reset. The tests also checked 1024 × 600 and 768 × 600 layouts, touch input at 360 × 640, keyboard navigation, reduced motion, and a temporary five-question configuration. No external requests or browser console errors were observed.

The managed test browser blocked direct `file://` navigation, so the tests loaded the same HTML directly into an offline Chromium page. Microsoft Edge and a physical school-managed Chromebook were unavailable for testing. The files are ready for deployment through Cloudflare Pages.
