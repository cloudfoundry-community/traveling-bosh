Traveling BOSH CLI
==================

This project packages the BOSH CLI (with plugins) into self-contained packages that can be downloaded and used by anyone without requiring Ruby and native extensions.

Simple installation
-------------------

Coming soon.

Step-by-step installation
-------------------------

To download the latest release https://github.com/cloudfoundry-community/traveling-bosh/releases

For example:

```
rm -rf tar xfz bosh_cli*.tar.gz
wget https://github.com/cloudfoundry-community/traveling-bosh/releases/download/v1.2788.0/bosh_cli-1.2788.0-linux-x86_64.tar.gz
tar xfz bosh_cli*.tar.gz
rm bosh_cli*.tar.gz
```

To check that its runnable:

```
./bosh_cli-*/bosh
```

You could now create a symlink:

```
rm -f bosh_cli
ln -s $PWD/$(ls -d bosh_cli* | head -n1) bosh_cli
```

Check that its runnable via the symlink:

To check that its runnable:

```
./bosh_cli/bosh
```

Finally, add the `bosh_cli` path into your `$PATH`:

```
export PATH=/path/to/bosh_cli:$PATH
```

Background
----------

This project uses http://phusion.github.io/traveling-ruby/

Create & publish releases
-------------------------

Anyone in the @cloudfoundry-community can create new releases whenever new BOSH CLI versions are released. This section contains the instructions.

You are required to use Ruby 2.1 to create releases as this is what traveling-ruby uses.

You will also need to install https://github.com/aktau/github-release to share the releases on Github.

The release version number is directly taken from the BOSH CLI to be packaged. First, upgrade to latest BOSH CLI.

```
bundle update
```

To create the new release, create new commit & git tag, and upload the packages:

```
rake release
```

This will create three packages:

```
$ ls bosh_cli*
bosh_cli-1.2788.0-linux-x86.tar.gz
bosh_cli-1.2788.0-linux-x86_64.tar.gz
bosh_cli-1.2788.0-osx.tar.gz
```