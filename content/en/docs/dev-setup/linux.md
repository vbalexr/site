---
title: Linux
date: 2025-04-21
description: >
  A basic setup guide for configuring a Linux/WSL development environment.
tags: [linux, configuration, guide]
---

I primarily use Linux for most of my systems, except for my main computer, which I use for gaming. My Linux setup is designed to match the look and feel of my Windows environment for consistency.

---

## Customizing Bash with OhMyPosh

To enhance the Bash experience, I recommend using [OhMyPosh](https://ohmyposh.dev/). OhMyPosh adds a customizable theme to your terminal, providing useful information directly in the prompt.

### Installing OhMyPosh

To install OhMyPosh, run the following command in your terminal:

```bash
curl -s https://ohmyposh.dev/install.sh | bash -s
```

By default, this will install OhMyPosh in the `~/.local/bin` directory.

### Setting Up the Atomic Theme

I prefer using the [Atomic Theme](https://github.com/JanDeDobbeleer/oh-my-posh/blob/main/themes/atomic.omp.json) for OhMyPosh. To configure it:

1. Open your `.bashrc` file and append the OhMyPosh configuration by running:
   ```bash
   echo 'eval "$(oh-my-posh init bash --config ~/.cache/oh-my-posh/themes/atomic.omp.json)"' >> ~/.bashrc
   ```

2. Save the changes and reload your `.bashrc` file by running:
   ```bash
   source ~/.bashrc
   ```

---

## Installing a Better Font

OhMyPosh requires a font that supports glyphs to display properly. I recommend using the **Bitstream Vera Sans Mono** font from [Nerd Fonts](https://www.nerdfonts.com/).

To install the font, follow these steps:

1. Create a directory for local fonts:
   ```bash
   mkdir -p ~/.local/share/fonts
   ```

2. Download the font archive:
   ```bash
   wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.3.0/BitstreamVeraSansMono.tar.xz
   ```

3. Extract the font files into the fonts directory:
   ```bash
   tar -xvf BitstreamVeraSansMono.tar.xz -C ~/.local/share/fonts
   ```

4. Remove the downloaded archive to save space:
   ```bash
   rm BitstreamVeraSansMono.tar.xz
   ```

5. Update the font cache to make the new fonts available:
   ```bash
   fc-cache -fv
   ```

6. Open your terminal settings and set the font to **Bitstream Vera Sans Mono Nerd Font**.

---

With these steps completed, your Linux development environment is now set up with a customized Bash prompt and a better font for improved readability. This setup mirrors the look and feel of the Windows environment for a consistent experience across platforms.