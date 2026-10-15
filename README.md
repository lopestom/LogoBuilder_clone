# Before taking any action - explaining the reason/motivation
Many users familiar with this software, especially Mediatek users, know how valuable it was back then and how well it worked.
However, it was only available for Windows.

Nowadays, finding something similar that works the way it did is very difficult, even on Linux. There are always limitations since the source code has never been released.
But there's always someone who tries and does something interesting, getting close, but I can say that if it works, that's enough. There are about 4 to 7 authors who took the idea and made their projects for Linux. Some no longer work and others (maybe only 2) don't work for all resolutions and devices.

Since the LogoBuilder software is free, but without updates since 2015, and reading about OER, I thought: Here's an opportunity to test if it works and try something from Windows for Linux.

Nothing here deviates from respect, citations, and references, since in addition to being a case study with an exclusively educational vision/purpose, with the objective of demonstrating how reverse engineering technology using AI worked to "revive" a software over 10 years old to run on Linux.
Since I didn't want to go further, some things like links, direct image selection by mouse, and texts in the information boxes ended up looking strange.

For these reasons, nothing has been altered in relation to the words, phrases, pictures or names of the original software.

You can find the [REA](https://github.com/morluto/rea/blob/main/README.md) used in this case here, and how Claude AI was used in [this document](https://github.com/lopestom/LogoBuilder_clone/blob/Linux/BuildLogo_Claude-en_US.md).


# LogoBuilder
LogoBuilder is a Windows tool used to customize the boot logo and battery charging graphics on Android devices with a MediaTek (MTK) processor.

# Precedents / Authors
The program was developed with the support of the community from the china-iphone.ru or in [china-devices.com](https://web.archive.org/web/20141003030955/china-devices.com/Thread-MTK-boot-logo-logo-bin-Editor) forums, to whom we are very grateful. The page/website (although it is no longer online =>> The requested URL was not found on this server. That's all we know.) for the LogoBuilder software on Windows on the internet is [here](https://sites.google.com/site/kadanutilities/home/logobuilder?pli=1&authuser=0).
Created on October 24, 2012 on xda forum, it was very successful for users who wanted to modify the device's initial logo.
The author's name is [kadar](https://xdaforums.com/m/ankadnikov.4916584/), and he is listed in the upper left corner. He can be contacted (if he still responds) via email at ankadnikov@gmail.com.

Some references to consultations and research on the subject can be found at [xda](https://xdaforums.com/t/changing-boot-logo-logo-bin-program.1953726/) and [4pda](https://4pda.to/forum/index.php?showtopic=391859).

## version 1.6 - 2015/11/03
For those who wish to change the boot logo on a MediaTek-based phone, we offer a application to edit the `logo.bin` file. This file contains the initial boot image, as well as the battery icons displayed while the phone is charging while powered off. The program also assists in editing the `boot_logo` file, which contains the secondary boot image.
The program is easy to use: it unpacks the `logo.bin` file, allows you to edit the images, and then creates a new file. Two files are generated as a result: `logo.bin` (containing the new images) and an `update.zip` file for installation via Custom Recovery.

To avoid unnecessary issues, it is not recommended to use this program if you are not familiar with terms such as `logo.bin` and firmware.

## Installing / Using
1) Create a new folder (e.g., MyLogo);
2) Choose the "Create new project" option;
3) Select the appropriate logo.bin file for your device, which will be located somewhere on your computer;
4) Specify the folder you created earlier to extract the files and monitor whether it is necessary to change the format/size/resolution of each image. If everything is fine, do not change anything. If you need to change something, manually adjust the vertical bar according to the resolution;
5) Edit the necessary images (do not change the name and resolution!), usually img1.png;img2.png;img3.png and img39.png. This gives you complete editing freedom.
6) Choose the "Make" option. The logo.bin and update.zip files will be created.
7) Install the modified logo.bin file as you wish.
8) Test and modify as much as you want.
9) Done!

> [!TIP]
> 1. Note that there is a selector that can be adjusted up or down. This allows the selector to move up or down until the user sees the desired image.
> <details><summary>Example -- Click to open</summary>
> <p>
> (picture_Mod) 1,2,3
> </p>
> </details>
>
> 2.You can click on the resolution numbers to change the image if you haven't done so before or to adjust it better.

## Frequently Asked Questions
<details><summary>Q/A -- Click to open</summary>
<p>
Q: Where can I get the `logo.bin` file from my phone?
A: Honestly, you shouldn't be using this program if you don't know how to do that. But, if you decide to try anyway, here are a few options:
1) This file is usually included in the firmware image.
2) Example usage:
`dd if=/dev/logo of=/sdcard/logo.bin bs=3145728 count=1`
You can run this in a terminal or via `adb shell` with root access, of course. Afterward, the file will be located at `/sdcard/logo.bin`. If three megabytes isn't enough, you can try adjusting the size (or look for the correct size in the scatter file).
3) You can perform a "ReadBack" using SmarthPhoneFlashTool.

Q: My `logo.bin` file was unpacked, but instead of nice images, I see noise.
A: The image size is incorrect. Click on the image size and change it to the correct one. Recreate the project so that the new size is applied to the rest of the images.

Q: Why won't the program start?
A: Make sure all dependencies are installed if you are using the AppImage, or verify that you have correctly installed the `tar.gz` file.

Q: The `Update.zip` file created by the program worked fine, but nothing changed on the phone—or the `Update.zip` didn't work at all.
A: 1) As of 2026, you shouldn't use the `Update.zip` file, as it is not secure—plus, there are better ways to do this.
2) Try flashing the file using FlashTool.
3) Try flashing the file using `fastboot` (the device must be unlocked first!).
`fastboot flash logo logo.bin`

Q: The program shows an error: "incompatible data size..." A: Most likely, your `logo.bin` file is corrupted or comes from a device other than a MediaTek-based phone. Do not assume that just because a device uses a MediaTek (MTK) chipset, everything else is the same. Tablets and other MediaTek devices almost always have a different structure for the `/logo` partition compared to phones (or it may be entirely absent). In fact, neither I, nor anyone else not even MediaTek itself can guarantee that all phones will have a similar structure in this section.

Q: How can I change the battery charging animation?
A: Unfortunately, this is a time-consuming and tedious process for any user to undertake. Since details such as image size and screen positioning for the "powered-off" charging animation are hard-coded—programmed specifically by the OEM there is not much that can be done at the moment. That said, you can still replace the individual images used in the charging animation and try something creative let your imagination run wild!
</p>
</details>

> [!WARNING]
> Remember that anything you do with your phone is at your own risk.
> Do not forget to create backups.
> Do not attempt to replace the update script if you do not know what it does.
> If you do not understand what the program does, avoid using it.
> Lenovo devices: A charging error may occur when the phone is powered off. Proceed with caution.
> Xiaomi/Redmi/POCO devices: Some models may have locks [the logo partition can rely on digital signature checks -- signature check -- in the LK] that could render the device unusable if a modified `logo.bin` file is installed. Proceed with caution.

### Updates
If a new version of LogoBuilder.exe appears (may be? nothing's impossible....), patch_exe.py will refuse it because the SHA-256 won’t match. In that case the two call sites need to be found again. I can help with that, since the REA/Cecil analysis steps are the same.

> [!IMPORTANT]  
> If you intend to alter and/or improve any of this, don't forget to give proper credit to the authors.

Enjoy your boot logos!
