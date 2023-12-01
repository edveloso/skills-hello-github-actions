<header>

<!--
  <<< Author notes: Course header >>>
  Include a 1280x640 image, course title in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280x640 social image, auto delete head branches.
  Add your open source license, GitHub uses MIT license.
-->

# Hello GitHub Actions

_Create a GitHub Action and use it in a workflow._

</header>

<!--

## Step 1: Create a workflow file

_Welcome to "Hello GitHub Actions"! :wave:_

**What is _GitHub Actions_?**: GitHub Actions is a flexible way to automate nearly every aspect of your team's software workflow. You can automate testing, continuously deploy, review code, manage issues and pull requests, and much more. The best part, these workflows are stored as code in your repository and easily shared and reused across teams. To learn more, check out these resources:

- The GitHub Actions feature page, see [GitHub Actions](https://github.com/features/actions).
- The "GitHub Actions" user documentation, see [GitHub Actions](https://docs.github.com/actions).

**What is a _workflow_?**: A workflow is a configurable automated process that will run one or more jobs. Workflows are defined in special files in the `.github/workflows` directory and they execute based on your chosen event. For this exercise, we'll use a `pull_request` event.

- To read more about workflows, jobs, and events, see "[Understanding GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)".
- If you want to learn more about the `pull_request` event before using it, see "[pull_request](https://docs.github.com/en/developers/webhooks-and-events/webhooks/webhook-events-and-payloads#pull_request)".

To get you started, we used actions to go ahead and made a branch and pull request for you.

### :keyboard: Activity: Create a workflow file

1. Open a new browser tab, and navigate to this same repository. Then, work on the steps in your second tab while you read the instructions in this tab.
1. Create a pull request to view all the changes you'll make throughout this course. Click the **Pull Requests** tab, click **New pull request**, set `base: main` and `compare:welcome-workflow`, click **Create pull request**.
1. Navigate to the **Code** tab.
1. From the **main** branch dropdown, click on the **welcome-workflow** branch.
1. Navigate to the `.github/workflows/` folder, then select **Add file** and click on **Create new file**.
1. In the **Name your file...** field, enter `welcome.yml`.
1. Add the following content to the `welcome.yml` file:
  <<< Author notes: Step 2 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  Historic note: The previous course had troubleshooting steps for people not using the GitHub UI
  <<< Author notes: Step 3 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->


## Step 3: Add actions to your workflow file

_Nice work adding a job to your workflow! :dancer:_

Workflows have jobs, and jobs have steps. So now we'll add steps to your workflow.

**What are _steps_?**: Actions steps will run during our job in order. Each step is either a shell script that will be executed, or an action that will be run. Each step must pass for the next step to run. Actions steps can be used from within the same repository, from any other public repository, or from a published Docker container image.

In our action, we post a comment on the pull request using a [bash](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) script and [GitHub CLI](https://cli.github.com/).

### :keyboard: Activity: Add Actions steps to your workflow file

1. Open your `welcome.yml` file.
2. Update the contents of the file to:
   ```yaml
   name: Post welcome comment
   on:
     pull_request:
       types: [opened]
   permissions:
     pull-requests: write
   jobs:
     build:
       name: Post welcome comment
       runs-on: ubuntu-latest
       steps:
         - run: gh pr comment $PR_URL --body "Welcome to the repository!"
           env:
             GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
             PR_URL: ${{ github.event.pull_request.html_url }}
   ```
3. Click **Start commit** in the top right of the workflow editor.
4. Type your commit message and commit your changes directly to your branch.
5. Wait about 20 seconds for actions to run, then refresh this page (the one you're following instructions from) and an action will automatically close this step and open the next one.

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

Get help: [Post in our discussion board](https://github.com/orgs/skills/discussions/categories/hello-github-actions) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
