# pkgbuild-helper
Helpful guide on how to generate PKGBUILD for Arch Linux distributions
Make sure to read 
https://wiki.archlinux.org/index.php/Arch_package_guidelines

https://wiki.archlinux.org/title/AUR_submission_guidelines

To generate the .SRCINFO type makepkg --printsrcinfo > .SRCINFO

First run git needs to set the global username information: <br />
git config --global user.email "you@example.com" <br />
git config --global user.name "Your Name"

To generate new md5sums run the command updpkgsums (requires package pacman-contrib)

How to upload to AUR repository
1. Create an account
2. Add your ssh public key
3. git clone ssh://aur@aur.archlinux.org/package-git.git
4. cd package-git
5. cp PKGBUILD .SRCINFO (from your package)
6. git add PKGBUILD .SRCINFO
7. git commit -m "Initial version"
8. git push
