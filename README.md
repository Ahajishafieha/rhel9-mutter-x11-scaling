# rhel9-mutter-x11-scaling

Port a patch to add fractional scaling support to mutter in x11 session for distributions based on RHEL 9.

Thanks to Marco Trevisan for providing the patch for [Ubuntu](https://salsa.debian.org/gnome-team/mutter/-/blob/ubuntu/master/debian/patches/ubuntu/x11-Add-support-for-fractional-scaling-using-Randr.patch).

## Build and install

### Pre-built rpm
Grab the .rpm from the release page in this repository and install via dnf:

`# dnf install /path/to/mutter-<version>.patched.<dist>.<arch>.rpm`

### Manually building from source code
Grab the mutter .src.rpm from your distribution's repository. extract it to /home/$USER/rpmbuild/SOURCES/ and replace the mutter.spec file from the one provided in this repository and put the patch next to other patches.
then run rpmbuild to create rpm package:

`$ rpmbuild -bb mutter.spec`

once the build is completed you can install using dnf:

`# dnf install /home/$USER/rpmbuild/RPMS/<arch>/mutter-<version>.patched.<dist>.<arch>.rpm`

## Usage
After installation log out and log back in to your gnome session and enable x11 scaling:

`$ gsettings set org.gnome.mutter experimental-features "['x11-randr-fractional-scaling']"`

