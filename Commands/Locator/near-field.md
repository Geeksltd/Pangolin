# NearField("text")



This command finds any element below a HTML field with text matched within quotation marks. This must be used with any arrange command to specify where an element resides on a page or with an action command to act on an element in the page.

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
            Run<AdminUser>();
            Click("Log out");
            Set("Email address").To("admin@gmail.com");
            NearField("Email address").Expect("Password");
            Set("Password").To("test");
            Click("Login");
        }
    }
}
```

