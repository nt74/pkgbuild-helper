# pkgbuild-helper
Helpful guide on how to generate PKGBUILD for Arch Linux distributions

### Make sure to read: 

[Category:Package development](https://wiki.archlinux.org/title/Category:Package_development),
[Creating packages](https://wiki.archlinux.org/title/Creating_packages),
[Arch package guidelines](https://wiki.archlinux.org/index.php/Arch_package_guidelines),
[AUR submission guidelines](https://wiki.archlinux.org/title/AUR_submission_guidelines)

### For license:

[Arch package guidelines#licenses](https://wiki.archlinux.org/title/PKGBUILD#license)

## Generate the .SRCINFO
```
makepkg --printsrcinfo > .SRCINFO
```

### Checking package sanity
```
namcap PKGBUILD
```
```
namcap pkgname.pkg.tar.zst
```

### Options functions
```
options=(
  # Default enabled options (use ! to disable)
  'strip'      # Strip symbols from binaries
  'docs'       # Keep documentation files
  'emptydirs'  # Keep empty directories
  'zipman'     # Compress manual pages
  'ccache'     # Use ccache during build
  'distcc'     # Use distcc during build
  'buildflags' # Use default CFLAGS/CXXFLAGS
  'makeflags'  # Use default MAKEFLAGS

  # Default disabled options (remove ! to enable)
  '!debug'      # Add debugging flags
  '!libtool'    # Leave libtool (.la) files
  '!staticlibs' # Leave static library (.a) files
  '!lto'        # Enable link-time optimization
  '!upx'        # Compress executables with UPX
)
```

## First run git needs to set the global username information:
```
git config --global user.email "you@example.com"
```
```
git config --global user.name "Your Name"
```
```
git config --global init.defaultBranch main # (trunk, development)
```

To generate new md5sums run the command updpkgsums:
```
sudo pacman -S pacman-contrib
```

## How to upload to AUR repository
1. Create an account
2. Add your ssh public key
3. ```git -c init.defaultbranch=master clone ssh://aur@aur.archlinux.org/pkgbase.git```
4. ```cd package-git```
5. ```cp PKGBUILD .SRCINFO (from your package)```
6. ```git add PKGBUILD .SRCINFO```
7. ```git commit -m "Initial version"```
8. ```git push```
