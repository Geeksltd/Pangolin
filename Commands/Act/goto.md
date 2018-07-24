#Goto("/");



The Goto command redirects the current page to another URL within the same domain.This is used when
action commands (Set, Click etc) cause the page to change. This ensures that the page(s) you intended to
navigate to, have been navigated to. In particular that the URL is what you would expect when the page change occurs.
The Goto  command is used by default in login snippets to ensure that you are on the login page when you
attempt to login (instead of relying on buttons in the application).