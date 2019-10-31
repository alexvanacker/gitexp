# gitexp
A repo for playing around with Git


## git filter-branch
My first experiment will be with git filter-branch.

In this setup, there are front files (the folder `front` and the `front.json` file) and back files (the `api` and this
README).

The first attempt is to use the following command:

```sh
git filter-branch --index-filter "git rm -rf --cached --ignore-unmatch front front.json" HEAD
```

The files are indeed removed from the full history, yet the commits remain.
Is this what we want?

See branch "filter-front".


