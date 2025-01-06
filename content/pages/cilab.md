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
- Change the password after the first login with web interface at [https://223.195.240.67:1006/](https://223.195.240.67:1006/)
> You might experience a problem of unsecured connection. It is OK🙄 to ignore the warning and proceed to the website.

> However, with an unsecured connection, your data, especially your username and password will be transmitted in plain text🤮. So, it is recommended to contact the administrator to install a SSL certificate on your PC, especially if you are using a public network and you share the same username and password with other services.
2. **Connecting To NAS**
   - NAS Web Interface
     - Open a web browser and go to [https://223.195.240.67:1006/](https://223.195.240.67:1006/)
     - Enter your username and password
     - Click [Sign In]
     - NAS Web Interface main features include:
       - [File Station] is for managing files and folders
       - [Personal] contains your account information
   - SFTP Clients  
        Please refer to [Data Transfer 🚚](./cilab/#data-transfer--and-environment-setup-) for more information
3. **NAS Folder Structure**
    - *your_username* contains your personal data.
    - *PAPER-WORK* is for storing our lab's documents.
    - *PUBLIC* is for sharing materials from graduated members, this folder is read-only.

---
## GPU Workstations
### Reservation 📅
Head to the [CILAB_Shared_GPUs_Sheet](https://docs.google.com/spreadsheets/u/1/d/1NsKRx_1eLOUUYIa9rYNJWEGnNnKrfy3VcYRzI4kRusA) to reserve the GPU(s) you need. For more information, please send a message to our KakaoTalk group.
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
   - Install Anaconda by following the instructions
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
VSCode is an **All-in-One** powerful editor that runs on your local machine. It can be used to connect to a remote workstation for develpment. It comes with a lot of useful features via extensions. This guide will show you how to set up and use VSCode to connect to a CILab workstation.
- Download and install [VSCode](https://code.visualstudio.com/download) on your **local machine** (NOT the workstation!)
- Remember to make a reservation before using a workstation. And, the reservations **MUST** be canceled if you are not using the workstations anymore.
- SSH configuration:  
*(skip this step if you have already done it before.)*
  + Run VS Code on your local machine.</li>
  + Install the [Remote-SSH extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) in VSCode  
  ![regular](../figs/vscode/1.ssh.png)
  + Press `F1` (Windows/Linux) or `⇧⌘P` (MacOS) to open `Command Palette`
  + Type `Remote-SSH: Open SSH Configuration File...` and press `Enter`  
  ![regular](../figs/vscode/2.config.png)
  + Select:
    - Linux: `~/.ssh/config`
    - Windows: `C:\Users\your_username\.ssh\config`
    - MacOS: `/Users/your_username/.ssh/config`  

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
  + Press `F1` (Windows/Linux) or `⇧⌘P` (MacOS) to open `Command Palette`
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
>   - In addition the Remote-SSH extension, you can also install other extensions in VS Code. For example, [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) is useful for managing Git repositories. Recommended extensions: compareit, Edit csv, GitHub Copilot, GitHub Pull Requests and Issues, GitLens, LaTeX Workshop, Markdown All in One, Python, Remote-SSH, Remote Development, TensorBoard, and WSL.
>   - With LaTeX Workshop, VSCode can be used to write and compile LaTeX documents. The output PDF file can be viewed directly in VSCode.
<!-- #### With X2Go 🚂 -->

### Data Transfer 🚚
- Before starting to work on GPU workstations, you need to know how to transfer your data between your PC, NAS, and GPU workstations. Here are some tools that you can use:
  - sd

---
## (Optional) Data Annotation With CVAT.ai ✏️
