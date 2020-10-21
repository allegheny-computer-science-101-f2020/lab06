# cs101f2020-lab06

## DUE: November 5 by 3pm

[![Actions Status](../../workflows/build/badge.svg)](../../actions)

## Table of Contents

- [Objectives](#objectives)

- [Introduction](#introduction)

- [Continuous Learning](#continuous-learning)

- [Program Requirements](#program-requirements)

- [Expected Program Output](#expected-program-output)

- [System Commands](#system-commands)

  - [Using Docker](#using-docker)
  - [Using Gradle](#using-gradle)

- [Automated Checks with GatorGrader](#automated-checks-with-gatorgrader)

- [Using GitHub Actions CI](#using-github-actions-ci)

- [Reporting Problems](#reporting-problems)

- [Receiving Assistance](#receiving-assistance)

- [Lab Assessment](#lab-assessment)

## Introduction

Designed for use with [GitHub Classroom](https://classroom.github.com/) and [GatorGrader](https://github.com/GatorEducator/gatorgrader/), this repository contains the starter files for a laboratory assignment six in a Data Abstraction introductory computer science class that uses the Java programming language. The GitHub Actions CI builds for this repository will pass, as evidenced by a green ✔ instead of a red ✗ appearing in the commit logs.

This assignment requires a programmer to implement and test a benchmarking framework that supports the empirical evaluation of a `PasswordChecker`. More details about the password checking strategy are provided later in this document. You can learn about experimental studies by reading the content in Section 4.1\. Please note that this assignment will also require you to read and uses Java classes that contain a test suite. The programmer is also responsible for learning how to run and extend a test suite written in the JUnit testing framework, as explained in Section 1.9\. As verified by [Checkstyle](https://github.com/checkstyle/checkstyle), the source code for all of the Java source code files must adhere to all of the requirements in the [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html).

The programmer completing this assignment is also responsible for writing a multiple-paragraph reflection, stored in the file `writing/reflection.md`, that explains the challenges that you faced and the solutions you developed. This is a Markdown file that should adhere to the standards described in the [Markdown Syntax Guide](https://guides.github.com/features/mastering-markdown/). Remember, an individual completing this assignment can preview the contents of a comitted Markdown file by clicking on the name of the file in your GitHub repository. Don't forget that your `writing/reflection.md` file should adhere to the Markdown standards established by the [Markdown linting tool](https://github.com/markdownlint/markdownlint).

## Continuous Learning

If you have not done so already, please read all of the relevant [GitHub Guides](https://guides.github.com/) that explain how to use many of the features that GitHub provides. In particular, please make sure that you have read the following GitHub guides: [Mastering Markdown](https://guides.github.com/features/mastering-markdown/), [Hello World](https://guides.github.com/activities/hello-world/), and [Documenting Your Projects on GitHub](https://guides.github.com/features/wikis/). Each of these guides will help you to understand how to use both [GitHub](http://github.com) and [GitHub Classroom](https://classroom.github.com/).

Students who want to learn more about how to use [Docker](https://www.docker.com) should review the [Docker Documentation](https://docs.docker.com/). Students are also encouraged to review the documentation for their text editor, which is available for text editors like [Atom](https://atom.io/docs) and [VS Code](https://code.visualstudio.com/docs). You should also review the [Git documentation](https://git-scm.com/doc) to learn more about how to use the Git command-line client. In addition to talking with the instructor and technical leader for your course, students are encouraged to search [StackOverflow](https://stackoverflow.com/) for answers to their technical questions.

To do well on this assignment, you should also read Sections 4.1 through 4.3, focusing on Code Fragment 4.1 and the text that discusses Figure 4.1\. Please see the course instructor or one of the student technical leaders if you have questions about any of these reading assignments.

## Program Requirements

There are many "TODO" markers inside of the provided source code. Ultimately, it is your responsibility to read each of these and provide the required source code. With that said, the remainder of this section will provide some pointers to help you to implement the needed code. First, you should know that you must implement a `PasswordChecker` class and experimentally evaluate it through a doubling experiment. The `PasswordChecker` must enforce the rule that the input password must contain at least one of the following: a digit, an uppercase letter, a lowercase letter, and a special symbol (i.e.,@,#,$, or%). The password must contain at least six characters. Once you have finished implementing the `PasswordChecker` you should also resolve all of the "TODO" markers in the `RunCampaign` and `Experiment` classes, ensuring that all of the provided tests pass. Please note that there are many different ways to implement the `PasswordChecker` in Java; you should use your creativity and expertise to implement a tool that is as efficient as is possible.

Your textbook contains several useful insights into the pattern that you should follow when thinking about the running time of the `PasswordChecker` that you implement. For instance, when describing the results from running an experiment, page 153 notes that "[A]s the value of `n` is doubled, the running time of `repeat1` typically increases more than fourfold." What does this suggest about the likely "worst-case time complexity" of `repeat1`? How can you apply this intuition to analyze the results that you collect when running an experiment? How can you apply what you learned in prior experiments to this assignment's experiments? Overall, what do the timing results and the order-of-growth ratios tell you about the worst-case time complexity of your `PasswordChecker` when it checks either valid or invalid passwords? How do you know?

You should write your reflections in a file, called `writing/reflection.md`, that uses the Markdown language. To complete this part of the assignment, you should write one paragraph that reports on your experiences. Your `writing/reflection.md` file should also have answers to the questions about `Experiment`'s implementation, testing, and output data tables. In summary, make sure that you can provide detailed responses to questions like these:

1. What was your strategy for automatically checking whether a password was valid or not?
2. What did your doubling experiment reveal about the overall performance of your checker?
3. Using the big-Oh notation, what is the likely worst-case time complexity of your checker?

## Expected Program Output

Typing the command `gradle run` in the terminal window should produce the following output for the completed version of `Experiment`. As long as your program adheres to all of the requirements for the assignment and passes all of the verification checks, your version should produce similar output. With that said, program output may vary according to, for instance, the name of the programmer and the date on which you ran the program.

```bash
> Configure project :
Configured GatorGradle 0.4.4

> Task :run
Starting a campaign of experiments with valid passwords ...
  Running round 0 with input size 250
  Running round 1 with input size 500
  Running round 2 with input size 1000
  Running round 3 with input size 2000
  Running round 4 with input size 4000
  Running round 5 with input size 8000
  Running round 6 with input size 16000
  Running round 7 with input size 32000
  Running round 8 with input size 64000
  Running round 9 with input size 128000
... Finishing a campaign of experiments with the password checker ...

Results of an experiment campaign with valid passwords:

Size (#)        Timing (ms)     Ratio (#)
250             2               0
500             1               1
1000            1               1
2000            2               2
4000            3               2
8000            2               1
16000           5               3
32000           4               1
64000           4               1
128000          5               1

Starting a campaign of experiments with valid passwords ...
  Running round 0 with input size 250
  Running round 1 with input size 500
  Running round 2 with input size 1000
  Running round 3 with input size 2000
  Running round 4 with input size 4000
  Running round 5 with input size 8000
  Running round 6 with input size 16000
  Running round 7 with input size 32000
  Running round 8 with input size 64000
  Running round 9 with input size 128000
... Finishing a campaign of experiments with the password checker ...

Results of an experiment campaign with invalid passwords:

Size (#)        Timing (ms)     Ratio (#)
250             2               0
500             1               1
1000            1               1
2000            2               2
4000            3               2
8000            2               1
16000           5               3
32000           4               1
64000           4               1
128000          5               1

BUILD SUCCESSFUL in 1s
2 actionable tasks: 2 executed
```

## System Commands

This project invites students to enter system commands into a terminal window. This assignment uses [Docker](https://www.docker.com) to deliver programs, such as `gradle` and the source code and packages needed to run [GatorGrader](https://github.com/GatorEducator/gatorgrader), to a students' computer, thereby eliminating the need for a programmer to install them on their development workstation.

### Using Docker

Once you have installed [Docker Desktop](https://www.docker.com/products/docker-desktop), you can use the following `docker run` command to start `gradle grade` as a containerized application, using the [DockaGator](https://github.com/GatorEducator/dockagator) Docker image available on [DockerHub](https://cloud.docker.com/u/gatoreducator/repository/docker/gatoreducator/dockagator).

```bash
docker run --rm --name dockagator \
  -v "$(pwd)":/project \
  -v "$HOME/.dockagator":/root/.local/share \
  gatoreducator/dockagator
```

The aforementioned command will use `"$(pwd)"` (i.e., the current directory) as the project directory and `"$HOME/.dockagator"` as the cached GatorGrader directory. Please note that both of these directories must exist, although only the project directory must contain something. Generally, the project directory should contain the source code and technical writing of this assignment, as provided to a student through GitHub. Additionally, the cache directory should not contain anything other than directories and programs created by DockaGator, thus ensuring that they are not otherwise overwritten during the completion of the assignment. To ensure that the previous command will work correctly, you should create the cache directory by running the command `mkdir $HOME/.dockagator`.

If you are running your program on a Windows Operating System, you should run the following command instead, replacing the word "user" with the username of your machine:

```bash
docker run --rm --name dockagator -v "%cd%":/project -v "C:\Users\user/.dockagator":/root/.local/share gatoreducator/dockagator
```

Here are some additional commands that you may need to run when using Docker:

- `docker info`: display information about how Docker runs on your workstation
- `docker images`: show the Docker images installed on your workstation
- `docker container list`: list the active images running on your workstation
- `docker system prune`: remove many types of "dangling" components from your workstation
- `docker image prune`: remove all "dangling" docker images from your workstation
- `docker container prune`: remove all stopped docker containers from your workstation
- `docker rmi $(docker images -q) --force`: remove all docker images from your workstation

### Using Gradle

Since the above `docker run` command uses a Docker image that, by default, runs `gradle grade` and then exits the Docker container, you may want to instead run the following command so that you enter an "interactive terminal" that will allow you to repeatedly run commands within the Docker container.

In Linux and Mac OS:

```bash
docker run -it --rm --name dockagator \
  -v "$(pwd)":/project \
  -v "$HOME/.dockagator":/root/.local/share \
  gatoreducator/dockagator /bin/bash
```

In Windows OS (replace `user` with your machine's username):

```bash
docker run -it --rm --name dockagator -v "%cd%":/project -v "C:\Users\user/.dockagator":/root/.local/share gatoreducator/dockagator /bin/bash
```

Once you have typed this command, you can use the [GatorGrader tool](https://github.com/GatorEducator/gatorgrader) in the Docker container by typing the command `gradle grade` in your terminal. Running this command will produce a lot of output that you should carefully inspect. If GatorGrader's output shows that there are no mistakes in the assignment, then your source code and writing are passing all of the automated baseline checks. However, if the output indicates that there are mistakes, then you will need to understand what they are and then try to fix them.

You can also complete several important Java programming tasks by using the `gradle` tool. For instance, you can compile (i.e., create bytecode from the program's source code if it is correct) the program using the command `gradle build`. Here are some other commands that you can type:

- `gradle grade`: run the [GatorGrader](https://github.com/GatorEducator/gatorgrader) tool to check your work
- `gradle clean`: clean the project of all the derived files
- `gradle check`: check the quality of the code using Checkstyle
- `gradle build`: create the bytecode from the Java source code
- `gradle run`: run the Java program in the command-line
- `gradle cleanTest`: clean the JUnit test suite of derived files
- `gradle test`: run the JUnit test suite and display the results
- `gradle tasks`: display details about the Gradle system

To run one of these commands, you must be in the main (i.e., "home base") directory for this assignment where the `build.gradle` file is located.

## Automated Checks with GatorGrader

In addition to meeting all of the requirements outlined in the assignment sheet, your submission must pass the following checks that [GatorGrader](https://github.com/GatorEducator/gatorgrader) automatically assesses:

- The RunCampaign.java in src/main/java/labsix/experiment has at least 1 of the `public String generateValidRandomPassword(` fragment
- The PasswordChecker.java in src/main/java/labsix/checker has at least 6 multiple-line Java comment(s)
- The ResultsTable.java in src/main/java/labsix/data has exactly 1 of the `double ratio =` fragment
- The repository has at least 10 commit(s)
- The TestPasswordChecker.java in src/test/java/labsix has exactly 1 of the `package labsix` fragment
- The PasswordChecker.java in src/main/java/labsix/checker has exactly 1 of the `package labsix` fragment
- The TestResultsTable.java in src/test/java/labsix has exactly 0 of the `Add Your Name Here` fragment
- The Experiment.java in src/main/java/labsix/experiment has at least 7 of the `println(` fragment
- The PasswordChecker.java in src/main/java/labsix/checker has exactly 1 of the `public boolean check(` fragment
- The RunCampaign.java in src/main/java/labsix/experiment has exactly 0 of the `TODO` fragment
- The TestRunCampaign.java in src/test/java/labsix has exactly 0 of the `Add Your Name Here` fragment
- The ResultsTable.java in src/main/java/labsix/data has exactly 1 of the `package labsix` fragment
- The RunCampaign.java in src/main/java/labsix/experiment has at least 3 of the `println(` fragment
- The TestResultsTable.java in src/test/java/labsix has exactly 1 of the `package labsix` fragment
- The reflection.md in writing has exactly 0 of the `Add Your Name Here` fragment
- The Campaign.java in src/main/java/labsix/experiment has exactly 1 of the `package labsix` fragment
- The file Campaign.java exists in the src/main/java/labsix/experiment directory
- The Campaign.java in src/main/java/labsix/experiment has exactly 0 of the `TODO` fragment
- The file RunCampaign.java exists in the src/main/java/labsix/experiment directory
- The PasswordChecker.java in src/main/java/labsix/checker has exactly 0 of the `TODO` fragment
- The reflection.md in writing has at least 8 paragraph(s)
- The RunCampaign.java in src/main/java/labsix/experiment has at least 7 multiple-line Java comment(s)
- The TestPasswordChecker.java in src/test/java/labsix has exactly 0 of the `Add Your Name Here` fragment
- The RunCampaign.java in src/main/java/labsix/experiment has at least 1 of the `public String generateInvalidRandomPassword(` fragment
- The file reflection.md exists in the writing directory
- The RunCampaign.java in src/main/java/labsix/experiment has exactly 0 of the `Add Your Name Here` fragment
- The RunCampaign.java in src/main/java/labsix/experiment has at least 1 single-line Java comment(s)
- The Experiment.java in src/main/java/labsix/experiment has at least 2 multiple-line Java comment(s)
- The Experiment.java in src/main/java/labsix/experiment has at least 2 single-line Java comment(s)
- The file PasswordChecker.java exists in the src/main/java/labsix/checker directory
- The file ResultsTable.java exists in the src/main/java/labsix/data directory
- The file TestPasswordChecker.java exists in the src/test/java/labsix directory
- The Experiment.java in src/main/java/labsix/experiment has exactly 0 of the `TODO` fragment
- The ResultsTable.java in src/main/java/labsix/data has exactly 0 of the `TODO` fragment
- The PasswordChecker.java in src/main/java/labsix/checker has exactly 0 of the `println(` fragment
- The RunCampaign.java in src/main/java/labsix/experiment has exactly 1 of the `package labsix` fragment
- The TestPasswordChecker.java in src/test/java/labsix has exactly 0 of the `TODO` fragment
- The TestResultsTable.java in src/test/java/labsix has exactly 0 of the `TODO` fragment
- The reflection.md in writing has at least 11 of the `heading` tag
- The Campaign.java in src/main/java/labsix/experiment has exactly 0 of the `Add Your Name Here` fragment
- The file TestResultsTable.java exists in the src/test/java/labsix directory
- The PasswordChecker.java in src/main/java/labsix/checker has exactly 0 of the `Add Your Name Here` fragment
- The ResultsTable.java in src/main/java/labsix/data has at least 2 single-line Java comment(s)
- The Campaign.java in src/main/java/labsix/experiment has exactly 0 of the `println` fragment
- The ResultsTable.java in src/main/java/labsix/data has at least 12 multiple-line Java comment(s)
- The ResultsTable.java in src/main/java/labsix/data has exactly 0 of the `println` fragment
- The Experiment.java in src/main/java/labsix/experiment has exactly 1 of the `package labsix` fragment
- The file TestRunCampaign.java exists in the src/test/java/labsix directory
- The ResultsTable.java in src/main/java/labsix/data has exactly 0 of the `Add Your Name Here` fragment
- The Experiment.java in src/main/java/labsix/experiment has exactly 0 of the `Add Your Name Here` fragment
- The file Experiment.java exists in the src/main/java/labsix/experiment directory
- The PasswordChecker.java in src/main/java/labsix/checker has at least 1 single-line Java comment(s)
- The TestRunCampaign.java in src/test/java/labsix has exactly 0 of the `TODO` fragment
- The reflection.md in writing has at least 700 word(s) in total
- The TestRunCampaign.java in src/test/java/labsix has exactly 1 of the `package labsix` fragment
- The command `gradle build` executes correctly
- The command `gradle test` executes correctly
- The command `gradle -q --console plain run` executes correctly

If [GatorGrader's](https://github.com/GatorEducator/gatorgrader) automated checks pass correctly, the tool will produce the output like the following in addition to returning a zero exit code (which you can access by typing the command `echo $?`).

```bash
        ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
        ┃ Passed 58/58 (100%) of checks for cs101f2020-lab06! ┃
        ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛
```

## Using GitHub Actions CI

This assignment uses [GitHub Actions CI](https://github.com/features/actions) to automatically run [GatorGrader](https://github.com/GatorEducator/gatorgrader) and additional checking programs every time you commit to your GitHub repository. The checking will start as soon as you have accepted the assignment -- thus creating your own private repository. If you do not see either a yellow ● or a green ✔ or a red ✗ in your listing of commits, then please contact the instructor.

## Reporting Problems

If you have found a problem with this assignment's provided source code or documentation, then you can go to the [Computer Science 101 Fall 2020 Lab 06](https://github.com/allegheny-computer-science-101-f2020/lab06) repository and [raise an issue](https://github.com/allegheny-computer-science-101-f2020/lab06/issues). If you have found a problem with the [GatorGrader tool](https://github.com/GatorEducator/gatorgrader) and the way that it checks your assignment, then you can also [raise an issue](https://github.com/GatorEducator/gatorgrader/issues) in that repository. To ensure that your issue is properly resolved, please provide as many details as is possible about the problem that you experienced. If you discover a problem with the assignment sheet for this project, then please raise an issue in the GitHub repository that provides the assignment sheets for your course.

Whenever possible, individuals who find, and use the appropriate GitHub issue tracker to correctly document, a mistake in any aspect of this assignment will receive free [GitHub stickers](https://octodex.github.com/) and extra credit towards their grade for the project.

## Receiving Assistance

If you are having trouble completing any part of this project, then please talk with either the course instructor or a student technical leader during the lab session. Alternatively, you may ask questions in the Slack workspace for this course. Finally, you can schedule a meeting during the course instructor's office hours.

## Lab Assessment

The grade that a student receives on this assignment will have the following components:

- **Percentage of Correct GatorGrader Checks [up to 70% of the lab grade]**: Students are encouraged to repeatedly try to implement a Java program that passes all of GatorGrader's checks by, for instance, creating a program that produces the correct output. Students should also repeatedly revise their technical writing to ensure that it also passes all of GatorGrader's checks about, for instance, the length of its content and its appropriate use of Markdown.

- **GitHub Actions CI Build Status [up to 10% of the lab grade]**: Since additional checks on the source code and/or technical writing may be encoded in GitHub Actions CI's actions and, moreover, all of the GatorGrader checks are also run in GitHub Actions CI, students will receive a checkmark grade if their last before-the-deadline build passes and a green ✔ appears in their GitHub commit log instead of a red ✗. As with the previous grading component, students are encouraged to repeatedly revise their source code and technical writing in an attempt to get their GitHub Actions CI build to pass.

- **Mastery of Technical Writing [up to 10% of the lab grade]**: Students will also receive a portion of their grade when the responses to the technical writing questions presented in the `writing/reflection.md` reveal a mastery of both writing skills and technical knowledge. To receive a checkmark grade, the submitted writing should have correct spelling, grammar, and punctuation in addition to following the rules of Markdown and providing technically accurate answers. Students are encouraged to ask the course instructor or a student technical leader to use the GitHub issue tracker to provide feedback on their mastery of technical writing skills. All members of the team are expected to contribute to the reflection document.

- **Mastery of Technical Knowledge and Skills [up to 10% of the lab grade]**: Students will receive a part of their grade when their GitHub repository reveals that they have mastered all of the technical knowledge and skills developed during the completion of this project. As a part of this grade, the instructor will assess aspects of the project including, but not limited to, the use of effective source code comments and Git commit messages. Students are encouraged to ask the course instructor or a student technical leader to use the GitHub issue tracker to provide feedback on how well their work demonstrates mastery of the assignment's technical knowledge and skills. All members of the team are expected to contribute to the technical implementation of the lab.

All grades for the assignments in this course will be reported through Canvas. Feedback on lab assignments will be provided through a student's GitHub repository using the comment in the "Feedback" pull request.
