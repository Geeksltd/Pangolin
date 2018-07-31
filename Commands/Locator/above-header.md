# AboveHeader("text")



The AboveHeader command finds an element above an HTML header with text matched within quotation
marks. You will need to combine this command with another arrange (Above, Near, Below etc) and/or an action command (Set, Click etc).

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
            Click("Candidates");
            AboveHeader(That.Contains, "Candidate Details").Click("Search");
            AboveHeader("Candidate Details").Expect("New Client");
            Click(What.Contains, "New Client");
            Click("Details");
            WaitToSeeHeader(That.Contains, "DETAILS");
        }
    }
}
```

