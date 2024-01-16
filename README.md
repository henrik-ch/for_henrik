# Current snapshot of system setup

A snapshot of my up-to-date current system setup for henrik to use as an example.

## Cloning instructions

(Git submodule: just a way to refer to another repository inside this repository.)

To clone with the [`system`](https://github.com/bzm3r/system) repo as a submodule:
```
git repo clone https://github.com/bzm3r/for_henrik --recurse-submodule
```

To clone without `system`:
```
git repo clone https://github.com/bzm3r/
```

## Explanation

The structure is:
```
/for_henrik
    /system
    mk-symlink
    entry-point.nix
    README.md
```

* `entry-point.nix` has only one job: to "declaratively set" which machine you're building for. (For me: desktop = "d", laptop = "l").

* `mk-symlink` is a bash script which makes a symlink copy of `system/home` into your home directory, in order to "initialize" home. In the past, I had more differences between desktop and laptop, but as I have been improving, I have been finding that most of these are non-sensical/unnecssary. Today there are only some differences related to setting up `sway`. Note that we do this because we do not care to use `home-manager`. So you could happily skip it, if you just want to use the "default settings" for everything. It should not affect the actual system.

* `system`, the actual heart of all of this, is the nixos system configuration you're familiar with. It contains the bash script `rebuild` which refers to `mk-symlink` and `entry-point.nix`.

**Note:** this setup is less than ideal, I am working on cleaning it up...but hopefully for now this explains some of the warnings you receive when running `system/rebuild`!

