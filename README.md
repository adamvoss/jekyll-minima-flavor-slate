# Minima flavor: Slate

The slate flavor makes [minima](https://github.com/jekyll/minima) look like [slate](https://github.com/pages-themes/slate) so slate-based websites can expand beyond a single page.

You can can [preview the flavor to see what it looks like](http://vossad01.github.io/jekyll-minima-flavor-slate), and [compare it to the Slate preview](http://pages-themes.github.io/slate).

![slate flavor preview](/screenshot.png)

## Installation
You can either manually copy the `_sass` and `assets` folder into your minima-based project, or you can add this repository as a remote and merge `master` as an unrelated branch (be cautious of the README.md and LICENSE file also in `master`).

## Minima flavors
Adding the right css rules on top of the `minima` theme can let a site transition to a more full-featured theme without dramatically changing the apperance of the site.  GitHub Pages has great, gem-based themes to help you create an attractive project page quickly.  Unfortunately, when a site grows beyond a single page, the project faces the growing pains because these themes do not provide any navigation area so the projct must either switch to a new theme or hack the existing one for some rudimentery support.  The `minima` theme is exceptional for having built-in support multiple pages and navigation and this repository themes it to look like the slate theme.

## Branches
- master
    The default branch which contains the flavor files.
- jekyll-comparison
    A new Jekyll including this flavor for comparison with vanilla minima.
- slate-comparison / gh-pages
    A Jekyll project including this flavor and the content from the Slate preview website for comparision with the Slate theme.

## Upstream (slate) changes
This repository derived directly from the Slate-theme.  `git subtree` does not work when all of the files are not in the directory; however, the concept used is the same.  The following command can be used on the slate repository to extract compatible history and get any new changes.  The command is derived from [this StackOverflow answer](http://stackoverflow.com/a/6006679/1072626).

``` shell
git filter-branch -f \
    --prune-empty \
    --index-filter '
        git ls-tree -z -r --name-only --full-tree $GIT_COMMIT \
        | grep -z -v "^_sass/jekyll-theme-slate.scss$" \
        | grep -z -v "^_sass/slate.scss$" \
        | grep -z -v "^LICENSE$" \
        | grep -z -v "^assets/images/bg_hr.png$" \
        | xargs -0 -r git rm --cached -r
    ' \
    -- \
    --all
```