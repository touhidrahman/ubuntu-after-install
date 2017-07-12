## Upgrade AUR packages
`yaourt -Syua`

## Remove a package 
`sudo pacman -Rs package_name`

## List all orphan packages with no dependencies
`sudo pacman -Qdt`

## Remove unused dependencies
`sudo pacman -Rsn $(pacman -Qdtq)`

## Get a list of installed packages
`sudo pacman -Q

## Cleaning orphan packages from the system
`sudo pacman -Rsn $(pacman -Qdtq)

## Cleaning the cache
`sudo pacman -Sc

## Get a full package list with versions.
**This will create a file called pacman.laptop in your home folder.**

`sudo pacman -Q > ~/pacman.laptop`

## Download a package without installation
`sudo pacman -Sw package_name`

## Install a downloaded or a local package
`sudo pacman -U /package_path/package_name.pkg.tar.xz`

## You can also use the URL:
`sudo pacman -U http://www.examplepackage/repo/examplepkg.tar.xz`
