CarbonROM 7.0 for Surnia
=======================

Current Status
--------------

What's working?
 - Unknown.

What's not working?
 - Unknown.

Download
--------

@ElDainosor's LineagOS builds are available [here](https://mega.nz/#F!3F9CTSrQ!ZBLcFw1Mh_47FdxiZ2LYyg!uYlmhBKT).
My CarbonROM builds will be up [here](https://t.me/romdelivery).

Build Instructions
------------------

#### Automatic compilation

Download the script

	wget -q https://raw.githubusercontent.com/FacuM/shellscripts/master/android/buildrom/examples/carbon_surnia.sh -O ~/carbon_surnia.sh

Edit the variables at the top to your liking

	vi ~/carbon_surnia.sh   or   nano ~/carbon_surnia.sh

![Variables to edit](https://i.imgur.com/6gqS7sn.png)

Then begin the build, syncing source and just building what you need.

	. ~/carbon_surnia.sh

If you want to remove the old source, you can run it like this.

	. ~/carbon_surnia.sh reset

Or you can just clean the old compilation and build it all again.

	. ~/carbon_surnia.sh clobber

#### Manual compilation

Create a build directory

	mkdir -p carbon
	cd carbon

Initialize your local repository using the CarbonROM trees:

	repo init -u https://github.com/CarbonROM/android.git -b cr-7.0

Now move your magic wand
	
	mkdir -p .repo/local_manifests
	wget -O .repo/local_manifests/surnia.xml https://github.com/Surnia-development/carbon_surnia/raw/master/surnia.xml

Do this everytime before every sync for tracking changes.

Then to sync up:

     repo sync  --force-sync --force-broken --current-branch --no-tags --no-clone-bundle --optimized-fetch --prune -j$(nproc --all)

Do this everything after sync for applying patches.	

Now start the build...

	. build/envsetup.sh 
	lunch carbon_surnia-userdebug
	brunch surnia   or   mka otapackage

Please see the [LineageOS WIKI](https://wiki.lineageos.org/) for further information.

Resources
---------

- Understanding bash sourcing: [How to detect if a script is being sourced - Stack Overflow](https://stackoverflow.com/questions/2683279/how-to-detect-if-a-script-is-being-sourced)
