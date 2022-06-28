# project-overview
Project structure and external services


```bash
gabehoban@MacBook-Pro cps491s22-team5 % tree -L 1
.
├── Dockerfile         # Template for the Docker image that gets pushed to Heroku
├── README.md          # Project Description
├── admin/             # Code for the admin page (AdminLTE)
├── backend/           # Code for the backend API
├── convert/           # Python script convert and upload members based on an excel sheet
├── frontend/          # Code for the public frontend website (swj1894.org)
├── god_mode.sh        # Random script....
```

## Docker CI/CD

In order to create a pipeline to automatically deploy code commited to the main branch, we used GitHub Actions along with the [heroku-deploy](https://github.com/AkhileshNS/heroku-deploy) addon. The code for this can be found in `.github/workflows`.

1. Commit to the main branch triggers GitHub Action: CI/CD.

2. The GitHub Action, using the heroku-deploy add-on, builds a docker image based on the Dockerfile in the root directory.

3. After the image is successfully built, it is pushed to the Heroku Repository using the API keys stored in Repository Settings.

4. This triggers Heroku to automatically start a new container from the docker image.

5. Boom... the website is updated.
 
 
*Should you ever manage to run out of Github build minutes, you can adapt the god_mode script to locally generate the docker image and push it directly to Heroku.*

## Admin Page

We used the open-source [AdminLTE](https://adminlte.io/) template to create the admin page. If you are planning to add more features, it is worth browsing the AdminLTE documentation first to verify that the feature has not been implemented yet. 

```bash
gabehoban@MacBook-Pro admin % tree -L 1
.
├── LICENSE       # Required due to open-source MIT license
├── dist/         # Custom JS for the pages is stored in dist/js/pages/
├── favicon.ico   # FavIcon :)
├── index.html    # Main HTML page
├── pages/        # HTML code for the pages
└── plugins/      # Scripts saved locally in order to reduce loading time
```

## Backend

