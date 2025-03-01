# haskell-flake (forked)

Manage Haskell projects conveniently with Nix

<img src="./doc/haskell-flake.webp" width=100 />

## Ethics of this fork

Before you start, please read [CONDUCT.md](./CONDUCT.md), which explains the
motivations for this fork and cautions about the externally linked documentation
for this project, specifically on https://srid.ca.

## Project goals

There are [several ways](https://nixos.asia/en/haskell) to manage Haskell packages using [Nix](https://nixos.asia/en/nix) with varying degrees of integration.  `haskell-flake` makes Haskell development, packaging and deployment with Nix flakes a lot [simpler](https://community.flake.parts/haskell-flake/start#under-the-hood) than other existing approaches.  This project is set up as a modern [`flake-parts`](https://flake.parts/) module to integrate easily into other Nix projects and shell development environments in a lightweight and modular way.

To see more background information, guides and best practices, visit https://community.flake.parts/haskell-flake

Caveat: `haskell-flake` only supports the Haskell package manager [Cabal](https://www.haskell.org/cabal/),
so your project must have a top-level `.cabal` file (single package project) or a `cabal.project` file
(multi-package project).

## Getting started

The minimal changes to your `flake.nix` to introduce the `haskell-flake` and [`flake-parts`](https://flake.parts/) modules will look similar to:

```nix
# file: flake.nix
{
  inputs = {
    ...
    flake-parts.url = "github:hercules-ci/flake-parts";
    haskell-flake.url = "github:shajra/haskell-flake";
  };

  outputs = inputs:
    inputs.flake-parts.lib.mkFlake { inherit inputs; } {
      systems = [ "x86_64-linux", ... ];
      imports = [
        ...
        inputs.haskell-flake.flakeModule
      ];
      perSystem = { self', system, lib, config, pkgs, ... }: {
        haskellProjects.default = {
          # basePackages = pkgs.haskellPackages;

          # Packages to add on top of `basePackages`, e.g. from Hackage
          packages = {
            aeson.source = "1.5.0.0"; # Hackage version
          };

          # my-haskell-package development shell configuration
          devShell = {
            hlsCheck.enable = false;
          };

          # What should haskell-flake add to flake outputs?
          autoWire = [ "packages" "apps" "checks" ]; # Wire all but the devShell
        };

        devShells.default = pkgs.mkShell {
          name = "my-haskell-package custom development shell";
          inputsFrom = [
            ...
            config.haskellProjects.default.outputs.devShell
          ];
          nativeBuildInputs = with pkgs; [
            # other development tools.
          ];
        };
      };
    };
}
```

`haskell-flake` scans your folder automatically for a `.cabal` or `cabal.project` file.
In this example an imaginary `my-haskell-package.cabal` project is used.

To see in more detail how to use `haskell-flake` in a realistic Haskell project
with several other development tools, take a look at
the corresponding [Haskell single-package project Nix template](https://github.com/shajra/haskell-template) and
this [Haskell multi-package project Nix example](https://github.com/srid/haskell-multi-nix).

## Documentation

https://community.flake.parts/haskell-flake

## Release

Be aware that for now the `main` branch of this fork will rebase against
upstream development. Though an inconvenience for collaboration, this makes it
easier to maintain this work. End user consumption through flakes should be
unaffected.
