# Sharing email 
We use the `django.core.mail` module which imports the `send_mail` function. But first we connect to an SMTP server to send our mail
Here is the SMTP configuration for the app
```python
EMAIL_HOST = 'smtp.gmail.com'  
EMAIL_HOST_USER = 'ajibewadannyboi@gmail.com'  
EMAIL_HOST_PASSWORD = 'zatl epjy kyxa ilmt'  
EMAIL_PORT = 465  
EMAIL_USE_SSL = True
```
I use my app key to connect to Gmail smtp server. I think the SSL port work for my system instead of the TLS port
## Sending the mail for the app
I created a form for the user so that they can use to send the mail. The `send_mail()` takes in the the following argument `subject`, `message`, `sender_email` and the `recipient` or list of recipient.  e.g., `send_mail(subject, message, sender, recipent` 
**Note**:  We can render form onto the template using the following methods: 
- `form.as_p` it is rendering forms in the form of the `<p></p>` tag 
- `form.as_table` it renders form in form of the table tag
- `form.as_ul` it render form in form of unordered list
But we can also render them manually which I prefer.
The `csrf_tokent` template tag generates an token to avoid **cross-site request forgery(CSRF)**. This tag generates and hidden field the is rendered like this 
```html
<input type='hidden' name='csrfmiddlewaretoken' value='26JjKo2lcEtYkGoV9z4XmJIEHLXN5LDR'/> 
```
# Creating a Comment System 
It is important to note the following columns for the comment system in the future I might use for my personal project. 
- post (FK)
- name
- email 
- body of comment 
- created
- updated 
- active 
It is important to know that the `related_name` attribute allow me to call the comment made on post like this `post.comment.all()` but if I do not put it Django will just set the related name to `comment_set`, `_set` will just follow the class name all in lowercase 

**Note:** Django use to base case for it form which are 
- Form class
- `ModelForm` This is used for model in the database of the app I am building 
I think I will be using the `@requred_POST` decorate for my model forms so I will not be using the conditional statement.
- `form.save(commit=False)` can be used to save a form after validation with out saving it to the database for further usage before saving the form to the database. 

**Note:** HTTP 405 error it means that **method not allowed** if the request is not the restricted request. 
> I can create a new model variable from a from that is valid using the `save(commit=False)` method of the form thereby allowing me to further manipulate the instance.  

**Note:** The `save()` method is only available for ModelForm instance not the Form instance since they are not linked to any model.
`{% with %}` tag allow one to assign a variable to a new value in the template. It is also useful for avoiding hitting the database multiple time
# Creating a custom tag
Create a separate template tag folder which will contain the `__init__.py` file and the file that will contain the template tag. 
```python
from django import template

register = template.Libary()

@register.simple_tag
# Custom tag defined below
```
There is also `@register.inclusion_tag` which return context variable and use this context variable in an html template and includes it in the location in which the tag is used.
