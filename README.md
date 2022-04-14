# Cabal Utils

Various utilities for Cabal a system for building and packaging Haskell libraries

## Uninstall cabal packages (step by step)
* Remove main packages
> if there are any dependent packages, is gonna give an error telling that those will be broken, then add `--force` to remove
```sh
./ghc-pkg-unregister my-package-1.2.0 some-package-1.0.0 ...
```

* Get all broken dependent packages
```sh
./ghc-pkg-check
```

* Remove all broken packages
```sh
./ghc-pkg-check --simple-output | xargs ./ghc-pkg-unregister --force
```
> run `./ghc-pkg-check` again to see if there are no broken packages 

* Clean associated libs 
> run only if you want save disk resources
```sh
./cabal-gc -r
```
