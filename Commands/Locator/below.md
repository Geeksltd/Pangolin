# Below("text")



This command searches below the specified text in the command for something on a web page. It should be used with any of the action (Set, Click etc) or find (Above, Near, Below) commands.

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
            LoginAs<Adminuser>();
            Click("Clients");
            WaitForNewPage();
            Below(What.Contains, "Name").ExpectLink(That.Contains, "New Client");
            Below("New Client").ExpectNoButton("Save");
        }
    }
}
```

