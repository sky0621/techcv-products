# techcv-products

`techcv-products` is an aggregate repository for `techcv-*` projects managed as Git submodules.

## Current submodules

- `techcv-design`

## Clone

```sh
git clone --recursive git@github.com:sky0621/techcv-products.git
```

If you already cloned the repository without submodules:

```sh
git submodule update --init --recursive
```

## Add a new submodule

Add each `techcv-*` repository at the repository root:

```sh
git submodule add <repository-url> <directory-name>
```

After adding or updating submodules, commit both the submodule pointer and `.gitmodules`.
