# Press(Keys);



Press command simulates pressing the key on the keyboard to click on an elememt.

You can separate multiple commands with comma:

Press(Keys.ArrowUp, Keys.ArrowUp, Keys.ArrowDown, Keys.ArrowDown, Keys.ArrowLeft, Keys.ArrowRight, Keys.ArrowLeft, Keys.ArrowRight);

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
            Goto("/");            
            Click("Timesheets");
            Click("Submitted");
            Press(Keys.End, Keys.Tab);
            Click("Search");
            WaitToSee(What.Contains, "NHS");
            Set("From").To("05:00");
            Set("To").To("21:00");
            Press(Keys.Tab);
            Press(Keys.Escape);
            AtLabel(That.Contains, "Total paid hours").Expect(What.Contains, "15");
            Click("Amend");
        }
    }
}
```

