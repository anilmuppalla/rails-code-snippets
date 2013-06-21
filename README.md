Rails Code Snippets
=================

This contains a list of all useful code snippets that i have used and aggregated over my time developing Rails based applications.

##Ruby Rails Code
<ol>

<li> Use the link_to_active_state gem to make active any link when selected, usually seen in nav bars. Use the following to add to your nav bars </li>

```
<%= link_to "Sign in", new_user_session_path, active_on: new_user_session_path %>
```

* If you need to 
