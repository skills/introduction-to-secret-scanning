<header>

<!--
  <<< Author notes: Course header >>>
  Read <https://skills.github.com/quickstart> for more information about how to build courses using this template.
  Include a 1280×640 image, course name in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Next to "About", add description & tags; disable releases, packages, & environments.
  Add your open source license, GitHub uses the MIT license.
-->

# Introduction to secret scanning

_GitHub scans repositories for known types of secrets, to prevent fraudulent use of secrets that were committed accidentally. In this GitHub Skills course you will learn how to enable secret scanning to identify serets and prevent them from being committed to your repository._

</header>

<!--
  <<< Author notes: Course start >>>
  Include start button, a note about Actions minutes,
  and tell the learner why they should take the course.
-->

## Welcome

Plain-text credentials accidentally stored in repositories on GitHub are a common target for attackers.  In fact, we find well over a million tokens stored on the GitHub platform each year. Secret scanning is a powerful tool which allows teams to identify these plain-text credentials, remove them, and create rules to prevent them from being written to GitHub in the first place.

Secret scanning is available for free for all public repositories. Organizations that need secret scanning capabilities for private repositories should review [GitHub Advanced Security](https://docs.github.com/en/enterprise-cloud@latest/get-started/learning-about-github/about-github-advanced-security). GitHub Advanced Security allows you to take advantage of additional security features such as [code scanning](https://docs.github.com/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning), [dependency review](https://docs.github.com/en/enterprise-cloud@latest/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review), and [security overview](https://docs.github.com/en/enterprise-cloud@latest/code-security/security-overview/about-security-overview).

- **Who is this for**: Developers, DevOps Engineers, security teams.
- **What you'll learn**: How to identify plain-text credentials in your repository and how to prevent them from being written in the first place.
- **Prerequisites**: Basics of git and GitHub functionality. We recommend you complete [Introduction to GitHub](https://github.com/skills/introduction-to-github).
- **How long**: This course takes less than 15 minutes to complete.

In this course, you will:

1. Enable secret scanning
2. Identify secrets stored in your repository
3. Enable push protection
4. Stop secrets from being written to your repository

### How to start this course

<!-- For start course, run in JavaScript:
'https://github.com/new?' + new URLSearchParams({
  template_owner: 'TBD-organization',
  template_name: 'TBD-course-name',
  owner: '@me',
  name: 'TBD-organization-TBD-course-name',
  description: 'My clone repository',
  visibility: 'public',
}).toString()
-->


[![start-course](https://user-images.githubusercontent.com/1221423/235727646-4a590299-ffe5-480d-8cd5-8194ea184546.svg)](https://github.com/new?template_owner=skills&template_name=introduction-to-secret-scanning&owner=%40me&name=skills-introduction-to-secret-scanning&description=GitHub+Skills:+Introduction+to+Secret+Scanning&visibility=public)

1. Right-click **Start course** and open the link in a new tab.
2. In the new tab, most of the prompts will automatically fill in for you.
   - For owner, choose your personal account or an organization to host the repository.
   - You will need to make the repository public, as private repositories do not have access to secret scanning without a [GitHub Advanced Security](https://docs.github.com/en/enterprise-cloud@latest/get-started/learning-about-github/about-github-advanced-security) license.
   - Scroll down and click the **Create repository** button at the bottom of the form.
3. After your new repository is created, wait about 20 seconds, then refresh the page. Follow the step-by-step instructions in the new repository's README.

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

Get help: [Post in our discussion board](https://github.com/orgs/skills/discussions/categories/introduction-to-secret-scanning) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
