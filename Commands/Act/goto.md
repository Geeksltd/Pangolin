# Goto("url");



The Goto command redirects the current page to another URL within the same domain.This is used when
action commands (Set, Click etc) cause the page to change. This ensures that the page(s) you intended to
navigate to, have been navigated to. In particular that the URL is what you would expect when the page change occurs.
The Goto  command is used by default in login snippets to ensure that you are on the login page when you
attempt to login (instead of relying on buttons in the application).

e.g. see the following code of using Goto command:

```C#
using Pangolin;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestUITests
{
    [TestClass]
    public class Test : UITest
    {
        [TestMethod]
        public override void RunTest()
        {
            LoginAs<Adminuser>();
            
            AssumeDate("06/12/2015");
            AssumeTime("18:30");            
            Goto("/");
            Click("Audit logs");
        }
    }
}

```

By default Goto("/") redirects browser to initialize page which has been set the value of 'AppBaseUrl' from 'app.config'. It can be any valid Url instead of "/" such as "http://localhost" .