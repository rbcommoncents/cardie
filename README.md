<p align="center">

  <!-- ![Cardie Logo](repo/images/logo_light.png#gh-dark-mode-only)
  ![Cardie Logo](repo/images/logo_dark.png#gh-light-mode-only) -->

  ![Hacktoberfest Banner](repo/images/hacktoberfest24.png)

</p>

---

<div align="center">

  [![](https://dcbadge.limes.pink/api/server/G24Ag9FqB8)](https://discord.gg/G24Ag9FqB8)
  [![](https://img.shields.io/github/issues/nfoert/cardie?style=for-the-badge)](https://github.com/nfoert/cardie/issues)
  [![](https://img.shields.io/github/license/nfoert/cardie?style=for-the-badge)](https://github/nfoert/cardie/blob/main/LICENSE)

  **[Live Server](https://cardie-uwtwy.ondigitalocean.app/)**

  **[Wiki](https://github.com/nfoert/cardie/wiki)** | 
  **[Releases](https://github.com/nfoert/cardie/releases)**


  **The latest changes are available in the [development](https://github.com/nfoert/cardie/tree/development) branch! Please check there for the most up to date changes.**

</div>

---

Design a unlimited number of business or information cards about yourself, share a link or QR code to them, print it out, and save other people's cards to your virtual wallet for later. Once you've created a card you can get analytics data on how your cards are getting visited, you can edit your cards as things change, and you can keep cards private so only people with a link to your card can see it.

<div align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=django,python,html,css,js,github,git,alpinejs"/>
  </a>
</div>

<div align="center">
  <img src="repo/images/screenshot1.png" style="border-radius: 10px; margin-top: 20px;">
</div>

> [!IMPORTANT]
> Cardie is currently in an open alpha. Things will be rapidly changing and bugs are to be expected.

## Hacktoberfest

Happy Hacktoberfest! I hope that you find this project interesting and that some issues offer a good learning experience! Help of any kind would be greatly appreciated.

- You can check out the [issues page](https://github.com/nfoert/issues) for anything that piques your interest, or you can check the [hacktoberfest tag](https://github.com/nfoert/cardie/issues?q=sort%3Aupdated-desc+is%3Aopen+label%3Ahacktoberfest) for specific issues I've selected for this Hacktoberfest.
- Additionally, please check out [contributing](#contributing) for some information on how you can contribute to this project.

## Installation

First, clone this repository using the following command
```
git clone https://github.com/nfoert/cardie
```

Then, navigate to that directory and create a new python virtual environment
```
cd cardie
python3 -m venv .venv
```

Activate the virtual environment using the command for your system (Linux is used here) and install the required dependencies
```
source ./.venv/bin/activate
pip install -r requirements.txt
```

Next, create a django superuser and make and migrate the models
```
cd cardie
python manage.py createsuperuser
python manage.py makemigrations
python manage.py migrate
```

Now just run the server using the following command, or run the `Start server` task in your Visual Studio Code
```
python manage.py runserver
```

Finally, navigate to `http://127.0.0.1:8000/admin` and log in using your new administrator account. Create a new `Server` object and be sure to configure the `ip` to be `http://127.0.0.1:8000`.

##### Secure alternative solution for server

Create a Server object manually in the Django Shell to avoid admin credentials being created in production environment.

```
python manage.py shell
```
Inside the shell, create a Server instance:
```
from main.models import Server
Server.objects.create(ip='http://127.0.0.1:8000)
```
To escape the shell just use ctrl + d keys.

### Additional steps for Production installation

This depends on what server hosting provider you're using. However, there's a couple environment variables you need to set and there's a run command.

Set the following global environment variables:
- `DJANGO_ALLOWED_HOSTS` -> `${APP_DOMAIN}` (This works on DigitalOcean, this may not work on every hosting provider)
- `DJANGO_SETTINGS_MODULE` -> `cardie.settings_production`
- `DJANGO_LOG_LEVEL` -> `WARNING`
- `STATIC_URL` -> `/static/main`

- `SECRET_KEY` -> `<your new secret key>` (Generate this using `django.core.management.utils.get_random_secret_key()`. If possible you should encrypt this value in your hosting provider.)
- `DEBUG` -> `False`
- `DATABASE_URL` -> `${db.DATABASE_URL}` (This works on DigitalOcean, this may not work on every hosting provider)

## To Do

There's lots of things that need implemented or changed in this project. Please see [TODO.md](TODO.md).

## Contributing

I'd love to see contributions to this project! Please check out the [issues](https://github.com/nfoert/cardie/issues) page to see what things currently need fixed or added.

Additionally, check [TODO.md](TODO.md) for a rough todo list of things that need implemented, and the [wiki](https://github.com/nfoert/cardie/wiki) for some information on how to work with some of the existing systems.

When contributing, first fork this repository. To ensure you're getting the latest development changes uncheck the `Copy the main branch only` option. Then, create a new branch with your change in it, either from the `main` branch or the `development` branch. Finally, open a pull request which merges into the `development` branch. Your changes will be reviewed and merged soon. Thanks for contributing to Cardie!