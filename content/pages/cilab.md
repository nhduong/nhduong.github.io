---
author: [""]
title: "CILab Documentation"
# date: "2019-03-10"
# description: "Sample article showcasing basic code syntax and formatting for HTML elements."
# summary: "Sample article showcasing basic code syntax and formatting for HTML elements."
# tags: ["markdown", "syntax", "code", "gist"]
# categories: ["themes", "syntax"]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
---

## Network Attached Storage (NAS) 📀
> What is NAS for?
> - Storing/sharing materials for research, e.g., datasets, codes, etc.
> - Being linked to workstations for remote development.

<mark>DO NOT</mark> keep any sensitive information on NAS!

1. **Gaining Access To NAS**
- Ask the administrator for a username and a password
- Change the password after the first login with web interface at <a href="https://223.195.240.67:1006" target="_blank">https://223.195.240.67:1006</a>
> You might experience a problem of unsecured connection. It is OK🙄 to ignore the warning and proceed to the website.

> However, with an unsecured connection, your data, especially your username and password will be transmitted in plain text🤮. So, it is recommended to contact the administrator to install a SSL certificate on your PC, especially if you are using a public network and you share the same username and password with other services.
1. **Connecting To NAS**
   - NAS Web Interface
     - Open a web browser and go to <a href="https://223.195.240.67:1006" target="_blank">https://223.195.240.67:1006</a>
     - Enter your username and password
     - Click [Sign In]
     - NAS Web Interface main features include:
       - [File Station] is for managing files and folders
       - [Personal] contains your account information
   - SFTP Clients  
        Please refer to [Data Transfer 🚚](./cilab/#data-transfer-) for more information
2. **NAS Folder Structure**
    - *your_username* contains your personal data.
    - *PAPER-WORK* is for storing our lab's documents.
    - *PUBLIC* is for sharing materials from graduated members, this folder is read-only.

---
## GPU Workstations
### Reservation 📅
Head to the <a href="https://docs.google.com/spreadsheets/u/1/d/1NsKRx_1eLOUUYIa9rYNJWEGnNnKrfy3VcYRzI4kRusA" target="_blank">CILAB_Shared_GPUs_Sheet</a> to reserve the GPU(s) you need. In summary,
- <mark>Only make a reservation</mark> when your <mark>code is ready</mark> to run as other members might need GPU(s) more urgently.
- <mark>Cancel the reservation</mark> if you <mark>do not need GPU(s)</mark> anymore.  

For more information, please ask questions in our KakaoTalk group.
### Connecting To Workstations 🖥️
Let's start with the most common way to connect to a workstation, which is using SSH with a terminal.
   - Ask the administrator for a username and a password
   - Open a terminal
   - Connect to the workstation with the following command
     ```bash
     ssh username@workstation_ip -p 1004
     ```
   - Enter your password
   - You are now connected to the workstation  
     ![regular](../figs/env/0.ssh_terminal.png)
### Environment Setup 🚧
For the most part, you will be working on GPU workstations with Python based projects. Here is an example of how to set up your Python environment:
1. **Connect to the workstation with SSH**
2. **Install Anaconda**
   - Download the latest version of Anaconda for Linux, for example, *Anaconda3-2024.10-1-Linux-x86_64.sh* 
     ```bash
     wget https://repo.anaconda.com/archive/Anaconda3-2024.10-1-Linux-x86_64.sh
     ```
   - Enter the following command to install Anaconda
     ```bash
     bash Anaconda3-2024.10-1-Linux-x86_64.sh
     ```
      then follow the instructions to complete the installation.
   - Create a new environment with Python 3.9
     ```bash
     conda create -n <your environment name here> python=3.9
     ```
     Replace `<your environment name here>` with any name you want.
   - Activate the environment
     ```bash
     conda activate <your environment name here>
     ```
     You should see the environment name in the terminal prompt which is `(csd)` in the figure below.  
     ![regular](../figs/env/1.env.png)
3. **Hello World!**
   - Let's start with a simple Python script
   - Use `nano` text editor to create a Python script
     ```bash
     nano hello.py
     ```
   - Enter the following content
     ```python
     print("Hello, World!")
     ```
   - Save the file by pressing `Ctrl + O` and then `Enter`
   - Close `nano` by pressing `Ctrl + X`
   - Run the file with the following command
     ```bash
     python hello.py
     ```
     You should see the output `Hello, World!` in the terminal!
### Interacting With Workstations 🖥️
<!-- #### Terminal 💪 -->
<!-- #### Using VSCode 🚀 -->
VSCode is an All-in-One powerful editor that runs on your local machine. It can be used to connect to a remote workstation for develpment. It comes with a lot of useful features via extensions. This guide will show you how to set up and use VSCode to connect to a CILab workstation.
- Download and install <a href="https://code.visualstudio.com/download" target="_blank">VSCode</a> on your <mark>local machine</mark> (NOT the workstation!)
- Remember to make a reservation before using a workstation. And, the reservations <mark>MUST be canceled</mark> if you are not using the workstations anymore.
- SSH configuration:  
*(skip this step if you have already done it before.)*
  + Run VS Code on your local machine.</li>
  + Install the <a href="https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh" target="_blank">Remote-SSH extension</a> in VSCode  
  ![regular](../figs/vscode/1.ssh.png)
  + Press `F1` (Windows/Linux) or `⇧⌘P` (macOS) to open `Command Palette`
  + Type `Remote-SSH: Open SSH Configuration File...` and press `Enter`  
  ![regular](../figs/vscode/2.config.png)
  + Select:
    - Linux: `~/.ssh/config`
    - Windows: `C:\Users\your_username\.ssh\config`
    - macOS: `/Users/your_username/.ssh/config`  

  then press `Enter`.
  + Add the following lines to the file:
    ```bash
    Host any_name_you_like
        HostName workstation_ip_address
        User your_username
        Port 1004
    ```
  + Save the file and close it.
- Connecting to a server
  + Run VS Code on your local machine (if you haven't.)
  + Press `F1` (Windows/Linux) or `⇧⌘P` (macOS) to open `Command Palette`
  + Type `Remote-SSH: Connect to Host...` and press `Enter`  
  ![regular](../figs/vscode/3.connect.png)
  + Select the name you set in the previous step and press `Enter`
  + Enter your password and press `Enter`
  + Wait for the connection to be established
  + You should see the workstation name in the bottom left corner of the VS Code window. In the example below, the server name is `cilabws05`  
  ![regular](../figs/vscode/4.connected.png)
  + Let's look for available GPUs. Open a new terminal by selecting `Terminal -> New Terminal` from the top menu
  + Type `nvidia-smi` and press `Enter`
  + In the example below, *GPU #0* is being used by someone else while *GPUs #1*, *#2*, and *#3* are free.  
  ![regular](../figs/vscode/5.nvidia-smi.png)

Now everything is set up and you can start working on the workstation with VS Code!

> *Tips and tricks*
>   - With VS Code, in general, a task, e.g., openning a terminal instance, can be done in multiple ways. Play around with it to find the way you like.
>   - In VS Code, most of the tasks can be done via `Command Palette` and they can also be associated with keyboard shortcuts. Click the wheel icon in the bottom left corner then select `Keyboard Shortcuts` for more information.
>   - In addition the Remote-SSH extension, you can also install other extensions in VS Code. For example, <a href="https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens" target="_blank">GitLens</a> is useful for managing Git repositories. Recommended extensions: compareit, Edit csv, GitHub Copilot, GitHub Pull Requests and Issues, GitLens, LaTeX Workshop, Markdown All in One, Python, Remote-SSH, Remote Development, TensorBoard, and WSL.
>   - With LaTeX Workshop, VSCode can be used to write and compile LaTeX documents. The output PDF file can be viewed directly in VSCode.
>   - To run code in background, you can use `nohup` command. For example, `nohup python train.py &`. For more information, visit <a href="https://en.wikipedia.org/wiki/Nohup" target="_blank">nohup</a>. Also, you can use <a href="https://en.wikipedia.org/wiki/GNU_Screen" target="_blank">screen</a> or <a href="https://en.wikipedia.org/wiki/Tmux" target="_blank">tmux</a> for more advanced features.
<!-- #### With X2Go 🚂 -->

---
## Data Transfer 🚚
Secure File Transfer Protocol (SFTP) is required for transferring data between your PCs, workstations and NAS. There are several SFTP clients available for you to choose from, such as <a href="https://filezilla-project.org" target="_blank">FileZilla</a>, <a href="https://www.bitvise.com/ssh-client" target="_blank">Bitvise</a>, etc. For command line based software, <a href="https://github.com/libfuse/sshfs" target="_blank">sshfs</a>, <a href="https://rclone.org" target="_blank">rclone</a>, etc. are also available. In this tutorial, we will use FileZilla, `sshfs`, and `rclone` as examples.

- FileZilla  
  FileZilla is a free software and available for Windows, macOS, and Linux. It is easy to use and provides a user-friendly interface for transferring files between your PCs, workstations and NAS.  
  Here are the steps to make a connection to workstations/NAS via FileZilla:
	+ Download and install <a href="https://filezilla-project.org" target="_blank">FileZilla</a>
	+ Head to `File -> Site Manager -> New Site`
  + Fill in the following information:
    + *Protocol*: SFTP - SSH File Transfer Protocol
    + *Host*: workstation/NAS's IP address
    + *Port*: 1004
    + *Logon Type*: Normal
    + *User*: your_username
    + *Password*: your_password
  + Click `Connect`  
  ![regular](../figs/trans/1.new_site.png)

	> For the first time you connect to a workstation/NAS, you will be asked to verify the server's fingerprint. Click on the `OK` button to continue.

	> Note that the above steps are for the first time you connect to a workstation/NAS. After that, you can simply select a server and click on the `Connect` button to connect to the server.
	
  In the figure below, the left panel is for your local machine and the right panel is for the remote server (workstation/NAS). You can drag and drop files between these two panels to transfer data. To visually inspect the data, you can right-click on a file and select `View -> Edit` to open it.  
  ![regular](../figs/trans/2.mainwin.png)

- `sshfs`  
	`sshfs` is a command line based software that allows you to mount a remote file system via SFTP. In other words, you can access a folder on the workstation/NAS via a local folder on your PCs. To install sshfs, follow the instructions for <a href="https://github.com/libfuse/sshfs" target="_blank">Linux</a>, <a href="https://github.com/winfsp/sshfs-win" target="_blank">Windows</a>, and <a href="https://osxfuse.github.io" target="_blank">macOS</a>.

	To mount a workstation/NAS folder on your local machine, follow these steps:
  + Open a terminal on your local machine.
  + Run the following command to mount a remote folder on your machine:
    ```bash
    sshfs your_username@remote_IP_address:/your_username/remote_folder -p 1004 local_folder
    ```
    > In addition to your PCs, the above command can also be run on a workstation! This way, your workstation can access a NAS folder or another workstation's folder.

    > You will need to execute the above command every time you restart your PCs or workstations.

- `rclone`  
`rclone` is another command line based software that allows you to transfer data between your PCs, workstations and NAS. It supports various cloud storage providers, including Google Drive, Dropbox, etc. To set up `rclone` on a local machine or a workstation, follow these steps:
  + Download <a href="https://rclone.org/downloads" target="_blank">rclone-version-os.zip</a> based on your operating system  
  ![regular](../figs/trans/3.rclone_download.png)
  + Unzip the downloaded file to a folder, for example, `/home/user/rclone`
  + Run the following command to set up a connection to a workstation/NAS:
  ```bash
  cd /home/user/rclone
  ./rclone config
  ```
  + Follow the instructions to set up a new connection:  
    + Enter `n` to create a new remote
    + Enter the following information:
      + *name*: type any name for the connection, for example, `nas`
      + *storage*: type `sftp` for secure file transfer protocol
      + *host*: type the workstation/NAS's IP address
      + *user*: type your username
      + *port*: type `1004`
      + You will be asked to enter your password `SSH password, leave blank to use ssh-agent...`. Type `y` and press `Enter`. After that, enter your password and press `Enter`
      + For the rest of the questions, you can press `Enter` to use the default values until you see the main menu again  
      ![regular](../figs/trans/4.rclone_main.png)
      + From the figure above, you can see that the connection `nas` has been successfully set up. Let's test the connection by running the following command:
      ```bash
      ./rclone lsd nas:/
      ```  
      ![regular](../figs/trans/5.rclone_lsd.png)
      + If you see a list of folders on the workstation/NAS, the connection is successful. You can now transfer data between your PCs, workstations and NAS using `rclone` with the following command:
      ```bash
      ./rclone copy local_folder nas:/remote_folder
      ```
      There are many other features of `rclone` that you might want to explore. Execute `./rclone --help` or visit <a href="https://rclone.org/commands" target="_blank">Rclone Commands</a> for more information.

---
<!-- ## (Optional) Data Annotation With CVAT.ai ✏️ -->
