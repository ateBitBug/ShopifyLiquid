# shopify_liquid

https://github.com/uxhacks/shopify-tutorial

things uploaded to shopify are:
assets
config
layout
locales
sections
snippets
templates

echo "# vuejs_test" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/ateBitBug/vuejs_test.git
git push -u origin main

creat a git repository and follow its instruction

how to set up theme for shopify (node version of themeKit)
https://shopify.dev/themes/tools/theme-kit
https://shopify.dev/themes/tools/theme-kit/getting-started

Important findings are recorded here.

git status -> shows what are being untracked by git
git add . -> to add tracked files to git
git commit -m "initial commit" -> upload to git
git push -u origin main
git pull

theme watch -> shopify monitors any changes to scripts

https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files

config.yml

In case you need to ignore a whole folder which was already tracked, do not forget to do it recursively with -r.

    Add foldername/ to .gitignore

    git rm -r --cached foldername/

ignoring secure file from uploading to github

- navigate to .git area
- create a file "touch .gitignore"
- remove the secure file -> git rm --cashed FILENAME

or

- add the file to "exclude"
- cd to .git area -> cd .git/info/exclude

////////////////////////////////////////

SASS setup along with gulp

- install gulp: https://gulpjs.com/docs/en/getting-started/quick-start/
  sudo npm install --global gulp-cli
  npm init -> creates package.json
  npm install --save-dev gulp
  gulp --version

set up gulp-sass: https://www.npmjs.com/package/gulp-sass

gulp-sass -> created node_modules -> exclude from git by adding 'node_modules' in .gitignore

- by using 'gulp sass' -> multiple commands are executed with one command "gulp sass"
  - gulp sass -> creates 'global.css' in the assets folder
    - to use this new 'global.css' file, go to layout -> edit theme.liquid at #78

* now the key to the gulp&sass is that css can be manipulated from scss/custom.scss without touching the original css
  for example, edit 'scss/custom.scss' to create a new 'assets/global.css'

  change this:
  $color-red: rgb(238, 43, 43);

header, body {
background-color: $color-red;
}

to:
$color-red: rgb(238, 43, 43);

.site-header,
body {
background-color: $color-red;
}

- open layout/theme.liquid
  - find line@ 77 -> <link ... stylesheet>; copy this line and change 'theme.css'
    to 'global.css' (see #78)

and then use 'gulp sass' which creates a new 'assets/global.css'
again additional changes can be made to 'scss/custom.scss' to create a new 'assets/global.css'

.site-header,
.site-header\_\_mobile-nav,
body {
background-color: $color-red;
}

- now adding 'theme watch' to gulp sass by adding another task in 'gulpfile.js'
- once 'theme watch' is added to gulp along with sass, use the command 'gulp watch' to run multiple
  commands and updates the theme
- to remove white spaces in the code, add in the 'gulp-clean' in the commands by adding it in 'gulpfile.js

* now to add all changes:
  - git status
  - git add .
  - git status
  - git commit -m "added gulp to execute sass-clean-watch and updates the pages
  - git push -u origin main
  - git pull

- go to github and review the '# commit'

- to restart gulp -> gulp watch
