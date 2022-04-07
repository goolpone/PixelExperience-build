# Pixel Experience #

### Donate ###
If you find my work useful, consider making a donation: https://www.paypal.me/giuseppebitonti

### 1. Installing Repo ###

```bash
# Make a directory where Repo will be stored and add it to the path
$ mkdir ~/bin
$ PATH=~/bin:$PATH

# Download Repo itself
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

# Make Repo executable
$ chmod a+x ~/bin/repo
```

### 2. Initializing Repo ###

```bash
# Create a directory for the source files
# This can be located anywhere (as long as the fs is case-sensitive)
$ mkdir PixelExperience && cd PixelExperience

# Install Repo in the created directory
$ repo init --depth=1 -u git://github.com/goolpone/PixelExperience-build.git -b eleven-plus
```

This is what you will run each time you want to pull in upstream changes. Keep in mind that on your
first run, it is expected to take a while as it will download all the required Android source files
and their change histories.

```bash
# Let Repo take care of all the hard work
$ repo sync -c -j$(nproc --all) --no-clone-bundle --no-tags --quiet
$ ln -s .repo/manifests/scripts/addVendor.sh && ./addVendor.sh
```

### 3. Building ###

```bash
# Go to the root of the source tree...
$ cd PixelExperience
# ...and run to prepare our devices list
$ . build/envsetup.sh
# ... Choose a target
$ lunch lineage_a5y17lte-userdebug
# ... and Build the code
$ mka bacon -j$(nproc --all)
```
