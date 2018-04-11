# Pangolin
The Pangolin UI testing framework.

Pangolin is a browser automated testing framework that enables you to write and run test scripts using simple commands in C#. The automation of Pangolin enables many tests to be executed in a short space of time, allowing faster and more efficient testing while still maintaining reliability and accuracy.

## The Pangolin Language
Although Pangolin code is written in C#, but it's effectively an internal Domain Specific Language.
In other words, when creating a Pangolin test, you will be thinking in terms of Pangolin commands, not a general purpose C# script.

The Pangolin language consists of basic commands that can simulate different user actions in a browser such as clicking buttons and menus, filling out input fields, ticking checkboxes and radio buttons.

## Getting started with Pangolin
To create your first Pangolin test, follow these steps:
1. In a Visual Studio solution, add a new project called *Tests* with the template of *Unit Test Project*
2. Add a NuGet reference to ...
3. .... (TODO: Complete)

## Fresh state: Server side compatibility
Running a test will often change the state (database, files, cookies, etc).
On the other hand, every time that you run any test, it should execute against a known and predictable state.

### With Docker/Containers
If you use Containers such as Docker, at the beginning of each test you should create a fresh container.
After a test is executed, you discard its container (which has dirty state). And the next test will again run in a fresh container, that is made from the source image. The source image will always have a known and predictable state.

### Without Docker/containers
If you don't use containers, and instead run the web application natively on Windows, then you need to provide Pangolin with a mechanism to reset the application to a known state.

1. Your application database should be avilable as SQL scripts in a folder that the application run-time can access.
2. Upon start-up, your application should create its database from the script files.
3. You should provide a way for Pangolin to explicitly ask your application to discard the current dirty database and start a fresh one from the script files again. To achieve this, Pangolin will send the following HTTP request to your application at the beginning of running each new test:
> http://localhost:1234/?Web.Test.Command=restart

This is already supported in the M# and Olive frameworks. If you use any other framework, you need to add a http handler that responds to that command and does the following:
- Recreate the database
- If you use files, clean up and recreate from a read-only source
- Clear browser cookies
- Clear database cache and any other application cache
- Clear any other state you might be using in your application.


## Pangolin Commands

### Action commands
| Command | Description | Example  |
| ------------- |:-------------:| -----:|
| `Click("{identifier}");` | Performs the click action on a click-able html element such as a button or link or input | `Click("Save");`
| ... | ... | ...|

### Assert commands
...

### Session context commands
...

## Locators
This is a very important concept, and a key differentiator of Pangolin from other UI testing tools. On web pages, there can be multiple elements all corresponding to the same label or textual representation. For example you might have multiple buttons named "Save" on the same page, for different forms. To disambiguiate your purpose, in most UI testing frameworks, you have to use exact CSS selectors or hard-code element IDs and Names. That makes your test code fragile and brittle, as every time that a small implementation detail is changed, your test will break.

But in Pangolin,...
| Locator | Description | Example  |
| ------------- |:-------------:| -----:|
| ... | ... | ...|


## Inter-dependencies and test reuse
...

## Cloud-based parallel execution
... explain the philosophy... and move the installation guides from the Google Docs to here

## Example: End-to-end test
(TODO: Add a full but simple Pangolin test script here)


TODO: Create a document to explain what server-side functionality is expected. Basically here we should identify every assumption we have made about M# applications, which will not neceessarily be true for non-M# apps.
