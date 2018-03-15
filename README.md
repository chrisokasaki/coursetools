# coursetools

For the past few semesters, I've been using [GitHub Classroom](https://classroom.github.com/) to manage programming assignments in my courses.  This repo is for [some tools](#Tools) that I've created to make this process easier. See below for a description of my [workflow](#Workflow). If you use&mdash;or are considering switching to&mdash;a similar process, then these tools may also be useful to you.  Also see some [Gotchas](#Gotchas) that you may encounter in the process.

# Tools

* [prs: Easily create links to student pull requests for grading](prs)
* more to come...

# Workflow

My general workflow is

* Before the semester begins
  * Apply through [GitHub Education](https://education.github.com/) for a free organization, which allows for unlimited private repos. (And if you use a separate repo per student for every assignment, you'll need a LOT of private repos!) My experience has been that this is usually approved within a few hours.  **Warning: Don't expect to use the same organization across multiple semesters.  As things stand right now, you'll probably need to reapply every semester.**
  * Once you have the organization, go to [GitHub Classroom](https://classroom.github.com/) and create a &ldquo;classroom&rdquo; for your course.
* On each assignment
  * Create a private repo in the organization containing the starter code for the assignment. Also create a separate branch (eg, `original`) that's even with the branch you expect the students to work in.  
  * Go to your classroom on GitHub Classroom and create a new Individual assignment. (Note that the &ldquo;Individual&rdquo; setting works fine for small teams that are using pair programming.)  It will be easier if you use a standard naming scheme for your assignments.  I use `hw1`, `hw2`, ...  When creating the assignment make sure to make the repos Private (if you don't want all the students to be able to see each other's code), and fill in the location of your starter code.
  * GitHub Classroom will then give you a link, which you can distribute to the students. When they click on the link, it will automatically create a repo for them, populated with your starter code.  Within GitHub Classroom you can see who has &ldquo;accepted&rdquo; the assignment (this list is useful way of collecting the GitHub usernames of your students).
  * Students work on the assignment, and turn it in by committing and pushing back to GitHub.
  * I then have students create a Pull Request between the branch containing their submission, and the separate branch that was even with the starter code (what I called `original` above).
  * Finally, I visit each Pull Request to grade and leave feedback.

# Gotchas

* Sometimes, when a student clicks on the link to accept the assignment, the new repo is created, but the starter code is not copied over. Make sure that they know that this can happen, and that they should contact you if it does.  The simplest fix is to go into the empty repo, delete it, and tell the student to wait a few minutes and try again.
* You will get an overwhelming number of emails from GitHub about student activity in their repos.  Set up one or more email filters early in the semester to automatically re-route these emails to some chosen folder(s) rather than to your inbox. Don't just auto-delete them though! These emails can be quite useful in giving you a glimpse into when students start an assignment.  They're also an easy way to tell when somebody turns in an assignment late or pushes further changes after creating the pull request.
* If you forget to check the box on an assignment to make student repos private, then students will be able to see each other's code. For some assignments, that may be okay, perhaps even desirable, but for many assignments it could be a disaster.
