#`LoginAs<T>`



Before reading this you should understand what a snippet is and where a snippet lives. Please read the related links to find this out.

The command "`LoginAs<T>()`" is actually a shortcut to a bunch of Pangolin code defined in the Users feature. "T" is a generic class which should be another test case that inherited UITest class.

Login snippets are treated like test cases, except that they are not treated as duplicates when used in a precondition.

Any test case saved in the Users tab in your Master Test Plan is considered to be a login snippet. They are called after the command 'LoginAs<T>()', not 'Run<T>()' like other test cases.

They all follow the same basic structure save for certain special projects/circumstances. e.g.



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
            Logout();
            AssumeDate("01/07/2017");
            Goto("/");
            Set("Email address").To("adamadmin@uat.co");
            Set("Password").To("Test_123");
            Click("Login");
            Expect("Adam Admin");
        }
    }
}
```


Firstly, the logout command deletes cookies, then the date the test is to take place is set and the User is
returned to the login page, followed by entering your login details and validating that a successful login
occurred.