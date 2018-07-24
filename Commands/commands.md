## Pangolin Commands

There are three groups of commands in Pangolin: those that act on an element, those that arrange your position on a page and those that assert or expect an outcome.

Arrange commands include the following:

- Above
- Near
- Below
- At row

Act commands include:

- click
- set

Assert commands include:

- expect
- expect botton
- expect field
- expect header
- expect row

### Action commands

| Command                                             | Example                        | Description                                                  |
| --------------------------------------------------- | ------------------------------ | ------------------------------------------------------------ |
| [Set](Act/set.md)                                   | Set("Password").To("test");    | The set command defines inputs to be entered into a HTML element on a page. |
| [Click](Act/click.md)                               | Click("Save");                 | Performs the click action on a click-able html element such as a button or link or input |
| [CheckMailBox](Act/checkmailbox.md)                 | CheckMailBox("email address"); | The CheckMailbox command accesses the email queue items in an application. |
| [Goto](Act/goto.md)                                 | Goto("/");                     | The Goto command redirects the current page to another URL within the same domain. |
| [CheckBackgroundTasks](Act/checkbackgroundtasks.md) | CheckBackgroundTasks();        | Redirect the current page to the page with the list of all Automated Tasks implemented in the application |
| [RefreshPage](Act/refreshpage.md)                   | RefreshPage();                 | The RefreshPage command refreshes the current page.          |
| [Press](Act/press.md)                               | Press(Keys.Escape);            | Simulates pressing the key on the keyboard to click on an elememt. |
| [Type](Act/type.md)                                 | Type("text");                  | Set a text to current focused element.                       |
| [WaitForPopup](Act/waitforpopup.md)                 | WaitForPopup();                | The execution of the next command is delayed until the pop up has loaded. |
| [WaitForNewPage](Act/waitfornewpage.md)             | WaitForNewPage();              | The execution of the next command is delayed until the new page has loaded. |



### Assert commands

| Topic                                        | Example                 | Description                                                  |
| -------------------------------------------- | ----------------------- | ------------------------------------------------------------ |
| [Expect](Assert/expect.md)                   | Expect("text");         | Searches the current page or pop-up window for the text matched within quotation marks. |
| [ExpectNo](Assert/expect-no.md)              | ExpectNo("text");       | Searches the current page to ensure the text matched in quotation marks is not found |
| [ExpectHeader](Assert/expect-header.md)      | ExpectHeader("text");   | This command searches the current page for an HTML header with the text matched in quotation marks on it. |
| [ExpectNoHeader](Assert/expect-no-header.md) | ExpectNoHeader("text"); | This command searches the current page in focus to ensure that a HTML header with the text matched in quotation marks is not found. |
| [ExpectButton](Assert/expect-button.md)      | ExpectButton("text");   | This command searches the current page for an HTML button with the text matched in quotation marks on it. |
| [ExpectNoButton](Assert/expect-no-button.md) | ExpectNoButton("text"); | This command searches the current page to ensure no HTML buttons are found with the text matched in quotation marks on them. |
| [ExpectField](Assert/expect-field.md)        | ExpectField("text");    | This command searches the current page for an HTML field with the text matched in quotation marks on it. |
| [ExpectNoField](Assert/expect-no-field.md)   | ExpectNoField("text");  | This command searches the current page in focus to ensure that a HTML field with the text matchedin quotation marks is not found. |
| [ExpectRow](Assert/expect-row.md)            | ExpectRow("text");      | This command searches the current page for a row in a list (or table) with the text matched in quotation marks in it. |
| [ExpectNoRow](Assert/expect-no-row.md)       | ExpectNoRow("text");    | This command searches the current page in focus to ensure a HTML table row with the text matched in quotation marks is not found. |
| [ExpectUrl](Assert/expect-url.md)            | ExpectUrl("url");       | This command confirms that the URL specified in quotation marks is the current page that Pangolin has in focus. |



### Session context commands

| Topic                                       | Example                   | Description                                                  |
| ------------------------------------------- | ------------------------- | ------------------------------------------------------------ |
| [`Run<T>`](SessionContext/run-test.md)      | `Run<Test>();`            | This command enables testers to run one test within the same project on Dashboard within another. |
| [`LoginAs<T>`](SessionContext/login-as.md)  | `LoginAs<User>();`        | Is actually a shortcut to a bunch of Pangolin code defined in the Users feature. |
| [AssumeDate](SessionContext/assume-date.md) | AssumeDate("01/01/2018"); | This command forces the application to assume a specified date. |
| [AssumeTime](SessionContext/assume-time.md) | AssumeTime("12:00");      | This command forces applications to assume a specified time. |
| [Logout](SessionContext/logout.md)          | Logout();                 | The Logout command clears certain cookies from the browser’s memory. |



## Locators

This is a very important concept, and a key differentiator of Pangolin from other UI testing tools. On web pages, there can be multiple elements all corresponding to the same label or textual representation. For example you might have multiple buttons named "Save" on the same page, for different forms. To disambiguiate your purpose, in most UI testing frameworks, you have to use exact CSS selectors or hard-code element IDs and Names. That makes your test code fragile and brittle, as every time that a small implementation detail is changed, your test will break.

But in Pangolin

| Locator                                | Example             | Description                                                  |
| -------------------------------------- | :------------------ | :----------------------------------------------------------- |
| [AtRow](Locator/at-row.md)             | AtRow("text")       | This command searches anywhere in the row for the text matched within the quotation marks. |
| [Above](Locator/above.md)              | Above("text")       | The Above command will find page elements above the text matched in quotation marks. |
| [AboveButton](Locator/above-button.md) | AboveButton("text") | This command will find an element above a button labelled with the text matched within quotation marks. |
| [AboveField](Locator/above-field.md)   | AboveField("text")  | The AboveField command finds an element above a field labelled with text matched within quotation marks. |
| [AboveHeader](Locator/above-header.md) | AboveHeader("text") | The AboveHeader command finds an element above an HTML header with text matched within quotation marks. |
| [Below](Locator/below.md)              | Below("text")       | This command searches below the specified text in the command for something on a web page. |
| [BelowButton](Locator/below-button.md) | BelowButton("text") | This command searches below a HTML button with the text matched within quotation marks. |
| [BelowField](Locator/below-field.md)   | BelowField("text")  | This command searches below a HTML field with text matched within quotation marks. |
| [BelowHeader](Locator/below-header.md) | BelowHeader("text") | This command searches below a HTML header with text matched within quotation marks. |
| [Near](Locator/near.md)                | Near("text")        | The Near command identifies an HTML element below text matched within quotation marks. |
| [NearButton](Locator/near-button.md)   | NearButton("text")  | This command tells Sanity to find any element below a HTML button with the text matched within quotation marks. |
| [NearField](Locator/near-field.md)     | NearField("text")   | This command finds any element below a HTML field with text matched within quotation marks. |
| [NearHeader](Locator/near-header.md)   | NearHeader("text")  | This command finds a HTML header with text matched within quotation marks. |

