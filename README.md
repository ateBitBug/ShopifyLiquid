# shopify_liquid
creat a git repository and follow its instruction

how to set up theme for shopify
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

ignoring secure file from uploading to github
+ navigate to .git area
+ create a file "touch .gitignore"
+ remove the secure file -> git rm --cashed FILENAME

or

+ add the file to "exclude"
+ cd to .git area -> cd .git/info/exclude
