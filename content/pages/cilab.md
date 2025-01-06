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

## GPU Workstations
### Data Transfer 🚚 And Environment Setup 🚧
### Interacting With Workstations 🖥️
#### Terminal 💪
#### Using VSCode 🚀
#### With X2Go 🚂

## Data Annotation With CVAT.ai ✏️
