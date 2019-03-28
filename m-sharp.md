# Plain Selenium with M# generated 'page model'

We are looking at a new architecture for UI Testing based on the following principals:

- Using Selenium API more closely
- Use strong typing and compile-time checking where possible, by generating page models using M#
- Benefit from Visual Studio intellisense for more productive test development

## New Development model
Tests written in this model will use a slighly different syntax.
Each section of the code will first select an `M# module` as its context in a `using` block to gain access to pre-generated UI object pointers which are properties that have a built-in 

```csharp
public class LoginTest : PangolinTest
{
    public void Run()
    {
        using (var form = Module<LoginForm>())
        {
            form.Username.SendKeys("jack@smith.com");
            form.Password.SendLeys("Test123");
            form.LoginButton.Click();
        }
    }
}
```

## PageModel.cs file

A single big file will be generated by M# to provide strongly typed UI element accessors.

```csharp
public partial class LoginForm : PangolinModule
{
    LoginForm(IWebDriver driver) : base (driver) { }
    
    public HtmlElement Username => driver.FindElement(By.XPath("[data-module='LoginForm'] [name='Username']");
    public HtmlElement Password => driver.FindElement(By.XPath("[data-module='LoginForm'] [name='Password']");
    
    public HtmlElement LoginButton => driver.FindElement(By.XPath("[data-module='LoginForm'] input[type=submit][name='Login']");
}
...
```

Test developers can add their own partial classes to these M# generated `PageModel` definitions for custom elements.

For all routine scenarios, M# can generate such properties to simplify access and resolve ambiguities, so that `location specifiers` such as `below`, `under`, etc are not needed any more. For example for a list page we can have something like:


```csharp
public class EditCustomer : PangolinTest
{
    public void Run()
    {
        using (var list = Module<CustomersList>())
        {
            list.Search.FirstName.SendKeys("Jack");
            list.SearchButton.Click();
            list.Columns.Name.AtRow("Jack smith").Click();
        }
    }
}
```


# SpecFlow vs Pangolin/Sanity
[Learn about Specflow here.](https://specflow.org/getting-started/)
It's a framework and tool for implementing BDD (Behaviour Driven Development) using `Cucumber` in .NET.

Specflow (and Cucumber in general) says that the `high level definition` of a test is different from the `code` that implements and runs that test. But the `high level specifications` of the behaviour of the application should be properly mapped to the code that run them.

The Pangolin (and Sanity) philosophy has been that the `test execution code` should be so simple and readable, that it can be used as the `test specification`. It argued that `any form of documentation` is worse than a `self documenting code` that is as concise and clean as English. And eliminating such a step would lead to productivity and avoids inconcistency (between code and documentation). The Sanity philosophy was that the `Sanity code` is simple and clean enough that it can be used as a `communication tool` between the technical and non technical people, including the clients.

With the Sanity conversion to Pangolin, the original simplicity of the language syntax was reduced, with the syntax noise from C# being added. It was arguably no longer pure enough to be usable as a communication tool. If that original vision cannot be fulfilled, then we might as well abandon that dream, and reintroduce separated documentation from code and think of our Pangolin code as a technical artefact only. This is where Specflow comes handy.

Specflow can be integrated with any Selenium based test automation, including Pangolin code (old and new).