rf-release
==========

Tag, push, changelog, and publish your repositories with one command.

Installation
------------

```sh
npm install rf-release
# or
npm install rf-release -g
```

Usage
-----

### BEFORE YOUR FIRST RUN

There are a couple gotchas I haven't spent time to smooth over. Before
your first run:

1. Ensure you have a semver style git tag in the past, otherwise the
   changelog script will fail.

   ```sh
   git checkout <some old commit>
   git tag v0.0.0
   git checkout master
   ```

2. Make sure you've committed a blank `CHANGELOG.md` to git. The code
   that creates the release commit uses `git commit -am` so if
   `CHANGELOG.md` is a new file, it won't be included in the commit.

    ```sh
    touch CHANGELOG.md
    git add CHANGELOG.md
    git commit -m 'added changelog because ryan is lazy'
    ```

Okay, now you're ready:

```bash
# if `node_modules/.bin` is in your path
# or you installed globally:
$ release

# otherwise
$ node_modules/.bin/release
```

What it does
------------

1. prompts you for the new version
2. updates `package.json` and `bower.json` (if they exist)
3. commits the version updates with a simple commit message
   ("release {version}")
4. creates the tag "v{version}"
5. generates a changelog with [rf-changelog][1]
5. pushes master and the new tag to origin
6. publishes to npm

But I have a build step before I can tag and publish!
-----------------------------------------------------

That's fine, just do your build first w/o committing, then run
`release`. It'll all go in the same commit. For example,
[react-router][2]'s release script does this.

License and Copyright
---------------------

MIT License

(c) 2014 Ryan Florence


  [1]:https://github.com/rpflorence/rf-changelog
  [2]:https://github.com/rackt/react-router/blob/master/script/release

