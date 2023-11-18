# Week 1 Project:
## Goal
The goal is to establish a robust development process by implementing version control with Git, comprehensive unit tests, and effective workflows, ensuring that only thoroughly tested code is merged into the Master branch.
## Task 1:Creating Git repository
Create a Git repository to centralize collaboration, allowing seamless code sharing, version control, and collaboration on the calculator application.
## Task 2: Implementing comprehensive unit tests
To guarantee the calculator application's reliability, implement thorough unit tests covering diverse mathematical operations, edge cases, and input scenarios. Rigorous testing will catch bugs, ensuring correct functionality in different scenarios.
## Task 3:Setting up effective CI/CD workflows
In a professional software development setting, prioritizing code quality and stability is essential. You'll set up reliable CI/CD workflows to ensure that only well-tested and reviewed code is merged into the main branch of the calculator application. Embracing code reviews and CI/CD practices, you'll automate testing processes on the CI/CD platform, validating each code change thoroughly before release to maintain high code integrity.

## Requirements
Inorder to complete the project, you'll need these:
- Python 3.9 "https://www.python.org/downloads/"
- Git "https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup"
- pip3 "https://pip.pypa.io/en/stable/installation/"

  # Instructions
  ## Step 1: Get the initial starter code onto your system
  - Fork this "https://github.com/yudhiesh/week1-devops" GitHub repository to work on your own copy of the project and make and save changes.
  ## Step 2: Add unit tests
  ```from src.calculator import add, div, mul, sub


  def test_add():
    assert add(1, 1) == 2


  def test_sub():
    assert sub(1, 1) == 0


  def test_mul():
    assert mul(1, 1) == 1


  def test_div():
    assert div(2, 1) == 2
  ``` 

 ## Step 3: Create a workflow
 First, create a directory called .github/workflows in the directory that contains the .git folder. Then, create a workflow YAML file called  ci_cd_wf.yml in the new directory.

Include the following text in the ci_cd_wf.yml file:
```name: test

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - "*"

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Check out repo code
        uses: actions/checkout@v3

      - name: Setup Python
        uses: actions/setup-python@v3
        with:
          python-version: "3.x"

      - name: Install Dependencies
        run: |
          python -m pip install -r requirements.txt
      - name: Run tests
        run: |
          python -m pytest -v tests

```
## Step 4: Check our Gitflow with a new branch

Create a new feature branch, "test," to observe how the CI/CD pipeline responds to a failed pull request. To intentionally introduce an error, let's make a purposeful mistake in the code.
``` git switch -c test
On this branch, let's change the test_add() method so that it asserts a False statement:
``` def test_add():
    assert add(1,1) == 0
```
Now, let's git add, commit, and push our changes

## Step 5: Fix all the errors to make a successful build
- Change back the test_add() function:
- Add, commit, and push our changes to the test branch again:

## Congratulations on finishing this project! 🎉 You've dedicated a lot of effort so far. Let's maintain our momentum and move on to Week 2!
