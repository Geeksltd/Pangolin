# NearButton("text")



This command tells Pangolin to find any element below a HTML button with the text matched within quotation marks. This needs to be used with another arrange command (e.g. Below or Above) or with an action command (e.g. Set or Click) to perform an action on the newly found element.

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
            Click("Agencies");
            Click("New Agency");
            ExpectHeader("Agency Details");
            NearButton("Save").Expect("Cancel");
            Click("Cancel");
        }
    }
}
```

