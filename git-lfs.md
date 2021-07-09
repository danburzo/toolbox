# Git LFS

[Git LFS](https://git-lfs.github.com/) (Large File Storage) is useful for storing binaries in your GitHub repositories. 

## Installation

Once on the machine:

```bash
brew install git-lfs
git lfs install
```

Then once in each repo:

```bash
git lfs track "static/img/**/*"
```

> Note: the glob pattern that also matches _subfolders_ is `**/*`.

This will produce a `.gitattributes` file that needs to be committed to your repository.