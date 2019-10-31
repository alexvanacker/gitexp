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


## Using git obliterate

Cf. this command from [git extra](https://github.com/tj/git-extras/blob/master/Commands.md#git-obliterate)

See `git-obliterate` branch for the result.

The command ran was:

```sh
git obliterate front front.json
```
