# How to Contribute to TLDR Pages

The TLDR Pages project simplifies documentation for various command-line utilities. Contributing to this project is a great way to help others. Follow the steps below to contribute effectively and submit a proper pull request (PR).

### Prerequisite: Sign the CLA (Contributor License Agreement)

Before contributing, you'll need to sign the TLDR CLA. Here are the steps:
1. **Go to the CLA page**: Visit the [CLA page](https://cla-assistant.io/tldr-pages/tldr).
2. **Agree to the CLA**: Click on the **"I Agree"** button.
3. **Authorize with your GitHub account**: Follow the authorization steps to sign the agreement.

![CLA PAGE](https://github.com/user-attachments/assets/bb40868e-8591-4deb-b30d-7c923db33389)

Once this is done, you're ready to contribute!

### 1. Fork and Clone the Repository

1. **Fork the TLDR repository**:
   Go to the [TLDR Pages GitHub repository](https://github.com/tldr-pages/tldr) and click on **Fork** at the top-right corner of the page.

2. **Clone your forked repository**:
   After forking, clone the repository to your local machine:
   ```bash
   git clone https://github.com/your-username/tldr.git
   cd tldr
   ```

---

### 2. Create a New Branch for Your Changes

Before making any changes, create a new branch to keep your work organized and separate from the main branch.

```bash
git checkout -b add-audit2allow-page
```
*Replace `add-audit2allow-page` with a descriptive name for your branch.*

---

### 3. Write or Update a Command Page

1. **Find the correct directory**: Navigate to the appropriate directory depending on the platform the command applies to (`linux`, `osx`, `windows`, etc.). For example:
   ```bash
   cd pages/linux
   ```

2. **Create a new Markdown file**: The file should be named after the command you're documenting. For example:
   ```bash
   touch audit2allow.md
   ```

3. **Write the command page**: The format for the command page should follow the TLDR guidelines, typically consisting of:
   - A brief description of the command.
   - A link to official documentation.
   - At most 8 examples of how to use the command.

#### Example:

```markdown
# audit2allow

> Create an SELinux local policy module to allow rules based on denied operations found in logs.
> More information: <https://man7.org/linux/man-pages/man1/audit2allow.1.html>.

- Generate and install a local policy to allow access for all denied services:

`sudo audit2allow --all -M {{local_policy_name}} && sudo semodule -i {{local_policy_name}}.pp`

- Generate and install a local policy module to grant access to a specific service from the audit logs:

`sudo grep {{apache2}} /var/log/audit/audit.log | sudo audit2allow -M {{local_policy_name}} && sudo semodule -i {{local_policy_name}}.pp`

- View the Type Enforcement (.te) file for a local policy:

`cat {{local_policy_name}}.te`
```

---

### 4. Lint the Page

Before committing, run the TLDR linter to ensure the page meets the required formatting and syntax.

1. Install `tldr-lint`:
   ```bash
   npm install --global tldr-lint
   ```

2. Run the linter on your page:
   ```bash
   tldr-lint pages/linux/audit2allow.md
   ```

If there are no errors, you can proceed. If errors appear, fix them and re-run the linter.

---

### 5. Commit and Push Your Changes

Once your changes are complete and verified with the linter, commit the changes:

1. **Add your file**:
   ```bash
   git add pages/linux/audit2allow.md
   ```

2. **Commit with a meaningful message**:
   ```bash
   git commit -m "audit2allow: add page"
   ```

3. **Push your branch**:
   ```bash
   git push origin add-audit2allow-page
   ```

---

### 6. Create a Pull Request (PR)

After pushing your branch, go to your repository on GitHub. You should see a notification to create a pull request (PR) for your new branch.

1. **Click "Compare & pull request"**.
2. **Fill out the PR template**:
   - Title your PR in the format `command: add page`.
   - In the description, could you mention which platform the command applies to and provide other relevant details?

#### **Checklist in the PR Description**:

Before submitting the PR, you must fill in the checklist to ensure you’ve followed all contribution guidelines.

Example PR Checklist:

```markdown
<!--
Thank you for contributing!
Please fill in the following checklist, removing items that do not apply.
See also https://github.com/tldr-pages/tldr/blob/main/CONTRIBUTING.md
-->

- [x] The page(s) are in the correct platform directories: `linux`.
- [x] The page(s) have at most 8 examples.
- [x] The page description(s) have links to documentation or a homepage.
- [x] The page(s) follow the [content guidelines](https://github.com/tldr-pages/tldr/blob/main/CONTRIBUTING.md#guidelines).
- [x] The PR title conforms to the recommended [templates](https://github.com/tldr-pages/tldr/blob/main/CONTRIBUTING.md#commit-message-and-pr-title).
- **Version of the command being documented (if known): audit2allow .1**
```

**Example**:
![PR Example](https://github.com/user-attachments/assets/24526dbd-216b-4749-a6d4-fdd39b3b6db1)


---

### 7. Submit the PR and Respond to Feedback

After submitting the PR, the TLDR maintainers will review your changes. They may ask for adjustments. Be sure to respond to any feedback and make the necessary changes.

1. **To update your PR**: 
   If changes are requested, make those changes locally, commit them, and push them to the same branch:
   ```bash
   git add .
   git commit -m "Update audit2allow page"
   git push origin add-audit2allow-page
   ```

2. The PR will automatically update with your changes.

---

### Additional Resources:

- **TLDR Contributing Guidelines**: Follow the official [contributing guide](https://github.com/tldr-pages/tldr/blob/main/CONTRIBUTING.md).
- **Using TLDR Lint**: [TLDR Lint](https://github.com/tldr-pages/tldr-lint) helps ensure that pages meet formatting requirements.

