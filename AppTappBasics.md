# Introduction #

The files used by the Installer are the following ones, where we note $user the default user on the iPod: _root_ for firmware versions up to 1.1.2, _mobile_ for firmware version 1.1.3 and possibly later versions.

  * /var/$user/Library/Installer/LocalPackages.plist
  * /var/$user/Library/Installer/PackageSources.plist
  * /var/$user/Library/Installer/RemotePackages.plist
  * /var/$user/Library/Installer/TrustedSources.plist

The most important one, that you certainly don't want to lose, is **LocalPackages.plist**. It contains the list of the applications already installed on your iPod. If you remove this file, you will not be able to uninstall them, and probably not to update them either. It is possible to reconstruct this file manually but it could be a long and tedious task if you have many applications.

The second one that is worth keeping is **PackageSources.plist**, it contains the list of the repository sources you are currently using on the iPod. If you lose this file, you will have to re-enter the list of your favourite sources.

The two remaining files, **RemotePackages.plist** and **TrustedSources.plist**, are reconstructed by the Installer so they are not really important. The first one contains the list of the applications fetched from the different repositories at the last refresh, removing the file will force a refresh. The second is provided by the authors of the Installer, it is updated remotely to give the name of the trusted repositories. If the remote version is updated, or if the file is missing, Installer will fetch a new version.

# How does Gopher work? #

The Pocket Gopher scans the remote repositories whose list is in the **PackageSources.txt** file. When the user has chosen the applications and does an **Export Script** from the Files menu,

  1. Gopher builds a local repository local.plist in the export directory. It downloads all the necessary zip files, one for each application and renames them to app001.zip ... appxxx.zip to avoid name conflicts. The zip filenames are changed accordingly in local.plist.
  1. The export directory contents is transferred to the iPod.
  1. The original PackageSources.txt file of the Installer is saved in a backup directory /var/$user/Library/Installer/Backup/PackageSources.plist, unless it detects that file already.
  1. A new /var/$user/Library/Installer/PackageSources.plist file is generated, which points to the local repository just transferred.

So after an Export Script, the iPod Installer is in a local mode: it will ignore all your usual external repositories (http://repository.apptapp.com, http://conceitedsoftware.com/iphone and so on) and only show the applications you have exported.

You can install and update the applications as desired. This operation is of course much faster than when you go wireless. Once this is done, leave the Installer as usual, it will probably respring to show the modifications in SpringBoard (new icons, ...).

At this point, you have the choice to leave everything as is, for example if you don't intend to use remote repositories for the time being. Or you can restore the normal Installer mode, with the original sources: to do that, select **Restore Sources** in the Gopher iPod menu.

# Something went wrong... #

Then good luck. For now, you are basically on your own - see the big warning in the project home page? ;-)

Don't panic though, most problems won't need anything special from your part, it will typically be a non-existing zip file (faulty remote repository), a bad USB connection, or a problem while using the AppTapp Installer.

A few important remarks:

  * Don't forget to refresh the repositories in Gopher, it won't do it automatically for you (menu Repositories / Refresh).
  * If you are lost, try to restore the normal mode: iPod menu, Restore Sources. If it tells you OK, or that there is nothing to restore, you're most probably fine.
  * If you can't connect to the iPod, for example you do a iPod / Get Version and you have the reply "Couldn't find user on iPod device.", check the cable, that iTunes is correctly installed and so on. Try to restart the program.

A log is kept in the program directory, it may help finding out what the problem is.

Note that a backup of the current LocalPackages.plist is made **before each export** in the backup directory on your PC, just where the Gopher.exe program is located. And it is very unlickely that your original LocalPackages.plist file has been destroyed on your iPod.

  * Start the Installer and check the Uninstall page: are your applications still there? Then you're fine and the LocalPackages.plist file is correct.
  * If you don't see your applications, first check with MobileFinder, WinSCP, or Total Commander and the T-Pot plug-in, if /var/$user/Library/Installer/LocalPackages.plist exists and has about the same size than the xxxx\_LocalPackages.plist files under your backup directory on your PC (right under where the Gopher.exe program is).
  * If you miss the iPod LocalPackages.plist, or if it is corrupted, replace it with the latest backup version of your PC (the PC files have a timestamp in front of the name, rename the file so that it has the correct name).

The same with **PackageSources.plist**:

  * First check with MobileFinder, WinSCP, or Total Commander and the T-Pot plug-in, if there is still a backup directory on the iPod at this location: /var/$user/Library/Installer/Backup/PackageSources.plist
  * If the file exists, simply remove /var/$user/Library/Installer/PackageSources.plist and replace it with the backuped version (so /var/$user/Library/Installer/Backup/PackageSources.plist).
  * If this file doesn't exist anymore, check if /var/$user/Library/Installer/PackageSources.plist is your original version. You can do that by starting the Installer and checking the Sources page.
  * If this is not your original file, you can look in the PC backup directory for the latest correct version, and put it back on the iPod (the PC files have a timestamp in front of the name, rename the file so that it has the correct name).

In the worst case, you will have to re-enter the repository sources, but this really shouldn't happen.