# AboveButton("text")



This command will find an element above a button labelled with the text matched within quotation marks. This must be combined with other commands that find elements on a page or perform an action such as clicking a button or setting the text of a field.

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
            AboveButton("Login").Expect("Email address");
            Set("Email address").To("admin@gmail.com");
            AboveButton("Login").Set("Password").To("test");
            Above(What.Contains, "Forgot password?").Click("Login");
            WaitForNewPage();
            Expect(What.Contains, "Welcome,");
        }
    }
}
```

