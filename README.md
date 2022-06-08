# ubuntu-hashes

When you verify an Ubuntu ISO file, you generally have to also use GPG to verify that the SHA256SUMS file has not been tampered with. This is a pain. In order to help users get around the need to do this, these are SHA256SUMS files for each Ubuntu disk image, pre-verified using GPG. If the hashes here and the hashes from your Ubuntu release match, you can be virtually 100% sure that they are good.

Each distro's verification hashes are in a separate directory, **except for Ubuntu Server.** Because of how Canonical made their Ubuntu verification files, Ubuntu and Ubuntu Server use the same verification files, so if you're here for verifying an Ubuntu Server image, use the `ubuntu` directory.

# How to verify an Ubuntu image using ubuntu-hashes

1. Download the ISO image for the Ubuntu flavour and version you want to use.
2. Find the corresponding Sha256 hash for your ISO image from the official website for the Ubuntu flavour you're downloading. It will look like a very odd number with letters in it, and it will be quite long. You may end up opening a SHA256SUMS file containing many entries in it - if so, find the one for the ISO file you downloaded.
3. Copy the hash into a text editor.
4. In this repository, find the Sha256 hash for your ISO image. If you downloaded Lubuntu 22.04, for instance, you'd click on "lubuntu", then "22.04", then "SHA256SUMS".
5. Copy the hash into a text editor, directly underneath the hash you got from the official website.
6. Open a terminal in the same folder as your ISO image. You can usually do this by navigating to the ISO image using your file manager, then right-clicking inside the folder, and clicking "Open Terminal" or something like that.
7. Run `ls` to get a list of the files in the folder. This will show you the file name of your ISO file.
8. Run `sha256sum ./<name of ISO file here>`, replacing the placeholder with the full filename of your ISO file. This will spit out yet another hash.
9. Select this hash with your mouse, then press Ctrl+Shift+C to copy it. (This shortcut works in all the terminals I've tried, but it if doesn't work for you, use whatever procedure allows you to copy from your terminal.)
10. Paste that hash into the text editor, beneath the other two.
11. Carefully compare all three hashes. If you're using a text editor that highlights all occurances of selected text (like KDE's Kate), you can just select one of the hashes with your mouse, and the other two will light up if they match.

If all of the hashes are identical, then your ISO file is good.

If the hash from the ISO file doesn't match the other two, then your download is bad and you'll need to download the ISO file again.

If the top two hashes (the one from the official site and the one from this GitHub repository) don't match, double-check that you did everything right. If you followed the instructions correctly, and you're still getting the mismatch, something is dreadfully wrong with either my repository or the Ubuntu flavour's official site. In that instance, you should verify your ISO file using sha256sum and GPG, as documented here: https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview If your distro's SHA256SUMs file is good, my hash is wrong, in which case please contact me ASAP so I can fix it. If your distro's SHA256SUMS file is wrong, ***DO NOT*** use the ISO file you downloaded, as it may be malware-contaminated, and alert the developers of your chosen Ubuntu flavour of a potential security breach ASAP. And if you can't do the GPG verification, let me know that there's a mismatch, and I'll look into it and either fix the problem or alert the developers, depending on what's gone wrong.

# Supported distros

I only include hashes for Ubuntu and official Ubuntu flavours. At the time of this writing, the supported distros are:

- [Ubuntu Desktop](https://ubuntu.com/download/desktop)
- [Ubuntu Server](https://ubuntu.com/download/server)
- [Lubuntu](https://lubuntu.me/downloads/)
- [Kubuntu](https://kubuntu.org/getkubuntu/)
- [Xubuntu](https://xubuntu.org/download/)
- [Ubuntu Studio](https://ubuntustudio.org/download/)
- [Ubuntu MATE](https://ubuntu-mate.org/download/)
- [Ubuntu Budgie](https://ubuntubudgie.org/)
- [Ubuntu Kylin](https://www.ubuntukylin.com/downloads/download-en.html)

I only include hashes for Ubuntu releases that are still fully supported. At the time of this writing, the supported releases are:

- 22.04 Jammy Jellyfish
- 21.10 Impish Indri
- 20.04 Focal Fossa
- 18.04 Bionic Beaver (only supported by Ubuntu Desktop and Ubuntu Server)

Finally, I only include hashes for the PC installation images. Some distros support alternate hardware, or feature OS variants optimized for specific hardware. **These alternate versions are not supported by this repository, even if they are official.** I may change this in the future, but for now, that's it.

If you need to verify an ISO file for a distro or release that is not supported, then you'll need to use your distro's ISO verification instructions (which probably means you'll have to fight with GPG, sadly). If you don't like this, do some research on the supported distros, and see if there's one that will do what you want. Or if you are using an official distro, but for alternate hardware, go ahead and bug me about it with a bug report (pun not intended), and I'll try to add alternate hardware support to the repository.
