# Visual Regression Testing Sample deployment code


## This sample code uses:
- WordPress composer https://github.com/pantheon-systems/wordpress-composer
- Composer https://getcomposer.org/
- Themes and plugins from WordPress Packagist https://wpackagist.org/
- Github Actions for CI / CD https://github.com/features/actions
- BackstopJS for Visual Regression Testing https://github.com/garris/BackstopJS
- Pantheon for hosting http://pantheon.io/ 

## WorkFlow:
- Code pushed to GitHub
- GitHub Actions kicks in to do the composer install, core, theme and plugin updates
- Deploy latest code to development site
- Do Visual Regression to the Development site VS Live site
- Deploy the backstop reports to a QA multidev in Pantheon

## Setup Pre-requisite fo youn to use this build:
You'll need an account in Pantheon and in GitHub to test this build
1) Github account for repo and CI/CD ( You can use GitLab or Bitbucket but you may need to modify to match their variables )
2) Pantheon account for Hosting ( You can use other hosting but you'll have to modify the script accordingly)

## Setup:
1) Clone this repo
2) Modify .github/workflows/composer-build.yml to reflect your 

`REFERENCE_SITE_URL`

`QA_PANTHEONENV`

`PANTHEONENV`

`PANTHEONSITENAME`

3) Further modify scripts/github/test/backstopjs/backstopConfig.js for additional settings

4) Add these as secret tokens in GitHub

`PANTHEONEMAIL` - Your Pantheon registered email

`PANTHEONSITEUUID` - Site UUID where your code will be deployed to

`STAGING_PRIVATE_KEY` - https://pantheon.io/docs/ssh-keys

`MACHINETOKEN` - https://pantheon.io/docs/machine-tokens#create-a-machine-token

## Why we use composer in WP?
- Easier plugin, theme and core version management from composer.json file
- Less merge conflicts
- Only maintain build scripts and custom code in the repo
- Easier for team members to replicate setup