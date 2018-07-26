# Set("field").To("value")



The set command defines inputs to be entered into a HTML element on a page. Use this command to fill up
fields on a form such as text fields, checkboxes, radio buttons and drop-down lists.

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
            Set("Email address").To("admin@yahoo.com");
            Set("Password").To("test");
            Click("Login");
        }
    }
}
```

