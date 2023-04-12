# Contribution

If you see any room for improvement in these configuration files, or see the potential to add any
more default configs, feel free to make a pull request to this repo! Note, however, that this
configuration is currently optimized for our organization's workflow. If you'd like to specify your
own overrides or configuration for your own process, feel free to make a fork and source it as a
plugin of your own.

For more information on how plugins are sourced, see the overview below:

## Config Merging Overview

When using trunk, you can merge several sets of configuration files with a `trunk.yaml` schema.
Config merging proceeds as follows:

1. Plugins sourced in `.trunk/trunk.yaml` (and `.trunk/user.yaml`), in the order that they are
   sourced. The [`trunk`](https://github.com/trunk-io/plugins) plugin is implicitly sourced first.
2. Your `.trunk/trunk.yaml` file, complete with a cli version and any definitions or enables.
3. Optionally, `.trunk/user.yaml`, a git-ignored file where users can provide their own overrides.

Additionally, any files enumerated in the lint `exported_configs` section are symlinked from their
relevant plugin into the root of the workspace when an applicable linter is run with `trunk check`.

The config fields for plugins sources and cli version are not merged from plugins.

## Upgrading

You can run `trunk upgrade` to upgrade the trunk CLI, any plugins, and any linters that you are
using.
