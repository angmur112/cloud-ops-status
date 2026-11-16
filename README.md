# Deploy an Operations Status Dashboard

**Project Link:** [View Project](https://nextwork.ai/projects/59bdd861-94df-4575-a1ca-10766f41bdf4)

**Author:** Angelo Murphy

---

## Defining the Automated Delivery Goal

### Purpose of the dashboard and delivery pipeline

I am building an operations status dashboard with GitHub Actions validating each release before GitHub Pages publishes it. I will be watching the pipeline reject a defective page before repairing the issue and deploying the dashboard.

## Preparing a Version-Controlled Workspace

### Setting up the local repository

In this step, I am getting ready to:\
Verify Git in Visual Studio Code's integrated PowerShell terminal.\
Sign in to GitHub through your browser.\
Prepare an empty local Git repository on main.

### Verifying development tools and GitHub access

Here is what confirms that each component is ready:\
Local Tool (Git): Running the command git --version in your terminal prints a version number. This output confirms that your integrated terminal can successfully find and run Git commands.

Cloud Account (GitHub): Completing the authentication flow in your browser and confirming that you are successfully signed into your GitHub account. This ensures you have a secure destination ready to receive your dashboard's code pushed.

![Preparing a Version-Controlled Workspace](https://nextwork.ai/angmur112/uploads/59bdd861-94df-4575-a1ca-10766f41bdf4_g4ea1mir)

## Building and Publishing the Status Dashboard

### Creating the first local dashboard

In this step, I'm building a local operations dashboard with three service cards. Preview the dashboard in your browser. Commit the files to a public GitHub repository.

![Building and Publishing the Status Dashboard](https://nextwork.ai/angmur112/uploads/59bdd861-94df-4575-a1ca-10766f41bdf4_m82ctcau)

### Publishing the dashboard source to GitHub

Check Your Repository: Open your cloud-ops-status repository page in your web browser and refresh the page.\
Verify the Files: You should see both index.html and styles.css listed in your repository.\
Verify the Branch: These files must be visible on the active main branch.\
Verify the Commit Message: The latest commit should display the exact message you used when committing: Build local status dashboard.

## Creating a Release Gate for Production Changes

### Adding validation and deployment jobs

In this step, I'm configuring GitHub Pages to use GitHub Actions. Create a workflow with validation and deployment jobs. Push the workflow and inspect its first validation result.

![Creating a Release Gate for Production Changes](https://nextwork.ai/angmur112/uploads/59bdd861-94df-4575-a1ca-10766f41bdf4_ybppqsgk)

## Fixing the Gate and Launching the Live Site

### Repairing the required production title

In this step, I'm repairing the production page title. Publish the title repair to GitHub. Confirm that the dependent jobs pass before opening the live dashboard.

![Fixing the Gate and Launching the Live Site](https://nextwork.ai/angmur112/uploads/59bdd861-94df-4575-a1ca-10766f41bdf4_49yt7l2z)

### Validation before deployment

I observed that the job order in your GitHub Actions workflow proved two critical things before your dashboard was deployed:\
Successful Dependency: It proved that the deploy job was fully dependent on the validate job. Because of the needs: validate parameter, the deployment could not start until the validation checks finished successfully.\
Release Protection: It proved that the validation gate successfully controls your live environment. Since the sequence requires validation to succeed first, it ensures that defective or unchecked code is blocked from publishing to GitHub Pages.\
In short, the sequence of seeing a green validate job run right before a green deploy job proves that deployment waited for the repaired page to pass validation.

## Proving Continuous Delivery in Production

### Shipping a visible dashboard update

In this step, I'm replacing the local-only note with a production deployment message.

Commit the update and push it to main.

Trace the successful workflow to the changed live page.

![Proving Continuous Delivery in Production](https://nextwork.ai/angmur112/uploads/59bdd861-94df-4575-a1ca-10766f41bdf4_85lfoc8x)

## Enforcing an Operational Maintenance Runbook

![Enforcing an Operational Maintenance Runbook](https://nextwork.ai/angmur112/uploads/59bdd861-94df-4575-a1ca-10766f41bdf4_bnsxifo9)

### Protecting releases with runbook validation

The updated validation job acts as an automated release gate, protecting production from being updated with defective or incomplete content. Here is exactly how it prevents an incomplete site from deploying:\
Enforcing File Existence: The updated script includes a file-path check (Test-Path -Path "./maintenance.html"). If the maintenance.html runbook file is missing entirely, the script immediately throws an error: maintenance.html is missing.\
Verifying Critical Content: Beyond checking if the file is there, it parses the document to ensure the main title matches exactly ("\<h1\>Maintenance Runbook\</h1\>"). If this header is incomplete, modified, or missing, it triggers the error: Required runbook heading is missing.\
Pipeline Job Dependency: In your YAML configuration, the deployment job is explicitly bound to the validation job using the needs: validate instruction. If any single check in the validation job fails (by throwing an error), the validation job terminates with a "failed" red status. As a result, GitHub Actions skips the dependent deploy job altogether.\
By making both the file presence and its specific structure mandatory before the deployment step can begin, you ensure that no version of the operational site can reach GitHub Pages without its accompanying, complete runbook documentation!

## Reflecting on DevOps Tools and Delivery Skills

### Tools and concepts developed

Key Tools Used:\
Local Command Line (Git Bash): You leveraged your Windows development terminal to run Git commands, open local web files, stage updates, and verify software versions.\
Source Control (Git & GitHub): You learned how to turn a local project directory into a tracked repository, commit stable code states with clear intent, and publish your work securely to a cloud repository.\
Web Basics (HTML & CSS): You built a responsive, functional dashboard showing the operational status of three core production services.\
Automation Engines (GitHub Actions): You wrote automated workflow configuration scripts in YAML format to orchestrate automated checks and deployment tasks.\
Cloud Hosting (GitHub Pages): You configured a live, public URL to automatically host and serve your dashboard directly from your repository's main branch.

Core Concepts Learned:\
source control: Tracking iterative code updates over time, ensuring your development changes are securely organized before publishing.\
CI/CD pipeline Architecture: Designing automation sequences split into logical steps (validation checks vs. live deployment phases) that run automatically on every code change.\
validation gate Enforcement: Creating a "gatekeeper" process. You learned how writing script checks (like verifying file presence with PowerShell's Test-Path or checking HTML headings) and binding them as dependencies stops broken deployments.\
continuous delivery: Ensuring that when your repository successfully passes all validation criteria, your live operations website immediately and safely updates without manual intervention.

### Project experience and challenge

This project took me approximately 120 minutes to complete. The most challenging parts for me was the GitHub actions setup and understanding how it the YAML file works.

### Next learning goal

CI/CD pipeline Architecture\
continuous delivery\
Containers
