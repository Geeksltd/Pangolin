# Pangolin
Pangolin is a browser automated testing framework that enables you to write and run test scripts using simple commands in C#. The automation of Pangolin enables many tests to be executed in a short space of time, allowing faster and more efficient testing while still maintaining reliability and accuracy.

### The Pangolin Language
Although Pangolin code is written in C#, but it's effectively an internal Domain Specific Language.
In other words, when creating a Pangolin test, you will be thinking in terms of Pangolin commands, not a general purpose C# script.

The Pangolin language consists of basic commands that can simulate different user actions in a browser such as clicking buttons and menus, filling out input fields, ticking checkboxes and radio buttons.

## Table of contents
| Topic | Description |
| ------------- |:-------------:|
| [Creating a Pangolin test project](create-project.md) | Learn how to get started by creating your first Pangolin project. |
| [Migrate from Sanity to Pangolin](sanity-migration.md) | Do you have an existing Sanity-based project? Learn how to migrate it. |
| [Running and debugging a test in Visual Studio](running-in-vs.md) | Learn how to run and debug a test case in Visual Studio and how to use Chrome Headless. |
| [Fresh state: Server side compatibility](fresh-slate.md) | Learn how Pangolin creates a fresh server side containers at the beginning of each test. |
| [Commands](commands.md) | See three groups of Pangolin commands, Act, Arrange and Assert commands and how to use them in Pangolin scripts. |
| [Cloud-based parallel execution](cloud-run.md) | Learn how to install server app and run a batch of test cases by Pangolin Test Explorer. |
| [Example: End-to-end test](example.md) | See an example of Pangolin and explanations about server-side functionality. |
