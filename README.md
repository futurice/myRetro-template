# MyRetro - Template

![MyRetro](https://github.com/futurice/myRetro-template/workflows/MyRetro/badge.svg)

This is a template repository for your own myRetro.

All the places where you should write text are marked in the example [MyRetro](./MyRetro.md). Writing in other places will most likely lead to parsing errors.

## Set up for yourself

Use the green `Use this template` to create your own copy of the repository in your personal github account. It can either be public or private, depending on how you would like it, both work equally good.

Then you can commit changes to `MyRetro.md` and the included workflow will automatically build a zip file of the site, that you can download from `Actions > <current run> > Artifacts`

**Bonus step: Publish to github pages**

Generate a new ssh key with `ssh-keygen -t rsa -b 4096 -f deploy_key`. Go to `Settings > Deploy keys > Add new` and paste the public key (`deploy_key.pub` into the "Key" text area. Name it however you like, e.g. "Github pages deploy key". **Turn on write access**, otherwise the publish will fail.

After adding the public key, go to `Settings > Secrets > Add new secret` and add the private key (`deploy_key`) as `Value` and name it `ACTIONS_DEPLOY_KEY`.

Now trigger a build either by pushing a new commit or by rerunning an earlier build.

Lastly go to `Settings`, scroll down to `GitHub Pages` and select the `gh-pages` branch from the dropdown

## Develop locally

Download the [latest release binaries](https://github.com/futurice/myRetroGenerator/releases/latest/) and unzip them in this folder.
Run `chmod +x ./myRetroGenerator` to make it executable.

This repo contains a [`Makefile`](./Makefile) with three targets:

- `make html` will build the static website and put it into the `docs/` folder by default. This folder is already gitignore'd. For this you only need `make` installed
- `make pdf` will build the website and generate a pdf version of it. This need `google-chrome`, `browser-sync` and `make`. You can install `browser-sync` with `npm install --global browser-sync`.
- `make watch` will watch the Retro markdown for changes and rebuild the static site as well as reload the browser. This needs `browser-sync`, `inotify-tools` on Linux and `fswatch` on Mac.

## Rename the retro markdown

To rename the retro file (e.g. to use it as a README.md instead of these instructions), you just have to update the `RETRO` variable in the `Makefile`. The CI will continue to work.

## Update your own repo with changes from this template

To bring your own repo up to date with the latest version of the template run:

```
git remote add template https://github.com/futurice/myRetro-template.git
git fetch template
git merge template/master
```

Then you have to fix the merge conflicts. After the rebase is completed, push your changes with `git push --force` and you are up to date!
