## Setup msys64, git, anaconda in Windows

This is for 64bit Windows only!

## MSYS2

1. Install 64bit version [MSYS2](https://www.msys2.org/) under C:\msys64

2. Open Start->MSYS2 64bit->MSYS2 MSYS

3. In msys bash shell execute the following commands
    Update the package database and core system packages with:
    ```
    pacman -Syu
    ```
    If needed, close MSYS2, run it again from Start menu. Update the rest with:
    ```
    pacman -Su
    ```

4. To customize your bash, copy the following line in [.bashrc](msys64/home/username/.bashrc) to the same path (with your \[username\]) on your computer:
    ```
    export PS1="\[\033[1;35m\]\u@\h \[\033[1;33m\]\w\[\033[1;36m\]\$(parse_git_branch)\]"$'\n'"\[\e[m\]> "
    ```
    Google and play with the attributes to further customize it

Refer to msys2 github page for more information https://github.com/msys2/msys2/wiki/Using-packages


