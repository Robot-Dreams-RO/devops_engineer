####
TODO
####

=========
Questions
=========

1. What file extension is used for GitHub Actions workflow files?

    a. .workflow
    b. .yml or .yaml
    c. .github
    d. .actions

2. Where must the GitHub Actions workflow files be placed in a repository?

    a. In the root directory of the repository
    b. In the .github/workflows/ directory
    c. In the actions/ directory
    d. In the workflow/ directory

3. Which event can trigger a GitHub Actions workflow?

    a. Push to a repository
    b. A pull request is opened
    c. A GitHub release is created
    d. All of the above

4. What is a runner in GitHub Actions?

    a. A type of workflow
    b. A user who triggers the workflow
    c. The virtual environment in which the workflow runs
    d. A specific task within a job


5. How can you reuse workflows in GitHub Actions?

    a. By linking to another workflow file in the repository
    b. Using the uses keyword in your workflow to reference an action
    c. By copying the workflow file to another repository
    d. It is not possible to reuse workflows


6. What is a job in the context of GitHub Actions?

    a. A step in a workflow
    b. An individual task that runs sequentially in a workflow
    c. A collection of steps that run in parallel
    d. A set of workflows that are executed on a trigger event

7. How are secrets stored and used in GitHub Actions?

    a. In plain text files within the repository
    b. As environment variables in the virtual environment
    c. In the repository settings as encrypted secrets
    d. They are not supported; all sensitive data must be hard-coded

=======
Answers
=======

1. Answer: b. .yml or .yaml

    Explanation: GitHub Actions workflows are defined in YAML files with .yml or .yaml extensions.

2. Answer: b. In the .github/workflows/ directory

    Explanation: Workflow files must be placed in the .github/workflows/ directory of your repository.

3. Answer: d. All of the above

    Explanation: GitHub Actions workflows can be triggered by a variety of events such as a push, pull request, release, and many more.

4. Answer: c. The virtual environment in which the workflow runs

    Explanation: A runner is a server that has the GitHub Actions runner application installed. It runs one job at a time.

5. Answer: b. Using the uses keyword in your workflow to reference an action

    Explanation: The uses keyword can be used to reuse an action as a step within a job.

6. Answer: b. An individual task that runs sequentially in a workflow
    
    Explanation: A job is a set of steps in a workflow that executes on the same runner. By default, jobs run in parallel unless specified otherwise.

7. Answer: c. In the repository settings as encrypted secrets

    Explanation: Secrets are stored encrypted and exposed to the workflow run as environment variables.