# PyLadiesCon Web Portal

# Local Dev setup

Requirements: Have these installed first before continuing further.

- Docker
- Docker compose
- GNU Make
- GitHub CLI (optional, but recommended) https://cli.github.com/


## Starting the local env

1. Clone the repo. If using GitHub CLI, run:

```
gh repo clone pyladies/pyladiescon-portal
```

2. Start the local environment:

```
make serve
```

3. Open the browser and go to <http://localhost:8000/> to see the app running.

4. Run the tests:

```
make test
```

## Emails in local env

The docker compose development environment includes a
[maildev](https://maildev.github.io/maildev/)
instance for previewing emails locally.

It is accessible at <http://localhost:1080> and will show all emails sent by the application.

## Set up your Account as a Staff user

1. Go to <http://localhost:8000/accounts/login/>
2. Go to the "Sign up" link
3. Fill in the email address, username, and password.
4. Upon signing up, the confirmation email will be available at <http://localhost:1080/>. Enter this code on the sign up form.
5. Your account is now verified.
6. On the terminal, go to Django shell:

```
make manage shell
```
7. Set your account as a staff and superuser:

```
from django.contrib.auth.models import User
user = User.objects.get(username='your_username') #use the username you created above
user.is_staff = True
user.is_superuser = True
user.save()
```

8. You can now access the /admin page.
