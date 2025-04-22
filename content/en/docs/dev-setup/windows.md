---
title: Windows
date: 2025-04-21
description: >
  A basic setup guide for configuring a Windows development environment.
tags: [windows, configuration, guide]
---

## Package Manager: Chocolatey

The first step in setting up a Windows development environment is to install a package manager. I recommend using [Chocolatey](https://chocolatey.org/), a popular package manager for Windows.

To install Chocolatey, open an **Administrator PowerShell terminal** and run the following command:

```ps1
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

> **Note:** Visit the [Chocolatey installation page](https://chocolatey.org/install#individual) to ensure the script is up-to-date.

Follow the instructions displayed in the terminal and agree to any prompts that may appear. Once the installation is complete, close the terminal.

---

## Installing Git

Git is an essential tool for version control. To install Git using Chocolatey, open a new **Administrator PowerShell terminal** and run the following command:

```ps1
choco install git
```

Follow the instructions displayed in the terminal and agree to any prompts that may appear. Once the installation is complete, Git will be ready to use.

---

## Customizing PowerShell with OhMyPosh

To enhance the PowerShell experience, I recommend using [OhMyPosh](https://ohmyposh.dev/). OhMyPosh adds a customizable theme to your terminal, providing useful information directly in the prompt.

### Installing OhMyPosh

To install OhMyPosh, run the following command in an **Administrator PowerShell terminal**:

```ps1
choco install oh-my-posh
```

### Setting Up the Atomic Theme

I prefer using the [Atomic Theme](https://github.com/JanDeDobbeleer/oh-my-posh/blob/main/themes/atomic.omp.json) for OhMyPosh. To configure it:

1. Open your PowerShell profile file in Notepad by running:
   ```ps1
   notepad C:\Users\$USERNAME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
   ```

2. Add the following line to the file:
   ```ps1
   Invoke-Expression (oh-my-posh --init --shell pwsh --config "C:\Program Files (x86)\oh-my-posh\themes\atomic.omp.json")
   ```

3. Save the file and close Notepad.

4. Close your terminal and reopen it. If you see strange symbols in the prompt, don’t worry—this will be resolved in the next step.

---

## Installing a Better Font

OhMyPosh requires a font that supports glyphs to display properly. I recommend using the **Bitstream Vera Sans Mono** font from [Nerd Fonts](https://www.nerdfonts.com/).

To install the font, run the following command in an **Administrator PowerShell terminal**:

```ps1
choco install nerd-fonts-bitstreamverasansmono
```

After installing the font, update your terminal settings to use it:

1. Open your terminal settings.
2. Navigate to **Profiles** > **Appearance** > **Font face**.
3. Select **Bitstream Vera Sans Mono Nerd Font** from the list.

Once this is done, your terminal should display the OhMyPosh theme correctly.

---

With these steps completed, your Windows development environment is now set up with a package manager, Git, a customized PowerShell prompt, and a better font for improved readability.