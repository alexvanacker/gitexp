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

### Trying with --prune-empty

See branch `git-filter-prune`


The command ran was

```sh
git filter-branch --index-filter "git rm -rf --cached --ignore-unmatch front front.json" --prune-empty HEAD
```

This feels like a safer version of what `git obliterate` does (see below). In this case, commits with front-only
code were removed.


## Using git obliterate

Cf. this command from [git extra](https://github.com/tj/git-extras/blob/master/Commands.md#git-obliterate)

See `git-obliterate` branch for the result.

The command ran was:

```sh
git obliterate front front.json
```

The result is way more hardcore: origin/master, master were rewritten! Well, origin/master (i.e. the remote)
was left untouched, but the reference would have been overwritten had I pushed my work branch without some
tweaking.

However the commits which had only front code were fully removed. Only commits
with both back and front impacted remained, with only the back part actually
remaining.

## Using `git-filter-repo`

As per Git version 2.24.0, the recommended way to clean repository history is to use
[git-filter-repo](https://github.com/newren/git-filter-repo).

What is tried here is:

```sh

git-filter-repo --path front --path front.json --invert-paths

```


## TODO
What impacts on tags?
