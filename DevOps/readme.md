# Definition
DevOps is combination of Development and Operations which helps to deliver applications and services at a high velocity. It’s a perspective that eliminates barriers between people, processes, and technologies so IT can deliver fast and compliant software to the customer.
DevOps = Development (Dev) and Operations (Ops)
- **Development** teams focus on writing code, building features, and creating software.
- **Operations** teams are responsible for the infrastructure, maintaining systems, and ensuring reliability.

# Development Previously:
- **The Waterfall Model** is when IT operated in a siloed, **rigid sequential manner**. A software project would move through rigid phases: requirements, design, development, testing, and finally, deployment. Each phase was the responsibility of a different team.
- **Agile Methodology** is a way of developing software in **small, incremental cycles** (called iterations or sprints), allowing teams to adapt quickly to changing requirements and deliver value continuously.

# Development Nowdays
DevOps provides an extension of **Agile principles, applying them to the entire software delivery pipeline**. The focus shifts to automation, continuous integration and delivery (CI/CD), and fostering a culture of shared responsibility and rapid feedback loops. The goal is to deliver value to the customer faster and more reliably. Eliminating the "wait time" between development completion and operational deployment.

The Mechanics of **Continuous Integration (CI)**:
- **Frequent Merging**: Developers push code to a shared repository multiple times a day to avoid "merge hell."
- Automated Builds: Every commit triggers a fresh build of the application to ensure it compiles correctly.
- Early Bug Detection: **Automated unit tests catch errors** seconds after they are introduced.
- Standardized Environments: Ensures **code is built in a clean, consistent environment every time**.
- Immediate Feedback: **Developers receive instant notifications of pass/fail results**, maintaining momentum.

**Continuous Delivery(CD)**: Always Ready for Release
- Deployment Readiness: **Every build that passes CI is automatically packaged and prepared for production**.
- Automated Staging: **Code is automatically deployed to a testing environment that mimics the real world**.
- UAT & Integration Testing: Advanced tests are run in staging to ensure the app works with databases and other services.
- Manual Trigger: The final "Go-Live" is a business decision, executed with a single click.
- Reduced Release Risk: Since the release process is automated and practiced daily, "Release Day" becomes a non-event.

Continuous Deployment: The Speed of Modern Tech
- Full Automation: Every change that passes the testing gauntlet goes straight to the customers.
- Eliminating Bottlenecks: Removes human intervention from the deployment path to maximize speed.
- High-Confidence Testing: Requires a robust suite of automated tests (End-to-End, Smoke tests, and Performance tests).
- Rapid Iteration: Enables features and fixes to reach users in minutes rather than weeks.
- Advanced Monitoring: Relies on real-time alerts to automatically "roll back" a deployment if errors are detected.

The Pillars of a CI/CD Pipeline
- Source Control: A central version-controlled repository (Git) serving as the single source of truth.
- Build Automation: Tools that compile and package code without manual human steps.
- Test Automation: A comprehensive library of tests that gate-keep the code from moving forward.
- Deployment Automation: Scripts and tools that handle the complex task of updating servers or containers.
- Observability: Integrated monitoring that feeds production data back into the start of the next CI/CD cycle.

The Pillars of a CI/CD Pipeline
- Source Control: A central version-controlled repository (Git) serving as the single source of truth.
- Build Automation: Tools that compile and package code without manual human steps.
- Test Automation: A comprehensive library of tests that gate-keep the code from moving forward.
- Deployment Automation: Scripts and tools that handle the complex task of updating servers or containers.
- Observability: Integrated monitoring that feeds production data back into the start of the next CI/CD cycle.

