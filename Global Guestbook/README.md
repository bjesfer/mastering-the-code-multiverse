# 📖 Global Guestbook - Team Profile Gallery

Welcome to the **Global Guestbook**! This is a collaborative project where students practice the complete Git workflow: fork, clone, branch, commit, push, and pull request.

---

## 🎯 Mission Objective

Each team member will create their own **HTML profile page** and contribute it to this shared guestbook. By the end of this mission, you'll have hands-on experience with:

- 🍴 Forking repositories
- 📥 Cloning your fork locally
- 🌿 Creating feature branches
- 📝 Making commits with meaningful messages
- 🚀 Pushing changes to your fork
- 🔄 Creating Pull Requests
- 📋 Working with GitHub Issues
- 📊 Managing tasks on a Project Board

---

## 👥 Team Structure

This project is designed for **5 collaborators** working simultaneously on a single repository. Each member will:

1. Create their own unique HTML profile page
2. Work on an assigned GitHub Issue
3. Submit their contribution via Pull Request
4. Review at least one teammate's work

---

## 🚀 How to Contribute (Step-by-Step)

### Step 1: Fork This Repository

1. Click the **"Fork"** button at the top right of this repository
2. This creates your own copy under your GitHub account

### Step 2: Clone Your Fork

```bash
git clone https://github.com/YOUR-USERNAME/mastering-the-code-multiverse.git
cd mastering-the-code-multiverse
cd "Global Guestbook"
```

### Step 3: Create a Feature Branch

```bash
git checkout -b add-profile-yourname
```

**Example:** `git checkout -b add-profile-john-doe`

### Step 4: Create Your Profile Page

Create a new HTML file named `yourname.html` in the `Global Guestbook/profiles/` folder.

**File naming convention:** Use lowercase with hyphens (e.g., `john-doe.html`)

#### 📄 Profile Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[Your Name] - Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .profile-card {
            background: white;
            max-width: 600px;
            width: 100%;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            animation: fadeIn 0.6s ease-in;
        }
        
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 3px solid #667eea;
        }
        
        h1 {
            color: #333;
            font-size: 2.5em;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #666;
            font-style: italic;
        }
        
        .section {
            margin: 25px 0;
        }
        
        .section h2 {
            color: #667eea;
            margin-bottom: 15px;
            font-size: 1.5em;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .section p {
            color: #555;
            line-height: 1.6;
            font-size: 1.1em;
        }
        
        .skills-list {
            list-style: none;
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .skills-list li {
            background: #667eea;
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.9em;
            transition: transform 0.2s;
        }
        
        .skills-list li:hover {
            transform: scale(1.05);
            background: #764ba2;
        }
        
        .footer {
            text-align: center;
            margin-top: 30px;
            padding-top: 20px;
            border-top: 2px solid #eee;
            color: #999;
            font-size: 0.9em;
        }
    </style>
</head>
<body>
    <div class="profile-card">
        <div class="header">
            <h1>👤 [Your Full Name]</h1>
            <p class="subtitle">[Your Role/Title - e.g., "Aspiring Full-Stack Developer"]</p>
        </div>
        
        <div class="section">
            <h2>📝 About Me</h2>
            <p>
                [Write a brief bio about yourself. Include your background, 
                what you're studying, your interests in technology, and what 
                drives your passion for coding.]
            </p>
        </div>
        
        <div class="section">
            <h2>💻 Technical Skills</h2>
            <ul class="skills-list">
                <li>HTML/CSS</li>
                <li>JavaScript</li>
                <li>Git & GitHub</li>
                <li>[Add More Skills]</li>
                <li>[Add More Skills]</li>
            </ul>
        </div>
        
        <div class="section">
            <h2>🎯 Interests & Hobbies</h2>
            <p>
                [Share your hobbies, interests outside of coding, 
                favorite projects, or what you do for fun.]
            </p>
        </div>
        
        <div class="section">
            <h2>🚀 Goals</h2>
            <p>
                [What are your career goals? What do you hope to achieve 
                in the tech industry?]
            </p>
        </div>
        
        <div class="footer">
            Created with ❤️ as part of the Git Collaboration Mission
        </div>
    </div>
</body>
</html>
```

### Step 5: Commit Your Changes

```bash
git add profiles/yourname.html
git commit -m "Add profile page for [Your Name]"
```

**Good commit message example:** `Add profile page for John Doe`

### Step 6: Push to Your Fork

```bash
git push origin add-profile-yourname
```

### Step 7: Create a Pull Request

1. Go to your fork on GitHub
2. You'll see a banner: **"Compare & pull request"** - click it
3. Fill in the PR details:
   - **Title:** `Add profile page for [Your Name]`
   - **Description:** 
     ```
     Closes #[issue-number]
     
     ## Changes
     - Added HTML profile page for [Your Name]
     - Included sections: About, Skills, Interests, Goals
     
     ## Checklist
     - [x] File follows naming convention (lowercase-with-hyphens.html)
     - [x] All template sections are filled out
     - [x] HTML is valid and properly formatted
     - [x] Profile is unique and personalized
     ```
4. Click **"Create Pull Request"**
5. Move your issue to **"Review"** on the Project Board

### Step 8: Code Review

- Review at least **one teammate's Pull Request**
- Leave a constructive comment
- Check for:
  - ✅ All sections are filled out
  - ✅ HTML is properly structured
  - ✅ No broken code
  - ✅ Profile is creative and personal

---

## 📋 GitHub Issues & Project Board

### Working with Issues

1. Go to the **Issues** tab
2. Find an issue assigned to you (or claim an unassigned one)
3. Click on the issue and assign it to yourself
4. Move the issue card to **"In Progress"** on the Project Board
5. Reference the issue in your Pull Request using: `Closes #[issue-number]`

### Project Board Columns

- **To Do:** Tasks not yet started
- **In Progress:** Currently working on
- **Review:** Pull Request submitted, awaiting review
- **Done:** Merged and completed

---

## 📁 Folder Structure

```
Global Guestbook/
├── README.md              ← You are here
├── profiles/              ← Put your HTML files here
│   ├── john-doe.html
│   ├── jane-smith.html
│   ├── ...
└── jesfer_babao.txt      ← Example guestbook entry
```

---

## ⚠️ Important Guidelines

### ✅ DO:
- Create **unique** and **personalized** content
- Use proper HTML structure
- Follow the naming convention (lowercase-with-hyphens)
- Write meaningful commit messages
- Be respectful in code reviews
- Help teammates if they're stuck

### ❌ DON'T:
- Copy someone else's profile
- Edit other people's files without permission
- Commit directly to the `main` branch
- Skip creating a feature branch
- Leave placeholder text like "[Your Name]" in your final submission

---

## 🎓 Learning Resources

- [GitHub Docs - Forking a Repository](https://docs.github.com/en/get-started/quickstart/fork-a-repo)
- [GitHub Docs - Creating a Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)
- [Git Branching Basics](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
- [Writing Good Commit Messages](https://chris.beams.io/posts/git-commit/)

---

## 🏆 Success Criteria

You've successfully completed this mission when:

- ✅ Your profile page is created and personalized
- ✅ Your Pull Request is submitted
- ✅ You've reviewed at least one teammate's PR
- ✅ Your PR is approved and merged
- ✅ Your issue is moved to "Done"

---

## 🆘 Need Help?

If you encounter issues:

1. Check if your branch is up to date with `main`
2. Make sure you're pushing to YOUR fork, not the original repo
3. Verify your remote settings: `git remote -v`
4. Ask your teammates or instructor for help
5. Review the error message carefully - Git errors are usually descriptive

---

## 🎉 Congratulations!

By completing this mission, you've practiced the **real-world workflow** used by professional developers every day. You're now ready to contribute to open-source projects and collaborate with teams globally!

---

**Remember:** In the Multiverse of Code, collaboration is the superpower. Keep learning, keep coding, and keep sharing! 🚀

---

*Last Updated: February 2026*  
*Part of the "Mastering the Code Multiverse" Lab Activity*
