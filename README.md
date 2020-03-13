# MyRetro - Template

![MyRetro](https://github.com/futurice/myRetro-template/workflows/MyRetro/badge.svg)

This is a template repository for your own myRetro.

## Set up for yourself

Use the green `Use this template` to create your own copy of the repository in your personal github account. It can either be public or private, depending on how you would like it, both work equally good.

Then you can commit changes to `MyRetro.md` and the included workflow will automatically build a zip file of the site, that you can download from `Actions > <current run> > Artifacts`

**Bonus step: Publish to github pages**

Generate a new ssh key with `ssh-keygen -t rsa -b 4096 -f deploy_key`. Go to `Settings > Deploy keys > Add new` and paste the public key (`deploy_key.pub` into the "Key" text area. Name it however you like, e.g. "Github pages deploy key". **Turn on write access**, otherwise the publish will fail.

After adding the public key, go to `Settings > Secrets > Add new secret` and add the private key (`deploy_key`) as `Value` and name it `ACTIONS_DEPLOY_KEY`.

Now trigger a build either by pushing a new commit or by rerunning an earlier build.

Lastly go to `Settings`, scroll down to `GitHub Pages` and select the `gh-pages` branch from the dropdown
