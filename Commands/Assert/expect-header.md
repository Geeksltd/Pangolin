# ExpectHeader("text")



The header command focuses Sanity on any HTML h2 elements on your page. e.g. ExpectHeader("Customer Details"). Use this command when verifying or validating that an intended header appears as a result of some other action you performed within Pangolin.

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
            LoginAs<Clientuser>();
            Click("Banks");
            Click("Bank Agency");
            WaitToSeeHeader(That.Contains, "Bank Candidates");
            ExpectHeader(That.Contains, "Bank Candidates");
            Click(What.Contains, "Candidate1");
            WaitToSeeHeader(That.Contains, "Candidate Details");
            ExpectHeader(That.Contains, "Candidate Details");
            AtLabel("Title").Expect("Mr");
            AtLabel(That.Contains, "Last name").Expect(What.Contains, "Candidate");
            Click("Candidate Status");
            WaitForPopup();
            ExpectHeader(That.Contains, "Candidate Status");
            Click("Cancel");
        }
    }
}
```

