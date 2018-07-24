## Example: End-to-end test

There are cases when a single test case is verifying multiple features. For example "ManageXXX" test cases
usually test Edit, Delete, Search, ...
It's possible for such tests to end up with many lines of Sanity code. It's not a problem to have long sanity tests, but it's key to use comments to logically separate the lines that are testing a particular feature.

See example template.



```C#
using Pangolin;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestUITests
{
    [TestClass]
    public class ManageXXX : UITest
    {
        [TestMethod]
        public override void RunTest()
        {
            // ---- Add MyObject ----
            Run<AddmyobjectJack>();

            LoginAs<myuseruatco>();

            Click("My Objects");

            // ---- Cancel button ---
            Click("New My Object");

            Click("Cancel");

            ExpectHeader(That.Contains, "My objects");

            // ---- Edit ----
            AtRow(That.Contains, "Jack").Click("Edit");

            Set("Name").To("Edited Name");

            Click("Save");

            ExpectRow(That.Contains, "Edited Name");

            // ---- Search: Exclusion ----
            Set("Find").To("non-existent");

            Click("Search");

            ExpectNoRow(That.Contains, "Edited Name");

            // ---- Search: Inclusion ----
            Set("Find").To("Edited Name");

            Click("Search");

            ExpectRow(That.Contains, "Edited Name");

            // ---- Delete ----
            AtRow(That.Contains, "Edited Name").Click("Delete");

            Expect(What.Contains, "Are you sure you want to delete MyObject?");

            Click("Cancel");

            ExpectRow(That.Contains, "Edited Name");

            AtRow(That.Contains, "Edited Name").Click("Delete");

            Click("Yes");

            ExpectNoRow(That.Contains, "Edited Name");
        }
    }
}

```



#run test Add XXX: YYY

In your tests you often need to call other tests to create objects that you need to use for your current test.
Those are essentially "pre-conditions" of your test.
For simplicity of understanding, always include them at the top of your sanity code before any of the lines
related to the current test.



#Manage XXX - multiple edits

There are scenarios where a list module has more than one Edit action.
For example, a USERS LIST module can have a normal edit button, but also one of the columns could be USER STATUS which allows you to toggle between ACTIVE and INACTIVE.
In essence, this status column (links) is an alternative EDIT concept, albeit for a specific field (STATUS). So it
needs to be tested.
The way to test it will be similar to the normal edit function. You click it, make a change, and EXPECT the result.
Such "alternative edit" functionality can be tested similar to the normal EDIT function as part of the MANAGEXXX template.



#Avoid relying on the UI state of referenced tests

When you use the command "Run<test>" your starting screen and logged-in user will be the end point of the last test you ran. It can be tempting to start the steps of the CURRENT TEST from there directly, for example if your test is using the same logged-in user, or the page that ended with.
However it's bad practice.
Rule: Never rely on the END STATUS of your referenced tests. Always start with the basics:

LoginAs<T>
Click("MENU ITEM");

This way you are making it easier to read the test, and understand its context and purpose. So remember that the ONLY reason we use the RUN command, is to bring the DATABASE status to a desired state, and not the UI.



#What test data to use?

When coming up with test data such as texts, numbers, etc, think about the meaning of your purpose.
Instead of a random test data or meaningless or confusing words that lack the actual purpose in them, use
something that literally conveys the purpose of your test.
For example when searching for Exclusion, if you are typing a text that should not yield any result, use the data "non-existent user" or "non-existent product" instead of actual name of a user (product, etc).



#Testing EDIT

When testing an Edit function, in most cases the purpose is to make sure that a simple editing scenario works (i.e. the developers haven't made a fatal mistake). In those cases, changing the value of a single field will do. However, there may be complex scenarios where a particular SIDE EFFECT is expected, in those cases, you need to design your test case and the following actions (expectations) to ensure that the side effect is done correctly.
For example if you are editing a user's availability, your expectation is not just that the data is saved correctly, you also care if the updated availability is working correctly in the modules that use it.
For example you edit a user, make him unavailable, then you go to another module to try and book that user and expect that the system doesn't allow you.
In the former scenario, what you are testing is essentially CRUD.
In the second scenario, you are testing a BUSINESS LOGIC PROCESS or RULE.



#Testing for security

Imagine a scenario where Bob places an Order and can see his Order details using a URL like this:
http://sitename.com/Orders/View?OrderId=100
Now if Alice logs into the system she should not be able to use the same URL and see Bob's order.

You can use Sanity to test for a scenario like this with two new commands:

- CopyUrl()
- GotoCopiedUrl()
  Here is an example:
  // A test can place the purchase normally
  LoginAs<Bob>();
  Run<Make_a_purchase>();
  Click("view_order_details");
  // then copy the URL of the current page into clipboard
  CopyUrl();
- // now we login as Alice and use the copied URL to verify seeing an error message
  LoginAs<Alice>();
  GotoCopiedUrl();
  Expect("Unauthorized");