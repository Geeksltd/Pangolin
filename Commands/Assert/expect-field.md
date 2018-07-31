# ExpectField("text")



This command searches the current page for an HTML field with the text contained in quotation marks on it. You can use this command when verifying or validating that an intended field appears as a result of some other action you performed within Pangolin.

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
            Click(What.Contains, "Candidate");
            WaitToSeeHeader(That.Contains, "Candidate Details");
            AtLabel("Title").Expect("Mr");            
            ExpectField("First name");
            AtLabel(That.Contains, "First name").Expect(What.Contains, "Agency1");            
            ExpectField("Last name");
            AtLabel(That.Contains, "Last name").Expect(What.Contains, "Candidate");            
            ExpectField("Date of birth");
            AtLabel(That.Contains, "Date of birth").Expect(What.Contains, "01/01/1980");
            AtLabel(That.Contains, "Gender").Expect("Male");
            AtLabel(That.Contains, "Nationality").Expect(What.Contains, "English");
            Click("Candidate Status");
            WaitForPopup();
            ExpectHeader(That.Contains, "Candidate Status");
            Click("Cancel");
            WaitToSeeHeader(That.Contains, "Candidate Details");
        }
    }
}
```

