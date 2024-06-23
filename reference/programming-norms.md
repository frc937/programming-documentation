# Programming Norms

This is a list of norms and standards for how we handle our code—for example, how we like to handle parentheses, variable names, etc.

## General Norms

If not otherwise specified on this page, default to the Google Java Style Guide:

{% embed url="https://google.github.io/styleguide/javaguide.html" %}

### Formatting (Spotless)

To enforce and auto-apply that style (along with some other basic style conventions), we use Spotless ([https://github.com/diffplug/spotless](https://github.com/diffplug/spotless)) with the following configuration ([https://github.com/frc937/robot2023/blob/cowtown2023/build.gradle](https://github.com/frc937/robot2023/blob/cowtown2023/build.gradle)):

```gradle
spotless {
  format 'misc', {
    target '*.gradle', '.gitignore', '*.txt'
    trimTrailingWhitespace()
    indentWithSpace(2)
    }

  java {
    licenseHeader '// Copyright (c) FIRST and other WPILib contributors.\n// Open Source Software; you can modify and/or share it under the terms of\n// the WPILib BSD license file in the root directory of this project.\n\n/*\n * Asimov\'s Laws:\n * The First Law: A robot may not injure a human being or, through inaction, allow a human being to come to harm.\n * The Second Law: A robot must obey the orders given it by human beings except where such orders would conflict with the First Law.\n * The Third Law: A robot must protect its own existence as long as such protection does not conflict with the First or Second Law.\n */'
    removeUnusedImports()
    formatAnnotations()
    googleJavaFormat().reflowLongStrings()
}
}
```

{% hint style="info" %}
IMPORTANT: If you are using git on Windows, _make sure_ that git is set to checkout LF (Unix-style) line endings AND VS Code is set to LF (Unix-style) line endings. Otherwise, Spotless, VS Code, and git will all fight with each other over the line endings and you will be in line-ending purgatory for all eternity.
{% endhint %}

We also use the VS Code plugin for Spotless ([https://marketplace.visualstudio.com/items?itemName=richardwillis.vscode-spotless-gradle](https://marketplace.visualstudio.com/items?itemName=richardwillis.vscode-spotless-gradle)) with the following configuration ([https://github.com/frc937/robot2023/blob/cowtown2023/.vscode/settings.json](https://github.com/frc937/robot2023/blob/cowtown2023/.vscode/settings.json)) for linting and format-on-save:

```json
"[java]": {
  "spotlessGradle.format.enable": true,
  "spotlessGradle.diagnostics.enable": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.spotlessGradle": true 
  }
}
```

### CI/CD (GitHub Actions)

We use GitHub Actions for compile CI/CD. Since tests and formatting checks are handled by Gradle, this will also run those. We use the following workflow file:

{% @github-files/github-code-block url="https://github.com/frc937/robot2023/blob/cowtown2023/.github/workflows/compile.yml" %}

## Workflow Conventions

All of our code is hosted on our GitHub ([https://github.com/frc937](https://github.com/frc937)). All team members should be granted access to this organization on their own individual GitHub accounts, and they should work on code only on those accounts on their own separate devices. (git and GitHub will work on school computers, it just requires some extra legwork).

### Repository

The robot code for each year should be contained in a GitHub repository owned by the frc937 organization called `robot(year)`, where `(year)` is the year of the season the robot is for. For example, our 2024 robot's repository would be called `robot2024`. The WPILib project should share its name with the GitHub repository.

Additional repositories can (of course) be created for additional projects.

Each year's robot code should be initialized with the skeleton command-based framework from WPILib and our Spotless and GitHub Actions configurations (found above).

### Workflow

The general programming workflow should be as follows:

1. Identify necessary features and bugfixes
2. Assign team members to implement those features and bugfixes
3. Team members create topic branches off of main within the frc937/robot(year) repository for each feature/bugfix they implement
4. Team members create a pull request for each feature/bugfix once it is complete
5. At least one reviewer reviews and approves each PR
6. PR is merged into main
7. Rinse and repeat until the robot is ready!

### Reviewers

A team of approved reviewers should be created for the programming team every year. Each PR must be approved by at least one reviewer before it can be merged into main, and reviewers may not approve their own PRs.

Reviewers should generally be experienced programmers, and should specifically be experienced with programming on Team 937. Most (if not all) lead programming specialists will be reviewers, but the team of reviewers is not necessarily limited to lead programming specialists.

If a reviewer is uncertain about a PR, they may defer to another reviewer for a second opinion. If no reviewer is confident about merging a PR and/or giving feedback before a merge, they may defer to a programming mentor.

## Naming Conventions

### Class Names

ALL class names should be in PascalCase

#### Commands

1. Commands should start with an action verb
   1. Example: DriveRobotOriented, ClimbUp, etc.
2. Should of course be descriptive
3. Should be descriptive of the subsystem it works with

#### Subsystems

1. Should be brief and begin with a noun
   1. Example: Drive, Climber, Flywheel, etc.
2. Coordinate with mechanical and electrical to determine a common name for the subsystem
   1. Example: If mechanical is calling a certain wheel the "index wheel," programming should call it that too

#### Other classes

1. Should be descriptive
2. Most of these will be created for you by WPILib. If you have very many classes that are neither commands nor subsystems, you are probably doing something wrong.

### Variable Names

1. All variable names should be in camelCase
2. Should, of course, be descriptive
3. Use `this`
   1. If you have a [formal parameter](https://www.educative.io/answers/what-are-formal-and-actual-parameters-in-java) which sets an [instance variable](https://www.javatpoint.com/instance-variable-in-java) and it makes sense to name them the same thing, use `parameterAndVariableName = this.parameterAndVariableName`
4. Constants
   1. Should be in ALL\_UPPER\_CASE
   2. Constants should all be contained within the constants file, and referenced from that file throughout the project

## Talking About Code

1. When saying the name of something that has "init" in it, you must say it in a British accent (preferably a terrible one).
