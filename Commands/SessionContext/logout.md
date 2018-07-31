# Logout();



The Logout command does not log users out of an application as the name may suggest. In fact, the logout
command actually clears certain cookies from the browser’s memory. For the curious, these are:

- ASPXAUTH
- AspNet.ApplicationCookie

e.g.

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
            Logout();
            AssumeDate("01/07/2017");
            Goto("/");
            Set("Email address").To("admin@gmail.com");
            Set("Password").To("test");
            Click("Login");
            Expect("admin");
        }
    }
}
```

