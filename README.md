Rails Code Snippets
=================

This contains a list of all useful code snippets that i have used and aggregated over my time developing Rails based applications.

##Ruby Rails Code


Use the link_to_active_state gem to make active any link when selected,  usually seen in nav bars. Use the following to add to your nav bars

```HTML+ERB
<%= link_to "Sign in", new_user_session_path, active_on: new_user_session_path %>
```
If you need to add a bootstrap icon in your button

As part of your form


```erb
<%= button_tag(type: 'submit', class: "btn btn-success") do %>
    <i class="icon-ok icon-white"></i> Signup
  <% end %>
```

Normal way ( here you can see i don use the bootstrap provided icons, use fontello for its large collections)


```erb
<%= link_to "<i class=\"fontello-icon-off \"></i>".html_safe,
          destroy_user_session_path,
          class: "btn btn-danger", :'data-toggle' => "popover", :title => "Sign Out",
          method: :delete %>
```

Using Gravatar to embedd user profile images

```ruby
def gravatar_for(user, options = { size: 50 })
    gravatar_id = Digest::MD5::hexdigest(user.email.downcase)
    size = options[:size]
    gravatar_url = "https://secure.gravatar.com/avatar/#{gravatar_id}?s=#{size}"
    image_tag(gravatar_url, alt: user.name, class: "gravatar img-polaroid")
  end
```
after you write this in one of the helper files you can call for the gravatar image by:

```erb
<%= gravatar_for current_user, size: 60 %>
```

Make an Image a clickable button

```html+erb
<%= link_to image_tag("mark_attendance.gif", :size=>'160x120', :alt=>'attendence', 
:class=>"img-rounded"), '#', {:class=>"thumbnail"}%>
<%= label_tag 'Mark Attendance'%>
```

**Rails Date and Time picker**

*Requirements*

* jquery-rails gem
* [jquery-ui-rails](https://github.com/joliss/jquery-ui-rails)
* [Datepicker](https://github.com/albertopq/jquery_datepicker)
* [Timepicker](https://github.com/trentrichardson/jQuery-Timepicker-Addon)


*Datepicker*

The date field should be set to a "text_field".
```erb
<%= f.text_field :date %>
```
Javascript for application.js file

```js
$(function() {
  $('#selector').datepicker();
});
```
*Timepicker*

The time field should be set to a "text_field".
```erb
<%= f.text_field :time %>
```
Javascript for application.js file
```js
$(function(){
 $('#selector').timepicker();
});
```

CSS for Timepicker to be added in application.css file
```css
.ui-timepicker-div .ui-widget-header { margin-bottom: 8px; }
.ui-timepicker-div dl { text-align: left; }
.ui-timepicker-div dl dt { height: 25px; margin-bottom: -25px; }
.ui-timepicker-div dl dd { margin: 0 10px 10px 65px; }
.ui-timepicker-div td { font-size: 90%; }
.ui-tpicker-grid-label { background: none; border: none; margin: 0; padding: 0; }

.ui-timepicker-rtl{ direction: rtl; }
.ui-timepicker-rtl dl { text-align: right; }
.ui-timepicker-rtl dl dd { margin: 0 65px 10px 10px; }
```

**Flash Messages**
```erb
<% flash.each do |key, value| %>
    <%= content_tag(:div, class: "alert alert-#{key}") do%>
        <%= content_tag(:button, 'x',type: "button",class: "close",
        :'data-dismiss'=>"alert") %>
        <strong><%=value%></strong>
    <% end %>
<%end%>
```
If you use Devise to manage the Authentication, Here is the *Remember Me* code
```erb
<% if devise_mapping.rememberable? -%>
      <%= f.check_box :remember_me %> 
      <%= f.label :remember_me, class: "checkbox inline" %>
  <% end -%>
```

If you want any field to be uneditable, lets say when you want to update a useraccount,
you might want the email of the user be uneditable.
```erb
<%= f.email_field :email, readonly: "readonly", name: "uneditablefield" %>
```

If you want Flash Messages corresponding to the actions 
```erb
<% flash.each do |key, value| %>
        <%= content_tag(:div, class: "alert alert-#{key}") do%>
        <%= content_tag(:button, 'x',type: "button",class: "close",
                :'data-dismiss'=>"alert") %>
            <strong><%=value%></strong>
          <% end %>
      <%end%>
```

If you want to change the look of the scroll bar.
```css
::-webkit-scrollbar {
    width: 8px;
}
::-webkit-scrollbar-track {
    background-color: inherit;
}
::-webkit-scrollbar-thumb {
    background-color: #bf3e11;
    border-radius: 5px;
}
::-webkit-scrollbar-thumb:hover {
  background-color: #aaa;
}
```
