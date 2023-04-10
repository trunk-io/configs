<!-- trunk-ignore(markdownlint/MD041) -->
<p align="center">
  <a href="https://docs.trunk.io">
    <img height="128" src="https://static.trunk.io/assets/vscode_icon.png" />
  </a>
</p>
<h2 align="center">Trunk Configs</h2>
<h3 align="center">Clean default configs for linters, formatters, and more</h2>
<p align="center">
  <a href="https://marketplace.visualstudio.com/items?itemName=Trunk.io">
    <img src="https://img.shields.io/visual-studio-marketplace/i/Trunk.io?logo=visualstudiocode"/>
  </a>
  <a href="https://slack.trunk.io">
    <img src="https://img.shields.io/badge/slack-slack.trunk.io-blue?logo=slack"/>
  </a>
  <a href="https://docs.trunk.io">
    <img src="https://img.shields.io/badge/docs.trunk.io-7f7fcc?label=docs&logo=readthedocs&labelColor=555555&logoColor=ffffff"/>
  </a>
  <a href="https://api.securityscorecards.dev/projects/github.com/trunk-io/configs">
    <img src="https://api.securityscorecards.dev/projects/github.com/trunk-io/configs/badge"/>
  </a>
</p>

> 🎉 [Trunk][trunk] is a constantly evolving product. We'd appreciate your feedback - stop by the
> [Trunk Community Slack](https://slack.trunk.io/) and let us know what you think. Thanks!

Here are the default **configuration files, linters, and actions** that we turn on in all of our own
repositories during development. Every setting has been carefully scrutinized to optimize our own
workflow. Feel free to import them for your own use, or turn them all on by adding the following to
your `.trunk/trunk.yaml`:

```yaml
plugins:
  sources:
    - id: configs
      uri: https://github.com/trunk-io/configs
      ref: v0.0.1
```

Included in this repository is a set of `exported_configs`. Simply source this repository and you
will automatically have access to all of the config files enumerated in [plugin.yaml](./plugin.yaml)
whenever you run `trunk check`. You can override these configs by adding your own file with the same
name to `.trunk/configs`.

For more information about [plugins](https://github.com/trunk-io/plugins) and Trunk config merging,
check out our [docs](https://docs.trunk.io)!

## Three tips for successful linter configs

### 1. Turn off formatting errors, use autoformatters instead

Nobody wants to hear about every missing space as a separate lint error. Don't run prettier via
eslint. Don't run flake8 formatting errors instead of autoformatting with
[black](https://github.com/psf/black), etc. The same theme rings true with most language linter
setups.

### 2. Put your linter configs in standalone files

Sure, you can embed your eslint settings in `package.json` or your flake8 settings in `setup.cfg`,
but please don't. It's just good separation of concerns. It's easy for other people to find the
config options in standalone files, if you stop using a linter it's easy to delete the config, it's
easy to look up the format of a config or get editor autocompletion (they often have schemas on
schemastore.org), everything is easier.

### 3. Keep your linter configs in one place in .trunk/configs

To override any of the config files exported from this repo, simply include a config file with the
same name in your `.trunk/configs` directory or in the root of your repo. Trunk will take care of
the rest.

## Why you should spend more time on linter configs

An ounce of prevention is worth a pound of cure. Running more well configured linters will reduce
your bugs, increase consistency, reduce security vulnerabilities, and increase your overall speed.
Spend a little time now, reap the rewards forever.

## Notes

### `.editorconfig`

Always have a `.editorconfig` file, not only for users of your repo using editors, but also some
linters use the settings in `.editorconfig`. For example `shfmt` uses it to figure out indentation,
and `prettier` will also respect it as a fallback to its own config (though that is undocumented).

## What's the best way to run linters and formatters?

[Trunk][trunk] 🎉 ([docs](https://docs.trunk.io) •
[vscode extension](https://marketplace.visualstudio.com/items?itemName=trunk.io) •
[github action](https://github.com/trunk-io/trunk-action))

## Contributing

Think there's a better setup for one of these linters? Put up a PR and let's see it! Also happy to
see contributions for linters we haven't covered here in our
[plugins](https://github.com/trunk-io/plugins) repo.

[trunk]: https://trunk.io/
