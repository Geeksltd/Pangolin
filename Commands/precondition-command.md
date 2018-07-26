# Pangolin commands precondition



Most of Pangolin commands have overloaded methods and different type of arguments with default values. 

For instance ClickButton command has the following overloaded methods:

```C#
ClickButton(The the, That that, string locator = null, Casing casing = Casing.Ignore)
ClickButton(The the, string locator = null, Casing casing = Casing.Ignore)
ClickButton(That that, string locator = null, Casing casing = Casing.Ignore)
ClickButton(string locator = null, Casing casing = Casing.Ignore)
```

Most of commands have the same overloaded methods with the same arguments. 



'locator' is name of element to search for, default value is null and it means search for all elements on the page or an area. It's useful if you expected there is only one element inside an area or on the page. For example 

```C#
AtRow(That.Contains, "Clients").ClickField();
```

If there is one field (e.g.  checkbox, textbox, radiobutton, etc) inside table row "Clients", it's not necessary to set its name.



The first argument is "The", it is an enum value includes:

```C#
public enum The
{
    Top,
    Bottom,
    Right,
    Left
}
```

If more than one element with the same name exist on the page, it's possible to search for specific element by its position. 'Top' value finds the topmost, 'Bottom' searches for lowest and 'Right' and 'Left' values detect rightmost and leftmost element on the page.



Next argument is enum 'That' or 'What', each of them has the same values. General methods get 'What' as argument such as 'Click', 'Expect' and others get 'That' such as Click[object] (object is Button, Header, etc). 

```C#
public enum That
{
    Equals,
    Contains,
    Wildcard
}
```

It's clear when passing 'That' with 'Equals' value, Pangolin looks for an element which has the same 'locator' name. 'Contains' gets any element which contains the name. 'Wildcard' can be used when you expected a format number text (e.g: {digit}{digit}{letter}-{digit}).



The last argument is 'Casing' which has the below values:

```C#
public enum Casing
{
    Ignore,
    Exact
}

```

It can be combined with 'That', means looking for case sensitive element. Default value is Casing.Ignore. For example:

```C#
AtLabel("Candidate", Casing.Exact).Click(What.Contains, "Paul Candidate");
```

First searches for element that exactly has the same name 'Candidate', then 'Click' on element which has any type of name 'Paul Candidate'.