# tforge-docs

## TForge project's documentation

### Initial setup

-   Clone the repository into _tforge-gh-pages_ subfolder (the repository does not contain _gh-pages_ branch yet):

` ~/projects/github/tforge-gh-pages $ git clone https://github.com/sergworks/tforge.git . `

-   Create _gh-pages_ branch:

` ~/projects/github/tforge-gh-pages $ git checkout --orphan gh-pages `

### Deploy to GitHub Pages

-   Delete all files from work directory:

` ~/projects/github/tforge-gh-pages $ git rm -rf . `

-   Copy the site content to work directory

-   Stage new files:

` ~/projects/github/tforge-gh-pages $ git add . `

-   Commit new files:

` ~/projects/github/tforge-gh-pages $ git commit -m "commit" `

-   Push the site to GitHub Pages:

` ~/projects/github/tforge-gh-pages $ git push -u origin gh-pages `










