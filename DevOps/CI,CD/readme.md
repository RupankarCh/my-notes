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

