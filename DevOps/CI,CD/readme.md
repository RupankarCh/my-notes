# Actions Runner or CI/CD
A **CI/CD pipeline** is an automated process that builds, tests, and deploys code whenever developers make changes. 

## CI – Continuous Integration
Developers frequently push code to a shared repository (like GitHub). The system automatically builds the project and runs tests to make sure the new code doesn’t break anything.

## CD – Continuous Delivery / Continuous Deployment
After the code passes tests, it can be automatically prepared for release or deployed to production.

Simple flow of a CI/CD pipeline:

1.Developer pushes code to Git repo

2.Platform (e.g., GitHub Actions, Jenkins, GitLab CI/CD) triggers the pipeline

3.Code is built

4.Automated tests run

5.If tests pass → code is deployed to staging or production


