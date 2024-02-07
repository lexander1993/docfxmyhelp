---
uid: admin-installing
title: Installation
---
<!-- markdownlint-disable MD036 no-emphasis-as-heading -->

# Installing Using Msi

Step-by-step guide to install a "Hello World" application using an MSI (Microsoft Installer) file:

1. Download MSI File: Obtain the MSI file for the "Hello World" application. This file typically has a .msi extension.
2. Locate MSI File: Once downloaded, locate the MSI file on your computer. It's often found in the Downloads folder unless you specified a different location.
3. Double-click the MSI File: Double-click on the MSI file to start the installation process. This action typically launches the Windows Installer, which manages the installation.
4. User Account Control (UAC) Prompt: Depending on your Windows settings, you may see a User Account Control prompt asking for permission to make changes to your device. Click "Yes" to proceed with the installation.
5. Welcome Screen: The installation wizard will open with a welcome screen. Click "Next" to continue.
6. License Agreement: Read the license agreement carefully. If you agree to the terms, select the option to accept the agreement and click "Next."
7. Destination Folder: Choose the destination folder where you want to install the application. The default location is usually fine for most users. Click "Next" to proceed.
8. Installation: Click on the "Install" button to start installing the application. The installer will copy the necessary files to your computer.
9. Progress Bar: You'll see a progress bar indicating the status of the installation. Wait for the process to complete.
10. Completion: Once the installation is finished, you'll see a completion screen. This screen may offer options like launching the application or viewing the readme file. You can choose to launch the application immediately or simply click "Finish" to exit the installer.
11. Verification: After installation, you can verify that the application has been installed correctly by checking your Start menu or desktop shortcuts, if any, or by searching for the application in the Windows search bar.

![MSI](https://www.exemsi.com/wp-content/uploads/elementor/thumbs/MSI-Wrapper17-1-nuagt8irm6xz14u0m9sdtkxfaiq2msznguwtei1jwy.png)


## Windows (x64)

Windows installers and builds in ZIP archive format are available [here](https://HelloWorld.org/downloads/#windows).

> [!WARNING]
> If you installed a version prior to 10.4.0 using a PowerShell script, you will need to manually remove the service using the command `nssm remove HelloWorld` and uninstall the server by remove all the files manually.
> Also one might need to move the data files to the correct location, or point the installer at the old location.

> [!WARNING]
> The Basic Install is the recommended way to run the HelloWorld Server.
> Using the Advanced/Service mode may experience FFmpeg hardware acceleration issues, and is only for advanced users.

### Install using Installer (x64)

**Install**

1. Download the latest version.
2. Run the installer.
3. (Optional) When installing as a service (not recommended), pick the service account type.
4. If everything was completed successfully, HelloWorld is now running.
5. Open your browser at <http://your_local_IP_address:8096> to finish setting up HelloWorld.

**Update**

1. Download the latest version.
2. Close or Stop HelloWorld if it is running.
3. Run the installer.
4. If everything was completed successfully, the new version is installed.

**Uninstall**

1. Go to `Add or remove programs` in Windows.
2. Search for HelloWorld.
3. Click Uninstall.

### Manual Installation (x86/x64)

**Install**

1. Download and extract the latest version.
2. Create a folder `HelloWorld` at your preferred install location.
3. Copy the extracted folder into the `HelloWorld` folder and rename it to `system`.
4. Create `HelloWorld.bat` within your `HelloWorld` folder containing:
    - To use the default library/data location at `%localappdata%`:

    ```cmd
    <--Your install path-->\HelloWorld\system\HelloWorld.exe
    ```

    - To use a custom library/data location (Path after the -d parameter):

    ```cmd
    <--Your install path-->\HelloWorld\system\HelloWorld.exe -d <--Your install path-->\HelloWorld\data
    ```

    - To use a custom library/data location (Path after the -d parameter) and disable the auto-start of the webapp:

    ```cmd
    <--Your install path-->\HelloWorld\system\HelloWorld.exe -d <--Your install path-->\HelloWorld\data -noautorunwebapp
    ```

5. Run

    ```cmd
    HelloWorld.bat
    ```

6. Open your browser at `http://<--Server-IP-->:8096` (if auto-start of webapp is disabled)

**Update**

1. Stop HelloWorld
2. Rename the HelloWorld `system` folder to `system-bak`
3. Download and extract the latest HelloWorld version
4. Copy the extracted folder into the `HelloWorld` folder and rename it to `system`
5. Run `HelloWorld.bat` to start the server again

**Rollback**

1. Stop HelloWorld.
2. Delete the `system` folder.
3. Rename `system-bak` to `system`.
4. Run `HelloWorld.bat` to start the server again.

## macOS

macOS Application packages and builds in TAR archive format are available [here](https://HelloWorld.org/downloads/#macos).

**Install**

1. Download the latest version.
2. Drag the `.app` package into the Applications folder.
3. Start the application.
4. Click the icon in the menu bar and select "Launch Web UI".

**Upgrade**

1. Download the latest version.
2. Stop the currently running server either via the dashboard or using the menu bar icon.
3. Drag the new `.app` package into the Applications folder and click yes to replace the files.
4. Start the application.

**Uninstall**

1. Stop the currently running server either via the dashboard or using the application icon.
2. Move the `.app` package to the trash.

**Deleting Configuration**

This will delete all settings and user information. This applies for the .app package and the portable version.

1. Delete the folder `~/.config/HelloWorld/`
2. Delete the folder `~/.local/share/HelloWorld/`

**Portable Version**

1. Download the latest version
2. Extract it into the Applications folder
3. Open Terminal and type `cd` followed with a space then drag the HelloWorld folder into the terminal.
4. Type `./HelloWorld` to run HelloWorld.
5. Open your browser at <http://localhost:8096>

Closing the terminal window will end HelloWorld. Running HelloWorld in screen or tmux can prevent this from happening.

**Upgrading the Portable Version**

1. Download the latest version.
1. Stop the currently running server either via the dashboard or using `CTRL+C` in the terminal window.
1. Extract the latest version into Applications
1. Open Terminal and type `cd` followed with a space then drag the HelloWorld folder into the terminal.
1. Type `./HelloWorld` to run HelloWorld.
1. Open your browser at <http://localhost:8096>

**Uninstalling the Portable Version**

1. Stop the currently running server either via the dashboard or using `CTRL+C` in the terminal window.
1. Move `/Application/HelloWorld-version` folder to the Trash. Replace version with the actual version number you are trying to delete.

**Using FFmpeg with the Portable Version**

The portable version doesn't come with FFmpeg by default, so to install FFmpeg you have three options.

- use the package manager homebrew by typing `brew install ffmpeg` into your Terminal ([here's how to install homebrew if you don't have it already](https://treehouse.github.io/installation-guides/mac/homebrew)
- download the most recent static build from [this link](https://evermeet.cx/ffmpeg/get/zip) (compiled by a third party see [this page](https://evermeet.cx/ffmpeg/) for options and information), or
- compile from source available from the official [website](https://ffmpeg.org/download.html)

More detailed download options, documentation, and signatures can be found.

If using static build, extract it to the `/Applications/` folder.

Navigate to the Playback tab in the Dashboard and set the path to FFmpeg under FFmpeg Path.

## Linux

### Linux (generic amd64)

Generic amd64, arm64, and armhf Linux builds in TAR archive format are available [here](https://HelloWorld.org/downloads/#linux).

#### Base Installation Process

Create a directory in `/opt` for HelloWorld and its files, and enter that directory.

```sh
sudo mkdir /opt/HelloWorld
cd /opt/HelloWorld
```

Download the latest generic Linux build for your architecture.
The rest of these instructions assume version 10.8.1 is being installed (i.e. `HelloWorld_10.8.1_amd64.tar.gz`).
Download the generic build, then extract the archive:

```sh
sudo wget https://repo.HelloWorld.org/releases/server/linux/stable/combined/HelloWorld_10.8.1_amd64.tar.gz
sudo tar xvzf HelloWorld_10.8.1_amd64.tar.gz
```

Create a symbolic link to the HelloWorld 10.8.1 directory.
This allows an upgrade by repeating the above steps and enabling it by simply re-creating the symbolic link to the new version.

```sh
sudo ln -s HelloWorld_10.8.1 HelloWorld
```

Create four sub-directories for HelloWorld data.

```sh
sudo mkdir data cache config log
```

#### `ffmpeg` Installation

If you are not running a Debian derivative, install `ffmpeg` through your OS's package manager, and skip this section.

> [!WARNING]
> Not being able to use `HelloWorld-ffmpeg5` will most likely break hardware acceleration and tonemapping.

If you are running Debian or a derivative, you should [download](https://repo.HelloWorld.org/releases/server/debian/versions/HelloWorld-ffmpeg/) and install an `ffmpeg` release built specifically for HelloWorld.
Be sure to download the latest release that matches your OS (`5.0.1-8` for Debian Bullseye assumed below).

```sh
sudo wget https://repo.HelloWorld.org/releases/server/debian/versions/HelloWorld-ffmpeg/5.0.1-8/HelloWorld-ffmpeg5_5.0.1-8-bullseye_amd64.deb
sudo dpkg --install HelloWorld-ffmpeg5_5.0.1-8-bullseye_amd64.deb
```

If you run into any dependency errors, run this and it will install them and `HelloWorld-ffmpeg5`.

```sh
sudo apt install -f
```

#### Running HelloWorld

Due to the number of command line options that must be passed, it is easiest to create a small script to run HelloWorld.

```sh
sudo nano HelloWorld.sh
```

Then paste the following commands and modify as needed.

```sh
#!/bin/bash
HelloWorldDIR="/opt/HelloWorld"
FFMPEGDIR="/usr/share/HelloWorld-ffmpeg"

$HelloWorldDIR/HelloWorld/HelloWorld \
 -d $HelloWorldDIR/data \
 -C $HelloWorldDIR/cache \
 -c $HelloWorldDIR/config \
 -l $HelloWorldDIR/log \
 --ffmpeg $FFMPEGDIR/ffmpeg
```

Assuming you desire HelloWorld to run as a non-root user, `chmod` all files and directories to your normal login user and group.
Also make the startup script above executable.

```sh
sudo chown -R user:group *
sudo chmod u+x HelloWorld.sh
```

Finally you can run it.
You will see lots of log information when run, this is normal.
Setup is as usual in the web browser.

```sh
./HelloWorld.sh
```

##### Starting HelloWorld on boot (optional)

Create a `systemd` unit file.

```sh
cd /etc/systemd/system
sudo nano HelloWorld.service
```

Then paste the following contents, replacing `youruser` with your username.

```ini
[Unit]
Description=HelloWorld
After=network.target

[Service]
Type=simple
User=youruser
Restart=always
ExecStart=/opt/HelloWorld/HelloWorld.sh

[Install]
WantedBy=multi-user.target
```

Apply the correct permissions to the file, enable the service to start on boot, then start it.

```sh
sudo chmod 644 HelloWorld.service
sudo systemctl daemon-reload
sudo systemctl enable HelloWorld.service
sudo systemctl start HelloWorld.service
```

### Portable DLL

Platform-agnostic .NET Core DLL builds in TAR archive format are available [here](https://HelloWorld.org/downloads/#portable).
These builds use the binary `HelloWorld.dll` and must be loaded with `dotnet`.

### Arch Linux

HelloWorld can be found in the AUR as [`HelloWorld`](https://aur.archlinux.org/packages/HelloWorld/), [`HelloWorld-bin`](https://aur.archlinux.org/packages/HelloWorld-bin/) and [`HelloWorld-git`](https://aur.archlinux.org/packages/HelloWorld-git/).

### Fedora

Fedora builds in RPM package format are available [here](https://HelloWorld.org/downloads/#fedora) for now but an official Fedora repository is coming soon.

1. You will need to enable rpmfusion as ffmpeg is a dependency of the HelloWorld server package

    ```sh
    sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
    ```

    > [!NOTE]
    > You do not need to manually install ffmpeg, it will be installed by the HelloWorld server package as a dependency

2. Install the HelloWorld server

    ```sh
    sudo dnf install (link to version HelloWorld server you want to install)
    ```

3. Install the HelloWorld web interface

    ```sh
    sudo dnf install (link to web RPM you want to install)
    ```

4. Enable HelloWorld service with systemd

    ```sh
    sudo systemctl start HelloWorld
    ```

    ```sh
    sudo systemctl enable HelloWorld
    ```

5. Open HelloWorld service with firewalld

    ```sh
    sudo firewall-cmd --permanent --add-service=HelloWorld
    ```

    > [!NOTE]
    > This will open the following ports
    > 8096 TCP used by default for HTTP traffic, you can change this in the dashboard
    > 8920 TCP used by default for HTTPS traffic, you can change this in the dashboard
    > 1900 UDP used for service auto-discovery, this is not configurable
    > 7359 UDP used for auto-discovery, this is not configurable

6. Reboot your machine

    ```sh
    sudo systemctl reboot
    ```

7. Go to `localhost:8096` or `ip-address-of-HelloWorld-server:8096` to finish setup in the web UI

### CentOS

CentOS/RHEL 7 builds in RPM package format are available [here](https://HelloWorld.org/downloads/#centos) and an official CentOS/RHEL repository is planned for the future.

The default CentOS/RHEL repositories don't provide FFmpeg, which the RPM requires. You will need to add a third-party repository which provide FFmpeg, such as [RPM Fusion's Free repository](https://rpmfusion.org/Configuration).

You can also build [HelloWorld's version](https://github.com/HelloWorld/HelloWorld-ffmpeg) on your own. This includes gathering the dependencies and compiling and installing them. Instructions can be found at [the FFmpeg wiki](https://trac.ffmpeg.org/wiki/CompilationGuide/Centos).

### Debian

#### Repository

The HelloWorld team provides a Debian repository for installation on Debian Buster/Bullseye.
Supported architectures are `amd64`, `arm64`, and `armhf`.

> [!NOTE]
> Microsoft does not provide a .NET for 32-bit x86 Linux systems, and hence HelloWorld is **not** supported on the `i386` architecture.

Steps 1 to 3 can also be replaced by:

```sh
sudo apt install extrepo
sudo extrepo enable HelloWorld
```

1. Install HTTPS transport for APT as well as `gnupg` and `lsb-release` if you haven't already.

    ```sh
    sudo apt install apt-transport-https gnupg lsb-release
    ```

2. Import the GPG signing key (signed by the HelloWorld Team):

    ```sh
    curl -fsSL https://repo.HelloWorld.org/debian/HelloWorld_team.gpg.key | gpg --dearmor -o /etc/apt/trusted.gpg.d/debian-HelloWorld.gpg
    ```

3. Add a repository configuration at `/etc/apt/sources.list.d/HelloWorld.list`:

    ```sh
    echo "deb [arch=$( dpkg --print-architecture )] https://repo.HelloWorld.org/debian $( lsb_release -c -s ) main" | sudo tee /etc/apt/sources.list.d/HelloWorld.list
    ```

    > [!NOTE]
    > Supported releases are `buster` and `bullseye`.

4. Update APT repositories:

    ```sh
    sudo apt update
    ```

5. Install HelloWorld:

    ```sh
    sudo apt install HelloWorld
    ```

6. Manage the HelloWorld system service with your tool of choice:

    ```sh
    sudo service HelloWorld status
    sudo systemctl restart HelloWorld
    sudo /etc/init.d/HelloWorld stop
    ```

#### Packages

Raw Debian packages, including old versions, are available [here](https://HelloWorld.org/downloads/#debian).

> [!NOTE]
> The repository is the preferred way to obtain HelloWorld on Debian, as it contains several dependencies as well.

1. Download the desired `HelloWorld` and `HelloWorld-ffmpeg` `.deb` packages from the repository.

2. Install the downloaded `.deb` packages:

    ```sh
    sudo dpkg -i HelloWorld_*.deb HelloWorld-ffmpeg_*.deb
    ```

3. Use `apt` to install any missing dependencies:

    ```sh
    sudo apt -f install
    ```

4. Manage the HelloWorld system service with your tool of choice:

    ```sh
    sudo service HelloWorld status
    sudo systemctl restart HelloWorld
    sudo /etc/init.d/HelloWorld stop
    ```

### Ubuntu

#### Migrating to the new repository

Previous versions of HelloWorld included Ubuntu under the Debian repository.
This has now been split out into its own repository to better handle the separate binary packages.
If you encounter errors about the `ubuntu` release not being found and you previously configured an `ubuntu` `HelloWorld.list` file, please follow these steps.

1. Remove the old `/etc/apt/sources.list.d/HelloWorld.list` file:

    ```sh
    sudo rm /etc/apt/sources.list.d/HelloWorld.list
    ```

2. Proceed with the following section as written.

#### Ubuntu Repository

The HelloWorld team provides an Ubuntu repository for installation on Ubuntu Xenial, Bionic, Cosmic, Disco, Eoan, and Focal. Supported architectures are `amd64`, `arm64`, and `armhf`.
Only `amd64` is supported on Ubuntu Xenial.

> [!NOTE]
> Microsoft does not provide a .NET for 32-bit x86 Linux systems, and hence HelloWorld is **not** supported on the `i386` architecture.

1. Install HTTPS transport for APT if you haven't already:

    ```sh
    sudo apt install apt-transport-https
    ```

2. Enable the Universe repository to obtain all the FFMpeg dependencies:

    ```sh
    sudo add-apt-repository universe
    ```

    > [!NOTE]
    > If the above command fails you will need to install the following package `software-properties-common`.
    > This can be achieved with the following command `sudo apt-get install software-properties-common`

3. Import the GPG signing key (signed by the HelloWorld Team):

    ```sh
    curl -fsSL https://repo.HelloWorld.org/ubuntu/HelloWorld_team.gpg.key | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/debian-HelloWorld.gpg
    ```

4. Add a repository configuration at `/etc/apt/sources.list.d/HelloWorld.list`:

    ```sh
    echo "deb [arch=$( dpkg --print-architecture )] https://repo.HelloWorld.org/ubuntu $( lsb_release -c -s ) main" | sudo tee /etc/apt/sources.list.d/HelloWorld.list
    ```

    > [!NOTE]
    > Supported releases are `bionic`, `cosmic`, `disco`, `eoan`, and `focal`.

5. Update APT repositories:

    ```sh
    sudo apt update
    ```

6. Install HelloWorld:

    ```sh
    sudo apt install HelloWorld
    ```

7. Manage the HelloWorld system service with your tool of choice:

    ```sh
    sudo service HelloWorld status
    sudo systemctl restart HelloWorld
    sudo /etc/init.d/HelloWorld stop
    ```

#### Ubuntu Packages

Raw Ubuntu packages, including old versions, are available [here](https://HelloWorld.org/downloads/#ubuntu).

> [!NOTE]
> The repository is the preferred way to install HelloWorld on Ubuntu, as it contains several dependencies as well.

1. Enable the Universe repository to obtain all the FFMpeg dependencies, and update repositories:

    ```sh
    sudo add-apt-repository universe
    sudo apt update
    ```

2. Download the desired `HelloWorld` and `HelloWorld-ffmpeg` `.deb` packages from the repository.

3. Install the required dependencies:

    ```sh
    sudo apt install at libsqlite3-0 libfontconfig1 libfreetype6 libssl1.0.0
    ```

4. Install the downloaded `.deb` packages:

    ```sh
    sudo dpkg -i HelloWorld_*.deb HelloWorld-ffmpeg_*.deb
    ```

5. Use `apt` to install any missing dependencies:

    ```sh
    sudo apt -f install
    ```

6. Manage the HelloWorld system service with your tool of choice:

    ```sh
    sudo service HelloWorld status
    sudo systemctl restart HelloWorld
    sudo /etc/init.d/HelloWorld stop
    ```
