# Actions Runner or CI/CD
A **CI/CD pipeline** is an automated process that builds, tests, and deploys code whenever developers make changes. 

Simple flow of a CI/CD pipeline:

1.Developer pushes code to Git repo
2.Platform (e.g., GitHub Actions, Jenkins, GitLab CI/CD) triggers the pipeline
3.Code is built
4.Automated tests run
5.If tests pass → code is deployed to staging or production

Create a github repo.
Create another branch.
Create an folder ".github/workflow/name.yml". 
write the Github Actions Workflow Configuration and commit it.

## CI – Continuous Integration
Developers frequently push code to a shared repository (like GitHub). The system automatically builds the project and runs tests to make sure the new code doesn’t break anything.

Continuous Integration (CI)
• Developers push code frequently
• Code pushed to Git
• Automatically build + test
Examples:
• GitHub
• GitLab

## CD – Continuous Delivery / Continuous Deployment
After the code passes tests, it can be automatically prepared for release or deployed to production.

Continuous Delivery (CD)
• Code is ready for deployment automatically
• Build> Test> Ready for production

Continuous Deployment (Advanced CD)
Automatically deploy to production without manual approval

**CI/CD Tools**
- Jenkins
- GitHub Actions
- GitLab CI



# **GitHub Actions workflow** configuration (YAML) designed to automate the deployment of a website to **GitHub Pages**.
<img width="342" height="420" alt="image" src="https://github.com/user-attachments/assets/36687de1-8af5-401f-aa20-ae7eab31e3fb" />

---

### Core Structure
*   **`jobs:`**: Defines the start of the automation tasks. A workflow can have multiple jobs running in parallel or sequence.
*   **`deploy:`**: The custom name for this specific job. 
*   **`runs-on: ubuntu-latest`**: Tells GitHub to run this job on a virtual machine using the newest version of Ubuntu Linux.

### Permissions
These grant the temporary "GITHUB_TOKEN" specific rights to perform the deployment:
*   **`contents: read`**: Allows the action to download (read) your repository code.
*   **`pages: write`**: Required to actually upload and update the GitHub Pages site.
*   **`id-token: write`**: Used for secure authentication with GitHub's deployment servers.

### The Steps
Each "step" is an individual task performed in order:

1.  **`Checkout code`**: Uses the `actions/checkout` tool to pull your code from the repository into the runner's workspace.
2.  **`Setup Pages`**: Uses `actions/configure-pages` to prepare the environment settings specific to GitHub Pages.
3.  **`Upload artifact`**: 
    *   **`path: .`**: Packages the files in the current directory (the root `.`) into a compressed "artifact" for deployment.
4.  **`Deploy to GitHub Pages`**: Takes that uploaded artifact and pushes it live to your public URL.

---


How to see the Triggers:

Repository> Settings> Pages> Select Deploy from Branch to Github Action> Actions> Select the .yml file and you can see all the steps defined in the .yml file of the Github Actions Workflow file.

The Rise of Native CI/CD
- Platform Integration: Moving away from external tools (like Jenkins) to tools built directly into the code repository.
- Single Source of Truth: Code, infrastructure (IaC), and deployment logic (YAML) all live in a single repository.
- Unified Security: Managing access to code and deployment permissions through a single identity provider.
- Reduced Overhead: No need to manage separate servers, plugins, or complex integrations between different vendors.
- Developer Experience: Developers can see the results of their builds and tests directly within their Pull Requests.


GitHub Actions: Event-Driven Automation
- Workflow Components: Workflows -+ Jobs -+ Steps —+ Actions.
- The Marketplace: Leveraging thousands of reusable components to build complex pipelines in minutes.
- Matrix Builds: Effortlessly testing your code across multiple operating systems and language versions at once.
- GitHub-Native Secrets: Securely storing API keys and cloud credentials that are only accessible during the build.
- Flexible Triggers: Automating tasks based on pushes, releases, or even cron-job schedules.

GitLab CI/CD: The "One Tool" Philosophy
- Stage-Based Execution: Defining clear boundaries between Building, Testing, and Deploying for maximum safety.
- Integrated Container Registry: Storing your Docker images directly within GitLab for faster, more secure deployments.
- Security First: Automated vulnerability scanning and license compliance checks are built into every pipeline.
- GitLab Runners: The flexibility to use GitLab's managed cloud runners or host your own for specialized hardware needs.
- Advanced Releases: Native support for "Canary Deployments" and "Feature Flags" to control how new code reaches users.

Bitbucket Pipelines: Integrated Simplicity
- Atlassian Synergy: Creating a seamless link between Jira issues, Bitbucket code, and final deployments.
- Serverless Model: No infrastructure to manage; Bitbucket scales the build environment automatically based on your needs.
- Pipe-Based Configuration: Using "Pipes" (similar to Actions) to simplify tasks like deploying to AWS, Azure, or Heroku.
- Deployment Tracking: Visualizing the health and history of deployments across different environments (Dev, QA, Prod). Quick Onboarding: Designed for teams that want to go from "zero to CI/CD" with minimal YAML configuration.

Choosing Your Repository Strategy
- Ecosystem Alignment: If you use Jira, Bitbucket is the logical choice. If you use open-source, GitHub is the standard.
- Complexity Requirements: Choose GitLab for high-compliance enterprise needs; choose GitHub Actions for rapid, community-driven growth.
- Cost Management: Evaluate the "Build Minutes" included in each plan, as costs can scale with the frequency of your deployments.
- Security Posture: Consider the built-in scanning tools versus third-party integrations required for each platform.
- Long-Term Scalability: All three platforms can handle massive scale, but their management style (Marketplace vs. Built-in) may dictate your team's workflow.

