<!-- trunk-ignore(markdownlint/MD041) -->
<p align="center">
  <a href="https://docs.trunk.io">
    <img height="128" src="https://static.trunk.io/assets/vscode_icon.png" />
  </a>
</p>
<h2 align="center">Trunk Configs</h2>
<h3 align="center">Clean default configs for linters, formatters, and more</h2>
<p align="center">
  <a href="https://trunk.io">
    <img src="https://github.com/trunk-io/trunk-action/actions/workflows/pr.yaml/badge.svg"/>
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=Trunk.io">
    <img src="https://img.shields.io/visual-studio-marketplace/i/Trunk.io?logo=visualstudiocode"/>
  </a>
  <a href="https://slack.trunk.io">
    <img src="https://img.shields.io/badge/slack-slack.trunk.io-blue?logo=slack"/>
  </a>
  <a href="https://docs.trunk.io">
    <img src="https://img.shields.io/badge/docs.trunk.io-7f7fcc?label=docs&logo=readthedocs&labelColor=555555&logoColor=ffffff"/>
  </a>
</p>

> 🎉 Trunk is in beta. We'd appreciate your feedback - stop by the
> [Trunk Community Slack](https://slack.trunk.io/) and let us know what you think. Thanks!

Here are some **simple and ultra-clean default configs for linters, formatters, and more**. Every
character has been scrutinized to create the finest dotfiles in the galaxy. Enjoy 😎

PRs are welcome!

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

### 3. Put your linter configs at the root of your repo

Whether you have a monorepo with language subdirectories or a microrepo with a single source file,
by sticking all of your lint configuration at the root, no matter where someone adds new files,
they're covered. All too often, large swaths of a codebase go unlinted because linter configs didn't
cover some directories.

## Why you should spend more time on linter configs

An ounce of prevention is worth a pound of cure. Running more well configured linters will reduce
your bugs, increase consistency, reduce security vulnerabilities, and increase your overall speed.
Spend a little time now, reap the rewards forever.

## Notes

### `.editorconfig`

Always have a `.editorconfig` file, not only for users of your repo using editors, but also some
linters use the settings in `.editorconfig`. For example `shfmt` uses it to figure out indentation,
and `prettier` will also respect it as a fallback to its own config (though that is undocumented).

### `.clang-format`

Clang-format can format a bunch of languages, but we prefer `prettier` on languages they both cover.
To lint additional languages, you need a section for that language as is shown in this
`.clang-format`. Note there's a section for proto: Clang-format can autoformat proto files too!
Cool.

This config is yaml, but it's kind of multiple yaml files stacked into the same file. Bad config
design, but a good tool!

### `.flake8`

We turned off all the formatting categories because [black](https://github.com/psf/black) handles
autoformatting. No one should be hearing about formatting issues one space at a time. This is a
theme across many linters.

Black itself has a black-compatible flake8 config
[here](https://github.com/psf/black/blob/main/.flake8), however it keeps flake8 formatting errors
_on_. If you've autoformatted with black, you won't have any flake8 errors with their config, but
really you should be gating your CI on both black and flake8 (with [trunk](https://trunk.io/)), and
it's much nicer to hear that you just need to autoformat your file with black, not hear about every
missing space as a different lint error.

### `.clang-tidy`

Clang-tidy has one of the more annoying configs around. Tidy has ~50 rules which are aliases of
other rules. If you don't disable them, you end up getting duplicate results _and_ tidy takes
longer.

Also, the config is yaml, but the `Checks` key takes a string which is a comma separated list
instead of a yaml list. :( The comment blocks at the top describe what we've turned on/off and why.

### `.markdownlint.yaml`

We turned off all formatting categories which are handled by prettier. If you use
trunk](https://trunk.io/), you'll just see that your file needs to be autoformatted, not every
instance of missing whitespace in your markdown.

### `.shellcheckrc`

This config turns on as much as possible, but relies on sourcing other scripts always relative to
the current script's directory. If you want to turn off checking related to `source`, you could add:

```text
disable=SC1090
disable=SC1091
```

## What's the best way to run linters and formatters?

[Trunk](https://trunk.io/) 🎉 ([docs](https://docs.trunk.io) •
[vscode extension](https://marketplace.visualstudio.com/items?itemName=trunk.io) •
[github action](https://github.com/trunk-io/trunk-action))

## Contributing

Think there's a better setup for one of these linters? Put up a PR and let's see it! Also happy to
see contributions for linters we haven't covered here.
