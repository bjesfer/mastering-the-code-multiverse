# Git Commit Best Practices

A comprehensive guide to writing meaningful commits and maintaining a clean project history.

---

## Table of Contents

1. [Why Commit Messages Matter](#why-commit-messages-matter)
2. [Anatomy of a Good Commit Message](#anatomy-of-a-good-commit-message)
3. [The Seven Rules of Great Commits](#the-seven-rules-of-great-commits)
4. [Atomic Commits](#atomic-commits)
5. [What to Commit (and What Not to Commit)](#what-to-commit-and-what-not-to-commit)
6. [Conventional Commits](#conventional-commits)
7. [Examples: Good vs Bad](#examples-good-vs-bad)
8. [Common Commit Patterns](#common-commit-patterns)
9. [When to Commit](#when-to-commit)
10. [Advanced Tips](#advanced-tips)

---

## Why Commit Messages Matter

Your commit messages serve multiple critical purposes:

### 1. **Documentation**
Commits create a permanent record of **why** changes were made, not just **what** changed. Six months from now, you or your teammates will need to understand the reasoning behind a decision.

### 2. **Code Reviews**
Well-written commit messages make code reviews faster and more effective. Reviewers can quickly understand the intent behind changes without having to dig through the entire codebase.

### 3. **Debugging**
When a bug is discovered, clear commit messages help you quickly identify when and why a problematic change was introduced using tools like `git bisect` or `git log`.

### 4. **Collaboration**
In team environments, commit messages are a primary form of communication. They help team members understand what everyone is working on and why.

### 5. **Project History**
A well-maintained commit history serves as a timeline of the project's evolution, making it easier to understand how the codebase arrived at its current state.

---

## Anatomy of a Good Commit Message

A well-structured commit message follows this format:

```
<type>: <subject>

<body>

<footer>
```

### Subject Line (Required)
- **50 characters or less**
- Capitalized first word
- No period at the end
- Written in imperative mood ("Add feature" not "Added feature")
- Summarizes **what** the commit does

### Body (Optional but Recommended)
- **Separated from subject by a blank line**
- Wrapped at 72 characters per line
- Explains **why** the change was necessary
- Describes **what** was changed at a high level
- Can include multiple paragraphs

### Footer (Optional)
- References to issues, tickets, or breaking changes
- Format: `Fixes #123` or `Closes #456`
- Breaking changes: `BREAKING CHANGE: description`

### Example

```
Add user authentication with JWT tokens

Implement JWT-based authentication to replace the previous session-based
approach. This change improves scalability by making the API stateless
and allows for easier horizontal scaling of the application.

The authentication flow now works as follows:
- User logs in with credentials
- Server validates and returns JWT token
- Client includes token in subsequent requests
- Server validates token without session lookup

Fixes #234
Related to #245
```

---

## The Seven Rules of Great Commits

### Rule 1: Separate Subject from Body with a Blank Line

**Why?** Many Git tools expect this format. Without the blank line, tools like `git log --oneline` won't work correctly.

**Bad:**
```
Fix user login bug
The login form was not validating email addresses correctly.
```

**Good:**
```
Fix user login bug

The login form was not validating email addresses correctly.
```

### Rule 2: Limit the Subject Line to 50 Characters

**Why?** 50 characters is a guideline that forces you to be concise and ensures the message displays properly in GitHub, GitLab, and other tools.

**Bad:**
```
Update the user authentication system to use JWT tokens instead of session-based authentication
```

**Good:**
```
Replace session auth with JWT tokens
```

### Rule 3: Capitalize the Subject Line

**Why?** Consistency and readability. Proper capitalization makes your commit history look professional.

**Bad:**
```
add user profile page
```

**Good:**
```
Add user profile page
```

### Rule 4: Do Not End the Subject Line with a Period

**Why?** The subject line is a title, not a sentence. Periods waste precious character space.

**Bad:**
```
Fix navigation menu bug.
```

**Good:**
```
Fix navigation menu bug
```

### Rule 5: Use the Imperative Mood in the Subject Line

**Why?** Git itself uses imperative mood when creating commits (e.g., "Merge branch..."). Following this convention creates consistency.

Think of it as completing this sentence: "If applied, this commit will **[your subject line]**"

**Bad:**
```
Fixed bug in checkout process
Added new payment method
Updated documentation
```

**Good:**
```
Fix bug in checkout process
Add new payment method
Update documentation
```

### Rule 6: Wrap the Body at 72 Characters

**Why?** Git doesn't automatically wrap text. Wrapping at 72 characters ensures your messages are readable in various Git tools and terminal windows.

### Rule 7: Use the Body to Explain What and Why, Not How

**Why?** The code itself shows **how** something works. The commit message should explain **what** changed at a high level and, more importantly, **why** the change was necessary.

**Bad:**
```
Update user model

Changed the User class to include a new field called lastLoginDate.
Added a getter and setter for the field. Updated the constructor to
initialize the field to null.
```

**Good:**
```
Add last login tracking to user model

Track when users last logged in to enable the new "inactive account
cleanup" feature. Accounts inactive for more than 6 months will be
flagged for review per the new security policy.

The lastLoginDate field is nullable to handle legacy accounts that
don't have this information yet.
```

---

## Atomic Commits

### What is an Atomic Commit?

An atomic commit is a **single, self-contained unit of work** that:
- Implements **one logical change**
- Can be reverted without side effects
- Passes all tests
- Leaves the codebase in a working state

### Why Atomic Commits Matter

1. **Easier Code Reviews:** Reviewers can understand each change independently
2. **Simplified Debugging:** Use `git bisect` to quickly find which commit introduced a bug
3. **Clean History:** Makes the project timeline easier to understand
4. **Safer Reverts:** Roll back specific changes without affecting unrelated work
5. **Better Collaboration:** Team members can cherry-pick specific features

### Examples

**Bad (Non-Atomic):**
```
Fix login bug, add user profile page, update README, refactor database queries
```
This commit does four different things. If the profile page has a bug, you can't revert it without also reverting the login fix.

**Good (Atomic):**
```
Fix login validation bug

Add user profile page

Update README with setup instructions

Refactor database queries for performance
```
Four separate commits, each addressing one concern.

### How to Create Atomic Commits

#### Use `git add -p` (Interactive Staging)

Stage changes interactively to split unrelated changes into separate commits:

```bash
git add -p
```

This allows you to stage specific chunks of changes, even within the same file.

#### Commit Frequently

Don't wait until the end of the day to commit. Commit each logical unit of work as you complete it.

#### Split Large Changes

If you realize you've made multiple unrelated changes:

1. Use `git add -p` to stage related changes
2. Commit those changes
3. Repeat for the next logical unit

---

## What to Commit (and What Not to Commit)

### ✅ DO Commit

1. **Source Code**
   - Application code
   - Configuration files (without secrets)
   - Build scripts
   - Database migration files

2. **Documentation**
   - README files
   - API documentation
   - Code comments
   - Architecture diagrams

3. **Tests**
   - Unit tests
   - Integration tests
   - Test fixtures (non-sensitive data)

4. **Dependencies**
   - Dependency lock files (`package-lock.json`, `Gemfile.lock`)
   - Essential vendor libraries (if not using a package manager)

### ❌ DO NOT Commit

1. **Secrets and Credentials**
   - API keys
   - Passwords
   - Private keys
   - Authentication tokens
   - `.env` files with sensitive data

2. **Build Artifacts**
   - Compiled binaries
   - Distribution packages
   - Build output directories (`dist/`, `build/`)

3. **Dependencies**
   - `node_modules/`
   - `vendor/` (when using package managers)
   - Downloaded packages

4. **IDE and OS Files**
   - `.DS_Store` (macOS)
   - `Thumbs.db` (Windows)
   - `.idea/` (JetBrains IDEs)
   - `.vscode/` (unless project-specific settings)

5. **Logs and Temporary Files**
   - Log files
   - Cache files
   - Temporary files
   - `.tmp`, `.cache` directories

6. **Local Configuration**
   - Personal IDE settings
   - Local database credentials
   - Development-only configurations

### Use `.gitignore`

Create a `.gitignore` file to automatically exclude unwanted files:

```gitignore
# Dependencies
node_modules/
vendor/

# Build output
dist/
build/
*.exe
*.dll

# Environment variables
.env
.env.local

# IDE
.vscode/
.idea/
*.swp

# OS
.DS_Store
Thumbs.db

# Logs
*.log
logs/
```

---

## Conventional Commits

Conventional Commits is a specification for commit messages that makes them machine-readable and helps automate versioning and changelog generation.

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Common Types

| Type | Description | Example |
|------|-------------|---------|
| `feat` | New feature | `feat: add user registration` |
| `fix` | Bug fix | `fix: resolve login timeout issue` |
| `docs` | Documentation only | `docs: update API documentation` |
| `style` | Code style changes (formatting) | `style: format code with prettier` |
| `refactor` | Code refactoring | `refactor: simplify user validation logic` |
| `perf` | Performance improvements | `perf: optimize database queries` |
| `test` | Adding or updating tests | `test: add unit tests for auth service` |
| `chore` | Maintenance tasks | `chore: update dependencies` |
| `ci` | CI/CD changes | `ci: add GitHub Actions workflow` |
| `build` | Build system changes | `build: update webpack configuration` |
| `revert` | Revert a previous commit | `revert: revert commit abc123` |

### Scope (Optional)

The scope specifies what part of the codebase is affected:

```
feat(auth): add password reset functionality
fix(api): handle null response from user service
docs(readme): add installation instructions
```

### Breaking Changes

For changes that break backward compatibility:

```
feat(api): change user endpoint response format

BREAKING CHANGE: The user endpoint now returns an object instead of an
array. Update client code to access user data via response.data.user
instead of response.data[0].
```

### Examples

```
feat(shopping-cart): add item quantity selector

Allow users to specify item quantity directly in the cart instead of
having to add items multiple times.

Closes #123
```

```
fix(payment): prevent double-charging on slow connections

Add request idempotency to prevent duplicate payment processing when
users click the submit button multiple times on slow network connections.

Fixes #456
```

```
docs: add contribution guidelines

Create CONTRIBUTING.md with guidelines for pull requests, code style,
and testing requirements.
```

---

## Examples: Good vs Bad

### Example 1: Feature Addition

**Bad:**
```
updates
```

**Better:**
```
Add search feature
```

**Best:**
```
feat: add full-text search to product catalog

Implement Elasticsearch integration for product search to improve
search relevance and performance. The new search supports:
- Full-text search across product names and descriptions
- Filter by category, price range, and availability
- Sorting by relevance, price, and rating

Search results are cached for 5 minutes to reduce load on Elasticsearch.

Closes #789
```

### Example 2: Bug Fix

**Bad:**
```
fixed it
```

**Better:**
```
Fix navigation bug
```

**Best:**
```
fix: prevent navigation menu overlap on mobile devices

The navigation menu was overlapping with page content on screens
smaller than 768px due to incorrect z-index values. This affected
approximately 30% of mobile users based on analytics.

Changed z-index from 100 to 1000 for the mobile menu and adjusted
the backdrop blur to improve visibility.

Fixes #234
```

### Example 3: Refactoring

**Bad:**
```
changes to user code
```

**Better:**
```
Refactor user authentication
```

**Best:**
```
refactor: extract authentication logic into separate service

Move authentication-related code from UserController into a dedicated
AuthService class to improve testability and separation of concerns.

This refactoring:
- Reduces UserController complexity from 450 to 180 lines
- Makes authentication logic reusable across controllers
- Simplifies unit testing with dependency injection
- No functional changes or breaking changes

Part of the effort to improve code maintainability outlined in #567
```

### Example 4: Documentation

**Bad:**
```
docs
```

**Better:**
```
Update README
```

**Best:**
```
docs: add troubleshooting section to README

Add common issues and solutions section covering:
- Database connection errors
- Port conflicts during development
- Environment variable configuration
- SSL certificate issues in production

Based on the 10 most common support requests from the last quarter.
```

---

## Common Commit Patterns

### Initial Commit

```
Initial commit

Set up project structure with basic configuration and dependencies.
```

or

```
feat: initialize project with Express.js and TypeScript

Bootstrap the project with:
- Express.js web framework
- TypeScript configuration
- ESLint and Prettier for code quality
- Jest for testing
- Basic project structure (src/, tests/, docs/)
```

### Merge Commits

Let Git generate these automatically. Don't manually create merge commit messages unless there's something special to note.

### Revert Commits

```
revert: revert "feat: add social login"

This reverts commit abc123def456.

The social login feature is causing authentication issues in production.
Reverting to investigate and fix before re-deploying.

See issue #890 for details.
```

### Work in Progress (WIP)

For commits on feature branches that aren't ready for review:

```
WIP: implement user profile editing

Basic form structure in place. Still need to add:
- Input validation
- API integration
- Error handling
```

**Note:** WIP commits should be squashed or rebased before merging to main.

---

## When to Commit

### Commit Often

Commit early and commit often. It's easier to combine commits later than to split them apart.

### Good Times to Commit

1. **After completing a logical unit of work**
   - A function is complete and tested
   - A bug is fixed
   - A test is written

2. **Before attempting something risky**
   - Major refactoring
   - Trying a new approach
   - Experimental features

3. **Before taking a break**
   - End of work day
   - Before lunch
   - Before switching tasks

4. **After tests pass**
   - All tests are passing
   - Code compiles without errors
   - Linter is happy

### When NOT to Commit

1. **Code doesn't work**
   - Don't commit broken code to shared branches
   - Exception: WIP commits on feature branches (but clean them up before merging)

2. **Tests are failing**
   - Fix the tests first
   - Or fix the code if the tests are correct

3. **Mixed concerns**
   - Don't bundle unrelated changes together
   - Split them into separate commits

---

## Advanced Tips

### Tip 1: Write Commit Messages in Your Editor

For detailed commit messages, use your preferred text editor:

```bash
git config --global core.editor "code --wait"  # VS Code
git config --global core.editor "vim"          # Vim
git config --global core.editor "nano"         # Nano
```

Then simply:
```bash
git commit
```

Your editor will open for you to write the message.

### Tip 2: Use Commit Templates

Create a template file (`~/.gitmessage.txt`):

```
# <type>: <subject> (max 50 characters)

# <body>: Explain what and why (wrap at 72 characters)

# <footer>: Issues, breaking changes, etc.

# Type can be:
#   feat     (new feature)
#   fix      (bug fix)
#   docs     (documentation)
#   style    (formatting)
#   refactor (refactoring code)
#   test     (adding tests)
#   chore    (maintenance)
```

Configure Git to use it:
```bash
git config --global commit.template ~/.gitmessage.txt
```

### Tip 3: Amend the Last Commit

Made a mistake in your last commit? Amend it:

```bash
# Fix the code
git add .
git commit --amend
```

**Warning:** Only amend commits that haven't been pushed yet!

### Tip 4: Use Interactive Rebase to Clean Up History

Before merging a feature branch, clean up the commit history:

```bash
git rebase -i main
```

This allows you to:
- Squash multiple commits into one
- Reword commit messages
- Reorder commits
- Drop unnecessary commits

### Tip 5: Reference Issues Automatically

Use keywords to automatically close issues:

```
Closes #123
Fixes #456
Resolves #789
```

GitHub, GitLab, and other platforms will automatically close these issues when the commit is merged.

### Tip 6: Co-authored Commits

For pair programming or collaboration:

```
Add payment processing feature

Co-authored-by: John Doe <john@example.com>
Co-authored-by: Jane Smith <jane@example.com>
```

### Tip 7: Sign Your Commits

For security and verification:

```bash
# Set up GPG key
git config --global user.signingkey YOUR_KEY_ID
git config --global commit.gpgsign true

# Commits will now be signed
git commit -m "feat: add secure feature"
```

---

## Quick Reference Checklist

Before committing, ask yourself:

- [ ] Does my commit represent **one logical change**?
- [ ] Does the subject line explain **what** changed in 50 characters or less?
- [ ] Is the subject line written in **imperative mood**?
- [ ] Does the subject line start with a **capital letter**?
- [ ] Does the subject line **not end with a period**?
- [ ] Does the body explain **why** the change was necessary?
- [ ] Is the body wrapped at **72 characters**?
- [ ] Have I referenced any **related issues**?
- [ ] Are **all tests passing**?
- [ ] Have I excluded **secrets and sensitive data**?
- [ ] Is the **code in a working state**?

---

## Additional Resources

- [Conventional Commits Specification](https://www.conventionalcommits.org/)
- [Git Commit Best Practices - Chris Beams](https://chris.beams.io/posts/git-commit/)
- [How to Write a Git Commit Message](https://cbea.ms/git-commit/)
- [Semantic Versioning](https://semver.org/)
- [GitHub - About Commit Signature Verification](https://docs.github.com/en/authentication/managing-commit-signature-verification)

---

## Conclusion

Writing good commit messages is a skill that improves with practice. The extra time spent crafting clear, descriptive commits pays dividends in:

- **Faster debugging**
- **Easier code reviews**
- **Better team communication**
- **Clearer project history**
- **Professional reputation**

Remember: **Your commit messages are a conversation with your future self and your team. Make them count.**

---

*"A well-maintained Git history is like a well-written story — it tells you not just what happened, but why it matters."*
