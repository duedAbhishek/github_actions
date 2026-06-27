# GitHub Actions Explained

GitHub Actions is GitHub's built-in automation tool. It lets you define workflows in YAML files so that your repository can run tasks automatically when something happens, such as a push, a pull request, or a scheduled time.

## What GitHub Actions does

A workflow is a set of instructions that tells GitHub what to do. Each workflow can contain one or more jobs, and each job can run several steps.

Typical uses include:

- Running tests automatically
- Checking code quality
- Building a project
- Deploying an app
- Sending notifications

Because this is a public repository, others can also learn from the workflow and copy the structure for their own projects.

## How CI/CD works with GitHub Actions

CI/CD stands for Continuous Integration and Continuous Delivery/Deployment.

- Continuous Integration (CI): every time code is pushed, GitHub can run checks such as installing dependencies and running tests.
- Continuous Delivery/Deployment (CD): if the checks pass, the workflow can continue to build or deploy the application.

A simple CI/CD flow looks like this:

1. A developer pushes code to the repository.
2. GitHub detects the event and starts the workflow.
3. The workflow checks out the repository.
4. It installs dependencies and runs tests.
5. If everything passes, it can build or deploy the project.

## A dummy GitHub Actions example

Create a workflow file in the repository at .github/workflows/demo.yml.

```yaml
name: Demo CI/CD Workflow

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Install dependencies
        run: python -m pip install --upgrade pip

      - name: 24f3004165@ds.study.iitm.ac.in
        run: echo "Hello, world!"

      - name: Run a dummy check
        run: echo "CI pipeline is working"
```

### What each part means

- `name`: the name shown in GitHub's Actions tab
- `on`: the event that triggers the workflow
- `jobs`: the tasks that will run
- `runs-on`: the virtual machine environment
- `steps`: the sequence of commands or reusable actions
- `uses`: a prebuilt action from the GitHub Actions marketplace
- `run`: a shell command to execute

## How to trigger the workflow

You can trigger this workflow by:

- pushing changes to the main branch
- opening a pull request targeting main

After pushing the file, open the Actions tab in GitHub to see the workflow run.

## Tips for learning and sharing

- Keep workflows simple at first
- Use secrets for private tokens or API keys
- Avoid exposing sensitive information in logs
- Copy this pattern and adapt it for your own projects

This example is intentionally basic, but it shows the core idea behind GitHub Actions and how CI/CD pipelines can be automated.
