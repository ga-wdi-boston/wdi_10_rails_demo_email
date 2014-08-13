## Action Mailer


#### Generate a mailer Ruby class and View

```
rails g mailer user_mailer signup_confirmation
```

We now have a app/mailers/user_mailer.rb and two views in the app/views/user_mailer directory.

#### Modify the app/mailers/user_mailer.rb class

Our emails will be from _ga@example.com_. We will send the email to the user's email address and make the user available to the views by creating a instance variable @user.  

```
class UserMailer < ActionMailer::Base
  # By default the email is from GA
  default from: "ga@example.com"

  # Subject can be set in your I18n file at config/locales/en.yml
  # with the following lookup:
  #
  #   en.user_mailer.signup_confirmation.subject
  #
  def signup_confirmation(user)
    # create an instance variable so that the view has access
    # to the user.
    @user = user

    # send email to the user
    mail to: user.email, subject: "Sign Up Confirmation"
  end
end
```