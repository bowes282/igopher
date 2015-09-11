# Pocket Gopher #

Gopher is a **Windows program** that reads iPod Touch/iPhone repositories and shows the list of available applications. The user can select which to install on the iPod and build a local package from the PC.

This package is then transferred to the iPod by the USB connection, and the AppTapp Installer settings are adjusted to allow you to browse and install/update the package contents. Without using the wireless connection ever.

Gopher is using the same component as [T-PoT](http://code.google.com/p/t-pot/), the Total Commander plug-in to browse the iPod filesystem from a PC.

# Features #

Currently, the main features of Gopher are:
  * Reads iPod/iPhone repositories from a source list and displays the applications.
  * Stores selected packages on the iPod for local installation.
  * Uses AppTapp Installer, so the compatibility with all the existing applications is guaranteed.

The current version is but a first test so the features and GUI are pretty basic. Further additions should include: better synchronization between the iPod and Gopher (import/export of repository sources, import of already installed applications to detect updates on the PC, application history backups to be able to roll back, repository statistics, ...).

It has been successfully tested on iPod Touch, firmware 1.1.2 and 1.1.3.

# Warning #


---

**While this program takes as many precautions as possible (tests and backup
of files), it directly modifies files used by the Installer. Should
something bad occur, it could leave the Installer in a bad state a need
manual intervention to solve the issue.**

**SINCE IT IS ONLY A FIRST ALPHA TEST VERSION, THE AUTHOR WILL NOT REPLY TO
ANY ENQUIRY AS TO HOW SOLVE PROBLEMS THAT HAPPENED USING THE PROGRAM. Use
it at your own risk!**

---


# Installation #

Download the latest version from the [Downloads](http://code.google.com/p/igopher/downloads/list) page, and unzip its contents to a directory. There is no installer for this version yet.

The program has been compiled with Visual Studio 2005, so it needs the following in order to run (already present on most recent systems):
  * [Microsoft .NET Framework Version 2.0 Redistributable Package (x86)](http://www.microsoft.com/downloads/details.aspx?FamilyID=0856EACB-4362-4B0D-8EDD-AAB15C5E04F5&displaylang=en)
> Which requires the following:
    * [Windows Installer 3.0 Redistributable](http://www.microsoft.com/downloads/details.aspx?familyid=5FBC5470-B259-4733-A914-A956122E08E8&displaylang=en) (needs genuine Windows)

It also uses the [Libxml2](http://xmlsoft.org/) library to parse xml files, the library files are included in the zip archive for convenience.

Don't forget to check the [AppTappBasics](AppTappBasics.md) page.

# Getting Started #

It's quite simple, edit the **PackageSources.txt** file to add/replace repository URL's, start the program. The first time, you will have to wait until it has scanned all the repositories, so patience.

Gopher uses a cache for the repositories, and will only refresh on demand. So don't forget to use the menu Repositories / Refresh regularly.

Choose which applications you want to install by checking them, you can use the search function to locate them more easily. Once you are satisfied with your choice, make sure your iPod is connected and use the menu **Files / Clear Local Script** (to remove any script you may have created before) then **Files / Export Script** to start the upload procedure to the iPod.

If everything goes well, a pop-up will tell you everything is ready to install. Start the Installer on the iPod, it should refresh and let you install or update your applications.

You can also simply use **Files / Create Local Script** which will put everything in the export subdirectory without transferring the files to the iPod. You can still transfer them later by using **Files / Export Script**.

Once the intallation is finished on the iPod, you can put the Installer back in normal mode (using external repositories) with the iPod / Restore Sources menu option. Later on, you will still be able to uninstall or update whichever applications you installed with Gopher, whether you do it locally with Gopher, or from the normal Installer mode with external repositories.

# Known Issues #

Problems are reported on the [Issues](http://code.google.com/p/igopher/issues/list?can=1&q=&colspec=ID+Type+Status+Priority+Milestone+Owner+Summary&cells=tiles) page of the project.

# History #

**Version 0.2 (16-Feb-2008)**

  * Fixed username in 1.1.3 vs 1.1.2 and prior.
  * Changed HTTP\_USER\_AGENT to "AppTapp Installer/3.0 (iPhone)" since some repositories now ignore the previous versions of the Installer.
  * Added Files/Create Script and Files/Clean Script (doesn't create the script if already exists in Files/Export Script).
  * Added support for repository "source" key value.

**Version 0.1 (10-Feb-2008)**

> First public test.
  * Reads iPod/iPhone repositories from a source list and displays the applications.
  * Stores selected packages on the iPod for local installation.
  * Uses AppTapp Installer, so the compatibility with all the existing applications is guaranteed.