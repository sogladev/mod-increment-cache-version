# AzerothCore Module Increment Cache Version

- Latest build status with azerothcore:

[![Build Status](
https://github.com/sogladev/mod-increment-cache-version/actions/workflows/core-build.yml/badge.svg?branch=master)](https://github.com/sogladev/mod-increment-cache-version)

This module for [AzerothCore](http://www.azerothcore.org) automatically increments the cache version on server startup, ensuring clients always have up-to-date cache data.

> Something I noticed is not common knowledge is that the client has a version associated with its cache. If the server cache version does not match the client, the client will automatically clear its cache.
>
> You can have the server increment this version each server restart very trivially. For example: https://i.imgur.com/3KYY9fJ.png
>
> Doing this, you no longer need to worry about manually clearing the cache or players having out of date caches.
> -- <cite>stoneharry, WoW Modding Community https://discordapp.com/channels/407664041016688662/1301592845978833028/1301592845978833028</cite>

### ⚠️ Warning

To use this module, ensure that the `ClientCacheVersion` setting in `worldserver.config` is set to its default value, `0`. Otherwise, the cache id from DB will be overwritten by this config.

- Configuration location: [`worldserver.conf.dist` on GitHub](https://github.com/azerothcore/azerothcore-wotlk/blob/88db984e52b2c0daf533c6a1ef769a3d50d7347c/src/server/apps/worldserver/worldserver.conf.dist#L965)

## How to install
https://www.azerothcore.org/wiki/installing-a-module

1. Requires source recompilation
2. Modify the config to easily disable in the future.
  Found in `/etc/modules`, copy `.conf.dist` to `.conf`

## How to disable
Disable `IncrementCacheVersion.Enable` in `.conf`

or

Set `ClientCacheVersion` setting in `worldserver.config`

## How to remove

1. Remove `mod-increment-cache-version` folder
2. Restore cache version ```UPDATE `version` SET `cache_id`=XX;```

## How to create your own module

1. Use the script `create_module.sh` located in [`modules/`](https://github.com/azerothcore/azerothcore-wotlk/tree/master/modules) to start quickly with all the files you need and your git repo configured correctly (heavily recommended).
1. You can then use these scripts to start your project: https://github.com/azerothcore/azerothcore-boilerplates
1. Do not hesitate to compare with some of our newer/bigger/famous modules.
1. Edit the `README.md` and other files (`include.sh` etc...) to fit your module. Note: the README is automatically created from `README_example.md` when you use the script `create_module.sh`.
1. Publish your module to our [catalogue](https://github.com/azerothcore/modules-catalogue).

