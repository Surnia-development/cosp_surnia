COSP Pie for Surnia
=======================

Current Status
--------------

What's working?
 - Unknown.

What's not working?
 - Unknown.

Download
--------

@ElDainosor's LineageOS builds are available [here](https://mega.nz/#F!3F9CTSrQ!ZBLcFw1Mh_47FdxiZ2LYyg!uYlmhBKT).
My COSP builds will be up [here](https://t.me/romdelivery).

Build Instructions
------------------

#### Automatic compilation

Download the script

	wget -q https://raw.githubusercontent.com/FacuM/shellscripts/master/android/buildrom/examples/cosp_surnia.sh -O ~/cosp_surnia.sh

Edit the variables at the top to your liking

	vi ~/cosp_surnia.sh   or   nano ~/cosp_surnia.sh

![Variables to edit](https://i.imgur.com/6gqS7sn.png)

Then begin the build, syncing source and just building what you need.

	. ~/cosp_surnia.sh

If you want to remove the old source, you can run it like this.

	. ~/cosp_surnia.sh reset

Or you can just clean the old compilation and build it all again.

	. ~/cosp_surnia.sh clobber

#### Manual compilation

Create a build directory

	mkdir -p cosp
	cd cosp

Initialize your local repository using the COSP trees:

	repo init -u https://github.com/cosp-project/manifest -b pie

Now move your magic wand
	
	mkdir -p .repo/local_manifests
	wget -O .repo/local_manifests/surnia.xml https://github.com/Surnia-development/cosp_surnia/raw/master/surnia.xml

Do this everytime before every sync for tracking changes.

Then to sync up:

     repo sync  --force-sync --force-broken --current-branch --no-tags --no-clone-bundle --optimized-fetch --prune -j$(nproc --all)

Do this everything after sync for applying patches.	

Now start the build...

	. build/envsetup.sh 
	lunch cosp_surnia-userdebug
	brunch surnia   or   mka bacon

Please see the [LineageOS WIKI](https://wiki.lineageos.org/) for further information.

Resources
---------

- Understanding bash sourcing: [How to detect if a script is being sourced - Stack Overflow](https://stackoverflow.com/questions/2683279/how-to-detect-if-a-script-is-being-sourced)
