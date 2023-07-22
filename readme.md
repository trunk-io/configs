# Opinionated Trunk.io Plugin

[![docs](https://img.shields.io/badge/-docs-darkgreen?logo=readthedocs&logoColor=ffffff)][docs]
[![slack](https://img.shields.io/badge/-slack-611f69?logo=slack)][slack]
[![vscode](https://img.shields.io/visual-studio-marketplace/i/trunk.io?color=0078d7&label=vscode&logo=visualstudiocode)][vscode]

This plugin has default **configuration files, linters, and actions** that we turn on in all of our
own repositories during development. Every setting has been carefully scrutinized to optimize our
own workflow. Feel free to import them for your own use by running:

```bash
trunk plugins add https://github.com/trunk-io/configs
```

Included in this repository is a set of `exported_configs`. Simply source this repository and you
will automatically have access to all of the config files enumerated in [plugin.yaml](./plugin.yaml)
whenever you run `trunk check`. You can override these configs by adding your own file with the same
name to `.trunk/configs`.

For more information about [plugins](https://github.com/trunk-io/plugins) and Trunk config merging,
check out our [docs][docs].

[slack]: https://slack.trunk.io
[docs]: https://docs.trunk.io
[vscode]: https://marketplace.visualstudio.com/items?itemName=Trunk.io
