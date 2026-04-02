# codespaces-vnc
Virtual linux computer with GitHub codespaces

This repository now includes a devcontainer config so Codespaces uses the provided Docker image.

### How to run
- Fork the repo
- Create a new codespace from the repo
- If you already had a codespace open before this change, run `Rebuild Container` once from the Command Palette.
- Once the codespace is fully loaded, run `gp-vncsession` in the terminal
   - Wait for the program to fully finish
   - port `6080` should open and link to the noVNC dashboard

### Troubleshooting
- If `gp-vncsession: command not found`, your codespace is not using this repo's devcontainer image yet.
  - Run `Rebuild Container` from the Command Palette.
  - Or delete the existing codespace and create a new one.
- Verify with `cat /etc/os-release` and `which gp-vncsession`.


### Firefox
If you want to browse the web, install Firefox directly instead of using Snap. Codespaces containers do not support Snap, so `sudo apt-get install firefox` can fail by trying to pull a snap package.

Run these commands in the terminal:

```bash
cd /tmp
wget -O firefox.tar.xz "https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-US"
tar -xJf firefox.tar.xz
sudo mv firefox /opt/firefox
sudo ln -sf /opt/firefox/firefox /usr/local/bin/firefox
```

After that, run `firefox` from the terminal and it should open in the desktop.
