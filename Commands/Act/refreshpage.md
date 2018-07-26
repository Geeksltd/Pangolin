# RefreshPage();



The RefreshPage command refreshes the current page.It is used alone on a line to force a web page to refresh at this point in the Pangolin code.

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
            
            Click("Configurations");
            WaitForNewPage();
            Click("Candidate");
            WaitToSeeHeader(That.Contains, "COMPLIANCES");
            Click("Timesheet Legal Information");
            WaitToSee(What.Contains, "TIMESHEET LEGAL INFORMATION");
            ExpectLabel(That.Contains, "Legal information");
            WaitToSee(What.Contains, "Save");
            Click("Save");
            WaitToSee(What.Contains, "Timesheet legal information updated");
            Click("OK");
            RefreshPage();
        }
    }
}
```

