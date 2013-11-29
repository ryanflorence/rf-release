rf-release
==========

Tag, push, and publish your repositories with one command.

Installation
------------

```sh
npm install rf-release
# or
npm install rf-release -g
```

Usage
-----

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
5. pushes master and the new tag to origin
6. publishes to npm

But I have a build step before I can tag and publish!
-----------------------------------------------------

That's fine, just do your build first w/o committing, then run
`release`. It'll all go in the same commit.

License and Copyright
---------------------

MIT License

(c) 2013 Ryan Florence

