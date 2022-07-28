# jsr-risotto

jsr-risotto is a minimalist, responsive [hugo](https://gohugo.io) theme inspired by terminal ricing aesthetics. It's based on [risotto](https://github.com/joeroe/risotto) and customized by [Jacana](https://jacana.io).

![Screenshot of the risotto theme](https://raw.githubusercontent.com/joeroe/risotto/master/images/screenshot.png)

## Install

The easiest way to install the theme is to clone this repository into your site's `themes` directory:

```shell
git clone https://gitlab.com/jacana-security-research/jsr-risotto.git themes/jsr-risotto
```

If your site is already a git repository, you can add the theme as a submodule instead:

```shell
git submodule add https://gitlab.com/jacana-security-research/jsr-risotto.git themes/jsr-risotto
```

## Configure

To use the theme, add `theme = jsr-risotto` to your site's `config.toml` or `config.yaml`.

See `exampleSite/config.toml` for the theme-specific parameters you need to add to your site's `config.toml` or `config.yaml` to configure the theme.

## Update

If you installed the theme using `git clone`, pull the repository to get the latest version:

```shell
cd themes/jsr-risotto
git pull
```

Or, if you added it as a git submodule:

```shell
git submodule update --remote
```

