#Type("text");



Pangolin 'Set' command automatically presses a tab at the end.

For cases where you don't want the automatic tab to happen (for example when you are testing an
autocomplete and you just want to type the first few letters) there is now a 'type' command.
For example:

ClickField("Country");

Type("great br");