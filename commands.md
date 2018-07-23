## Pangolin Commands

TODO: Copy from https://sanityhub.com/syntax. Make the description here very short.
Then create an MD file for each command and explain it fully with examples, and different tips and tricks, etc.
(Basir, Use the related sections from "QA docs.pdf". I will then get someone to proof read them and edit them. You can then check their changes to learn from and improve your English writing skills.)

### Action commands

| Command |  Example | Description
| ------------- |:-------------:|:-------:|
| [Click](commands\Click.md) | `Click("Save");` | Performs the click action on a click-able html element such as a button or link or input 
| ... | ... | ...

### Assert commands

...

### Session context commands

...

## Locators

This is a very important concept, and a key differentiator of Pangolin from other UI testing tools. On web pages, there can be multiple elements all corresponding to the same label or textual representation. For example you might have multiple buttons named "Save" on the same page, for different forms. To disambiguiate your purpose, in most UI testing frameworks, you have to use exact CSS selectors or hard-code element IDs and Names. That makes your test code fragile and brittle, as every time that a small implementation detail is changed, your test will break.

But in Pangolin,...

| Locator | Description | Example |
| ------- | :---------: | ------: |
| ...     |     ...     |     ... |

## Inter-dependencies and test reuse

...