# Mac OS Install

## Prerequisites:

* A computer with MacOS Sonoma (14.0) or later&#x20;
* At least 2 GB of free space. (Only \~60MB will be used for LDCAD; the rest will be used for emulation.)
* A computer with the Apple Silicon Chip Series (M1 or later)

## Downloading LDCAD

### [Click Here](https://drive.google.com/file/d/1f1gOuD8uoioyy1mCQ4CL0tE-Fv84Yaz8/view?usp=sharing)

Click on the link, and download the zip file.

Once downloaded, open the zip file.

### Installing Whisky

### [Click Here](https://getwhisky.app/)

Click on the link, and download the installer. Once installed, open the app.

#### Setting up Whisky

On the **top right corner**, click the **+** symbol. Name the "bottle" anything. I use "LDCad". If this is your first time using Whisky, creating the bottle may take some time.

Once your bottle is created, go into the **lower right hand corner** and click the **"Open C: Drive** button. Here, drag your LDCadVEX folder into drivec > Users > crossover > Desktop.

Now, go back to Whisky and click the **Run...** button in the lower right hand corner. Select the **LDCadVEX.exe** file that is in the folder you just now moved. After a while, you will see an installation prompt. Follow through.

Once you are done installing, it will ask you to select a library. Go into the same LDCadVEX folder again, and select the folder called **Library**, and then open.

## Changing the font

Once you enter the program, you'll see a lot of X's

<figure><img src="../.gitbook/assets/Screenshot 2026-01-05 at 10.44.20 PM.png" alt="" width="375"><figcaption></figcaption></figure>

This is because the program is looking for a font called "Verdana." However, our fonts folder is empty, because of a totally clean install of Windows.

**We will replace this with the GNU Free Font FreeSans.**

1. Close LDCad.Download the FreeFont package from [this link](http://ftp.gnu.org/gnu/freefont/freefont-ttf.zip), and extract the resulting zip file.&#x20;
2. Within the extracted contents, locate the file `FreeSans.ttf` inside the `sfd` directory.
3. Again, find the drive\_c folder through Whisky.&#x20;
4. Then navigate over to the `windows` folder, and then find the `Font` folder. This is the Windows font folder where we'll place the font file.The drive\_c folder is the same one we opened in the first part of the installation.
5. Copy the `FreeSans.ttf` file into the Windows font folder.

Make a second copy of `FreeSans.ttf` in the Windows font folder, and rename the new copy to `verdana.ttf` .

There should now be two files in the Windows font folder, `FreeSans.ttf` and `verdana.ttf` . These are the two font files LDCad expects to find in this directory. If you want to use a font other than FreeSans, you can, just make sure you end up with two .ttf files in the Fonts directory with the exact names `FreeSans.ttf` and `verdana.ttf` . LDCad will use `verdana.ttf` for almost everything and `FreeSans.ttf` for only the small "part info box" that appears when you select a part.



Now, you can reopen LDCad. To do this, go to Whisky > Pin program, and find you LDCadVEX.exe file in the Desktop folder (in the user folder crossover). Then, select it to pin. Name it whatever you want.

Now, right click the newly pinned LDCad, and click run. Everything should look correct now.



## Troubleshooting / FAQ

<details>

<summary><strong>My parts show up as blank items/Red plus's.</strong></summary>

This is because you haven't set the correct library, or the correct shadow.

Many people download the CAD files from the official VEX website, but that folder isn't compatible with LDraw. You need to use the "Library" folder found in this guide. (the gDrive) Another possibility is that you didn't set your shadow.&#x20;

Usually it should set it by itself. In LDCad, go into the "Prefs" tab in the top, and then click LDraw, then `Search (library) paths ...`. Here, make sure your LDCadVEX Library folder is an "Official" library. To add the shadow: Open your c\_drive, then go into the users/crossover folder, and then go to your %AppData% folder, and into Roaming. Find a folder called LDCadVEX, and open shadow > offLib. Inside this folder, you'll see 2 files.&#x20;

One of them in offLibShadow.csl. Go back to LDCad, and in the shadow box, click browse folder, and find the `offLib` **folder**. (you will NOT see the csl file, as LDCad is very old and the code is kinda crooked.) Press open. Now, **manually** type in `\offLibShadow.csl` after the `offLib` folder. Then, click Accept.&#x20;

Close and reopen LDCad

</details>

<details>

<summary><strong>My text is showing as all XXXXXX's</strong></summary>

Follow the guide again.

</details>

If you have any other issues please DM @ruiguan on Discord.
