# techcv-products

`techcv-products` is an aggregate repository for `techcv-*` projects managed as Git submodules.

## Current submodules

- `techcv-app`
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

## Local Codex skills

Project-local Codex skills live under `.codex/skills`.

- `go-best-practices`: Go code review and editing guidance for `.go` and `go.mod` changes

Use a skill explicitly by naming it in a prompt, for example: `$go-best-practices`.
