# 🚀 Lab Activity: The Code Multiverse Challenge

**Total Duration:** 3 Hours (180 Minutes)  
**Target Audience:** IT College Students  
**Mission:** Transition from a "Local Developer" to a "Global Contributor" by navigating the Git workflow.

---

## 🕒 Mission 1: Tracking Time (Local Workflow)

**⏱️ Suggested Time:** 60 Minutes  
**Objective:** Move a project through the "Three Stages of Git."

### 1.1 The Project Start (15 Mins)

1. Create a workspace named `multiverse-lab`.
2. Inside, create a file named `profile.md` containing a brief professional bio.

### 1.2 The Three-Stage Loop (30 Mins)

Your goal is to successfully take a "Snapshot" of your work.

- **Task A (Initialize):** Tell Git to start watching this folder.
- **Task B (Staging):** Move your file to the "Outbox" (Staging Area).
- **Task C (Commit):** Permanently seal the vault with a descriptive message.
- **Observation:** Run a status command after each task. What changes in the terminal output at each step?

### 1.3 The Time Machine (15 Mins)

1. Add a "Technical Skills" section to your bio.
2. Use a command to see exactly what lines were added/removed before you save.
3. Commit this change as a new version.

---

## 🕒 Mission 2: The Multiverse (Branching & Conflicts)

**⏱️ Suggested Time:** 60 Minutes  
**Objective:** Manage parallel versions of a project and resolve timeline clashes.

### 2.1 Divergent Timelines (30 Mins)

Imagine a client wants a "Dark Mode" version of your profile, but you must keep the "Standard" version safe.

- **Task:** Create a new branch named `feature-dark-mode` and switch to it.
- **Modification:** Change the text style/content in `profile.md` to reflect a "Dark Theme." Commit this change.
- **The Jump:** Switch back to the main branch.
- **Critical Thinking:** What happened to the "Dark Mode" text you just wrote? Is it gone?

### 2.2 The Timeline Clash (Merge Conflict) (30 Mins)

1. Stay on the `main` branch. Change the first line of your bio and commit it.
2. Now, attempt to merge `feature-dark-mode` into `main`.
3. **The Incident:** You should see a "Merge Conflict" error.
4. **The Surgery:** Open VS Code. Look for the conflict markers.
   - **Task:** Manually edit the file to combine both versions into a perfect final draft. Finish by "sealing" the resolution with a final commit.

---

## 🕒 Mission 3: Team Profile Gallery (Collaborative Project)

**⏱️ Suggested Time:** 60 Minutes  
**Objective:** Work as a team of 5 collaborators on a shared repository using fork, clone, and pull requests.

### 3.1 Setup: Team Repository Structure (Instructor-led, 5 Mins)

**Repository:** This repository (`mastering-the-code-multiverse`) already includes:

- A `Global Guestbook` folder with a comprehensive `README.md`
- A `Global Guestbook/profiles/` folder for student participant HTML pages
- Ready for GitHub Project Board (Kanban) with columns: "To Do", "In Progress", "Review", "Done"
- Ready for Issues to be created, one for each student participant (e.g., "Create profile page for [Participant Name]")

**Instructor Action Before Lab:**

1. ✅ Repository structure is ready (Global Guestbook folder exists)
2. Share the repository URL with students

**Team Formation:** Students are divided into teams of 5.

### 3.2 The Fork & Clone (10 Mins)

Each team member will:

1. **Fork the Repository:** Navigate to the instructor's `mastering-the-code-multiverse` repository and click "Fork" to create your own copy.
2. **Clone Your Fork:** Use Git to clone YOUR forked repository to your local machine.
3. **Verify Remote:** Check that your fork is set as the `origin` remote.

```bash
git clone https://github.com/YOUR-USERNAME/mastering-the-code-multiverse.git
cd mastering-the-code-multiverse
cd "Global Guestbook"
git remote -v
```

### 3.3 Create Your HTML Profile Page (30 Mins)

Each team member creates their own profile page:

1. **Create a Branch:** Create a feature branch for your work.

   ```bash
   git checkout -b add-profile-yourname
   ```

2. **Create Your HTML File:** Inside the `Global Guestbook/profiles/` folder, create a file named `yourname.html`.

**Note:** A detailed HTML template with modern styling is available in `Global Guestbook/README.md`

**Quick Template Structure:**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>[Your Name] - Profile</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        max-width: 600px;
        margin: 50px auto;
        padding: 20px;
        background-color: #f4f4f4;
      }
      .profile-card {
        background: white;
        padding: 30px;
        border-radius: 10px;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      }
      h1 {
        color: #333;
      }
      .section {
        margin: 20px 0;
      }
    </style>
  </head>
  <body>
    <div class="profile-card">
      <h1>[Your Name]</h1>
      <div class="section">
        <h2>About Me</h2>
        <p>[Write a brief bio about yourself]</p>
      </div>
      <div class="section">
        <h2>Skills</h2>
        <ul>
          <li>[Skill 1]</li>
          <li>[Skill 2]</li>
          <li>[Skill 3]</li>
        </ul>
      </div>
      <div class="section">
        <h2>Interests</h2>
        <p>[Your hobbies or interests]</p>
      </div>
    </div>
  </body>
</html>
```

3. **Commit Your Work:**

   ```bash
   git add "Global Guestbook/profiles/yourname.html"
   git commit -m "Add profile page for [Your Name]"
   ```

4. **Push to Your Fork:**

   ```bash
   git push origin add-profile-yourname
   ```

### 3.4 Create a Pull Request (15 Mins)

1. Go to your fork on GitHub. You should see a banner suggesting to "Compare & pull request."
2. Click it and create a Pull Request (PR) to the **main repository** (instructor's repo).
3. In the PR description:
   - Briefly describe what you added
   - Mention which profile is yours

### 3.5 Code Review & Merge (5 Mins)

**Team Activity:**

- Review at least one other team member's Pull Request
- Leave a constructive comment
- Instructor merges approved PRs

---

## 🕒 Mission 4: Staying in Sync (Optional Challenge)

**⏱️ Suggested Time:** If time permits  
**Objective:** Learn to keep your fork synchronized with the original repository.

### 4.1 Adding the Upstream Remote

After other team members' PRs are merged, your fork becomes outdated.

1. **Add Upstream Remote:** Connect to the original repository.

   ```bash
   git remote add upstream https://github.com/INSTRUCTOR-USERNAME/mastering-the-code-multiverse.git
   ```

2. **Fetch & Merge Updates:**

   ```bash
   git checkout main
   git fetch upstream
   git merge upstream/main
   ```

3. **Update Your Fork:**
   ```bash
   git push origin main
   ```

**Critical Thinking:** Why is it important to sync your fork before starting new work?

---

## ✅ Mission Completion Checklist

- [ ] I have at least 3 unique "save points" (commits) in my project history.
- [ ] I successfully jumped between two parallel branches.
- [ ] I manually fixed a merge conflict without deleting the whole folder.
- [ ] I forked a repository and cloned it to my local machine.
- [ ] I created an HTML profile page and pushed it to my fork.
- [ ] I created a Pull Request to the main repository.
- [ ] I reviewed at least one teammate's Pull Request.
- [ ] My profile page is merged into the team gallery.

---

## 📋 Instructor Preparation Checklist

**Before the Lab:**

1. ✅ Repository `mastering-the-code-multiverse` is ready with `Global Guestbook` folder
2. ✅ `Global Guestbook/README.md` contains detailed instructions and HTML template
3. ✅ `Global Guestbook/profiles/` folder exists and ready for student submissions
4. Share the repository URL with students

**During the Lab:**

- Direct students to read `Global Guestbook/README.md` for detailed instructions
- Monitor Pull Requests in real-time
- Guide students through merge conflicts if they arise
- Merge approved PRs
- Celebrate completed profiles!

---

## 🎯 Learning Outcomes

By the end of this lab, students will be able to:

1. ✅ Use Git's three-stage workflow (Working Directory → Staging → Repository)
2. ✅ Create and switch between branches
3. ✅ Resolve merge conflicts manually
4. ✅ Fork and clone repositories
5. ✅ Create and manage Pull Requests
6. ✅ Collaborate effectively in a team using Git workflow
7. ✅ Understand the difference between `origin` and `upstream` remotes

---

> _"In the Multiverse of Code, Git is your anchor. Master the workflow, and you master the industry."_
