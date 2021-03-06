# Node Webkit Github Auto-Updater

This is a demo of how you can auto-update a Node Webkit installation "on-the-fly"

We're auto-updating from GitHub but you could adapt this idea to get updated code from pretty-much anywhere...

## How it works

We're using a zipped 'package.nw" for distribution - but this would work with source folders too...

We've uploaded all our source-code to GitHub and released one round of changes (Version TWO)

The demo download (below) contains the support files but is Version One of our source - so when runs it should auto-update to the newer version

## Specifics...

We scrape GitHub to see if our locally-stored version differs from the latest 'release tag' on GitHub

If it does, we download the source for that release (as a tar.gz because Node has no reliable native unzip I can find), unpack it, remove the 'header' directory GitHub inserts and re-archive/zip that and overwrite "package.nw" (all in-memory via streams/pipe)

We can then restart the client and it will pickup the new code

Obviously you can customize this to check/when to update/when to restart the client/to tell the user what's going on!

## ToDo

If someone who knows how to make NPM packages wants to convert this into that format - that'd be great...

## What this doesn't do

This approach can't update the platform-specific Node Webkit executables or their support dlls/dats because they're in-use when the application is running

Compared to code updates, these change infrequently and you can always attached zip/tar archives to those releases as-required (and prompt people within your code to download them?)

## Dependencies

We're using node-tar (to unpack the GitHub source), node-archiver (to re-pack it) and requests (because GitHub uses redirects and we want a stream)

## Demo Download

Windows

[nwgu-0.01.zip](https://github.com/shrewdlogarithm/node-webkit-auto-update-demo/releases/download/0.01/nwgu.zip)

Linux

[nwgu-0.01.tar.gz](https://github.com/shrewdlogarithm/node-webkit-auto-update-demo/releases/download/0.01/nwgu.tar.gz)

