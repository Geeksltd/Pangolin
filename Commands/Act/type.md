# Type("text");



Pangolin 'Set' command automatically presses a tab at the end.

For cases where you don't want the automatic tab to happen (for example when you are testing an
autocomplete and you just want to type the first few letters) there is now a 'type' command.

e.g.

```C#
using Pangolin;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestUITests
{
    [TestClass]
    public class Adminuser : UITest
    {
        [TestMethod]
        public override void RunTest()
        {
            Logout();            
            AssumeDate("01/07/2015");
            AssumeTime("12:00");
            Goto("/");
            ClickField("Email address");
            Type("admin@yahoo.com");
            Press(Keys.Tab);
            ClickField("Password");
            Type("test");
            Click("Login");
        }
    }
}
```

