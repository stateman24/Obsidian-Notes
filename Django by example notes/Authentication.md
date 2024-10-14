- The authentication framework of Django is located in the `django.contrib.auth` module 
- Middleware is classes with methods that are globally executed during the request or response phase
The Django authentication framework has the following models in the `django.contrib.auth.models` package
- User
- Group - A group of model to categorize users
- Permission - To flag User or Group to perform any activity
>Note the difference between authenticate() and login(): authenticate() checks
user credentials and returns a User object if they are correct; login() sets the user in
the current session.

To django authentication framework has the following functionalities
- User login
- User logout 
- Change Password 
- Reset Password 
Django provides the following class-based views to deal with authentication. All of them are located 
in django.contrib.auth.views:
- LoginView: Handles a login form and logs in a user
- LogoutView: Logs out a user
Django provides the following views to handle password changes:
- PasswordChangeView: Handles a form to change the user’s password
- PasswordChangeDoneView: The success view that the user is redirected to after a successful password change
Django also includes the following views to allow users to reset their password:
- PasswordResetView: Allows users to reset their password. It generates a one-time-use link 
with a token and sends it to a user’s email account
- PasswordResetDoneView: Tells users that an email—including a link to reset their password—
has been sent to them
- PasswordResetConfirmView: Allows users to set a new password
- PasswordResetCompleteView: The success view that the user is redirected to after successfully 
resetting their password

The templates for this authentication views are always in the `templates/registration/` folder 

## User Registration
