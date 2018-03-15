# `prs`: Easily create links to student pull requests for grading

GitHub provides nice online code-review tools for pull requests.  For
me to visit each of these pull requests and leave feedback, it helps
to have those links all in one place. [prs.html](prs.html) helps me do
that by making it trivial to generate a page of links to the pull
requests for a particular assignment.

**Warning: I've only tested this on Firefox and Chrome. I make no promises about other browsers.**

## Getting ready
* Download [prs.html](prs.html) and save in a convenient directory.
* Download [jQuery](http://jquery.com/download/) and save it in the same directory. I recommend the compressed, production build. The version is unlikely to make a difference (I've been using 3.2.1).
* Open prs.html in an editor and configure it by making four changes:
  * In line 8 (`<script src="jquery-3.2.1.min.js"></script>`), change the `jquery-3.2.1.min.js` to match the version you downloaded in the previous step.
  * In line 10 (`var organization = "";`), fill in the string with the name of your GitHub organization (eg, `cs123-Fall-2018`).
  * In line 11 (`var assignment = "";`), fill in the string with the template for your assignment names (eg, `hw` if your assignments are named `hwN`).
  * At the end of the file, find `<div id="users">`. Between that `div` and the closing `</div>`, fill in the GitHub usernames of your students, one per line. (You can either have your students give you their GitHub usernames at the beginning of the course, or you can find the usernames when the students <i>accept</i> the first assignment in GitHub Classroom.)

## Grading an assignment

* Open prs.html in your browser, type the name of the assignment you are grading, and type Enter. This will create a list of links to individual pull requests, in groups of 6.  You can click on an individual link to open a single pull request in a new tab, or you can click on the Open Group button to the left of each group to open all 6 pull requests in separate tabs.  (The Open Group behavior is supported in Firefox, but NOT in Chrome.)
* Each pull request opens, not to the main page of that pull request, but rather to the `Files changed` view.
  * This view shows the diffs from the starter code, which is almost always what you actually want to focus on.
  * When you want to make a comment on a particular line, move your mouse to the start of a line and click on the blue `+` that will appear. This opens a text box where you can leave a comment. The textbox supports Markdown so it is easy to include code snippets in your comment.  Click on `Start a review` (for the first comment) or `Add review comment` (for later comments) to save that comment.
  * If you find yourself writing similar comments repeatedly, consider using GitHub's [saved replies](https://help.github.com/articles/using-saved-replies/) to save yourself some typing. I've also had good experience using the [Clippings](https://addons.mozilla.org/en-US/firefox/addon/clippings/) add-on for Firefox for similar purposes.
  * When you are almost done, click on the `Review changes` button (above and to the right of the diffs). This is a good place to leave grades and high-level feedback. Leave the radio button set to `Comment` and click on `Submit review` to publish your comments to the student.
  * Note that you do not need give all of your feedback in one sitting.  GitHub saves your partial review, so you can come back to it later&mdash;even on a different computer or browser&mdash;and pick up where you left off.
  * When your browser starts to get too cluttered with tabs, there's a handy browser feature that you may or may not know about.  If you right-click on the PRs tab and choose `Close Tabs to the Right` (exact wording dependent on browser), it will close all the tabs after PRs.  Between this and `Open Groups`, it can save you lots of individual clicks.
  
## Gotchas

* Make sure you've given the students detailed directions about how you want them to create the pull request. Unless they are experienced git users, they won't figure it out by themselves.
  * I create an `original` branch in the starter code, and then have them create a pull request against the `original` branch in ther own repo. If you forget to create this branch, expect much pain and suffering as you scramble to give them last-minute alternative instructions.
  * Despite all your efforts, some students will forget to create a pull request. The visible symptom will be the tab opening to a 404 &ldquo;This is not the web page you are looking for&rdquo; error.  If you go up to the address bar and delete the `pull/1/files` at the end of the URL, you can see whether the repo exists. If it does, then most likely it will say `Pull requests 0` near the top of the page. It's worth checking the commit message showing for the files in the top-level directory of the repo to see whether the student actually commited anything new. If they did, and just forgot to create the pull request, it's easy enough to create it yourself. Then you can decide what penalties (if any) you want to impose for not following directions.
* Explicitly warn students NOT to click on the 'Merge pull request' button. If you don't, a few of them will find that button irresistable.
* Also warn students NOT to **close** their pull request. Otherwise, some will close the first pull request, make a new change, and then open a second (or third) pull request.  When this happens, you can find yourself grading an obsolete submission! (Of course, a student could create a second pull request without closing the first pull request, but I haven't seen anybody do that yet.) It's hard to protect yourself against this problem without adding extra steps to your workflow for every individual submission. However, if you filter your GitHub emails into a separate folder&mdash;and better yet, have several such folders, with one specifically for pull requests&mdash;spending a few seconds at the beginning of grading to look over that folder can help reassure you that nobody did this.
* Finally, warn students NOT to push changes after the deadline. If so, such changes will automatically be included in their existing pull request. Again, a review of the GitHub email folder can make late pushes like these obvious, because you'll get an email for each push into a pull request. But you won't get an email if the student both failed to create a pull request and pushed changes after the deadline! (GitHub Classroom has a feature that copies and saves the commit that existed at the deadline, but my scripts do not attempt to use this feature.)