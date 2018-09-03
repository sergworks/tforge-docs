# Documentation workflow

---

### Initial setup

-   Clone the repository into _tforge-gh-pages_ subfolder (the repository does not contain _gh-pages_ branch yet):

```
 ~/projects/github/tforge-gh-pages $ git clone https://github.com/sergworks/tforge.git . 
```

-   Create _gh-pages_ branch:

```
 ~/projects/github/tforge-gh-pages $ git checkout --orphan gh-pages 
```

### Deploy to GitHub Pages

-   Delete all files from _tforge-gh-pages_ work directory:

```
 ~/projects/github/tforge-gh-pages $ git rm -rf . 
```

-   Copy the site content to _tforge-gh-pages_ work directory

-   Stage new files:

```
 ~/projects/github/tforge-gh-pages $ git add . 
```

-   Commit new files:

```
 ~/projects/github/tforge-gh-pages $ git commit -m "commit" 
```

-   Push to GitHub Pages:

```
 ~/projects/github/tforge-gh-pages $ git push -u origin gh-pages 
```

-   See the [deployed site](https://sergworks.github.io/tforge)

