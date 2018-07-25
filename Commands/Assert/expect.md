# Expect("text")



Searches the current page or pop-up window for the text after the command. The first argument can be That.Equals or That.Contains. Each has a purpose for narrowing the search.

The expect command should only be used when 'ExpectButton()', 'ExpectField()', 'ExpectHeader()' or 'ExpectRow()' are not applicable. It is also good practice that it should be the last command to appear in every test.