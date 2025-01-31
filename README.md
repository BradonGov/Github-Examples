## GitHub Actions Overview
### What is GitHub actions: 
GitHub Actions allows you to **automate your build, test, and deployment pipeline.** You can create workflows that **build and test every pull request to your repository**, or **deploy merged pull requests to production**. GitHub Actions lets you **run workflows when other events happen in your repository**.

### Components of GitHub Actions
You can configure workflow to start when an event occurs in your repository, such as a pull request. Your workflow has one or more jobs it runs (sequentaly or in parallel). Each job will run inside its own virtual machine runner (or container). Each job has one or more steps where it either runs scripts or run an action.

### Workflow
A workflow is a **configurable automated process** that will run one or more jobs. Workflows are a **YAML** file that's inside your repository and **will run when triggered by an event in your repository**, or they can be **triggered manually**, or **at a defined schedule**.

Workflows are in the ```.github/workflows``` directory in a repository. A repository can have multiple workflows, each of which can perform a different set of tasks such as:

1. Building and testing pull requests
2. Deploying your application every time a release is created
3. Adding a label whenever a new issue is opened

### Events
An **event** is a **specific activity** in a repository that **triggers a workflow** run. For example, an activity can originate from GitHub when someone creates a pull request, opens an issue, or pushes a commit to a repository.

### Jobs
A **job** is a **set of steps** in a workflow that is executed on the same runner. Each step **is either a shell script that will be executed**, or **an action that will be run**.

### Actions
An action is a custom application for the GitHub Actions platform that performs a **complex but frequently repeated task**. Use an action to **help reduce the amount of repetitive code** that you write in your **workflow files**.

### Runners
A runner is a server that runs your workflows when they're triggered. Each runner can run a single job at a time.

## Workflow syntax For Github Actions
Github actions uses YAML to create the workflows
### About YAML
YAML is a data serialisation language designed to be directly writable and readable by humans.
#### Common syntax rules for YAML
Based on this [article](https://learnxinyminutes.com/yaml/) 
```YAML
# Comments in YAML look like this.

key: value
another_key: Another value goes here.
a_number_value: 100

# The number 1 will be interpreted as a number, not a boolean. 
# If you want it to be interpreted as a boolean, use true.
boolean: true
null_value: null
another_null_value: ~
key with spaces: value

# Yes and No (doesn't matter the case) will be evaluated to boolean 
# true and false values respectively.
# To use the actual value use single or double quotes.
no: no            # evaluates to "no": false
yes: No           # evaluates to "yes": false
not_enclosed: yes # evaluates to "not_enclosed": true
enclosed: "yes"   # evaluates to "enclosed": yes

# Notice that strings don't need to be quoted. However, they can be.
however: 'A string, enclosed in quotes.'
'Keys can be quoted too.': "Useful if you want to put a ':' in your key."


# Special characters must be enclosed in single or double quotes
special_characters: "[ John ] & { Jane } - <Doe>"

# Multiple-line strings.
# Literal block turn every newline within the string into a literal newline (\n).
literal_block: |
  This entire block of text will be the value of the 'literal_block' key,
  with line breaks being preserved.

  The literal continues until de-dented, and the leading indentation is
  stripped.

# Nesting uses indentation. 2 space indent is preferred (but not required).
a_nested_map:
  key: value
  another_key: Another Value
  another_nested_map:
    hello: hello

# Maps don't have to have string keys.
0.25: a float key

# Sequences (equivalent to lists or arrays) look like this
# (note that the '-' counts as indentation):
a_sequence:
  - Item 1
  - Item 2
  - 0.5  # sequences can contain disparate types.
  - Item 4
  - key: value
    another_key: another_value
  - - This is a sequence
    - inside another sequence
  - - - Nested sequence indicators
      - can be collapsed

# Since YAML is a superset of JSON, you can also write JSON-style maps and
# sequences:
json_map: { "key": "value" }
json_seq: [ 3, 2, 1, "takeoff" ]
```

### Common YAML syntax for github actions
```name```: The name of the workflow. [Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#name) | Example: 
```run-name```: The name for workflow runs generated from the workflow.
```on```: To automatically trigger a workflow, use on to define which events can cause the workflow to run.[Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#on)  
```env```: A map of variables that are available to the steps of all jobs in the workflow.[Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#env)  
```defaults```: Use defaults to create a map of default settings that will apply to all jobs in the workflow.[Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#defaults)  

| Syntax | Definition | More Info | Example |
|----------|----------|----------|----------|
| ```name``` | The name of the workflow.  |  ```name: Update Test Server```   | [Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#name) |
| ```run-name``` | The name for workflow runs generated from the workflow. | ```run-name: Deploy to ${{ inputs.deploy_target }} by @${{ github.actor }}```   |  [Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#run-name)  |
| ```on``` |To automatically trigger a workflow, use on to define which events can cause the workflow to run.  |  ```on: push```, ```on: [push, pull]```   | [Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#on)  |
| ```env``` |A map of variables that are available to the steps of all jobs in the workflow.  |  ```env:SERVER: production```   | [Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#env) |
| ```defaults``` | Use defaults to create a map of default settings that will apply to all jobs in the workflow.  |  ```name: Update Test Server```   | [Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#defaults) |
| ```name``` | The name of the workflow.  |  ```name: Update Test Server```   | [Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#name) |
| ```name``` | The name of the workflow.  |  ```name: Update Test Server```   | [Docs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#name) |



