## Setup msys64, git, gcc, anaconda in Visual Studio Code on Windows

This is for 64bit Windows only!  
The folder structure in this repo is setup the same way as your computer should be under C:\\. All path with \[username\] should be substituted with your own username.

## MSYS2

1. Install 64bit version [MSYS2](https://www.msys2.org/) under C:\msys64

2. Open Start->MSYS2 64bit->MSYS2 MSYS

3. In msys bash shell, execute the following commands  
    Update the package database and core system packages with:
    ```
    pacman -Syu
    ```
    If needed, close MSYS2, run it again from Start menu. Update the rest with:
    ```
    pacman -Su
    ```

4. To customize your bash, copy the following line from [`.bashrc`](msys64/home/username/.bashrc) to the same file on your computer:
    ```
    export PS1="\[\033[1;35m\]\u@\h \[\033[1;33m\]\w\[\033[1;36m\]\$(parse_git_branch)\]"$'\n'"\[\e[m\]> "
    ```
    Google and play with the attributes to further customize it

Refer to msys2 github [page](https://github.com/msys2/msys2/wiki/Using-packages) for more information

## Git

1. Open msys bash and run:
    ```
    pacman -S git
    ```

2. Follow [this](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) tutorial to create your SSH key and add it to your source control server

3. Copy [`sshagent.sh`](msys64/home/username/sshagent.sh) to the same path on your computer

4. In your msys64/home/username/.bash_profile, add the following code from [`.bash_profile`](msys64/home/username/.bash_profile):
    ```
    # source the sshagent.sh if it exists
    if [ -f "${HOME}/sshagent.sh" ] ; then
        source "${HOME}/sshagent.sh"
    fi
    ```
5. Relaunch msys bash. Your SSH agent should automatically launch with your shell.

## GCC

## Anaconda

1. Install 64bit [Anaconda](https://www.anaconda.com/distribution/)

2. Remember your path to Anaconda. In my case, I installed for all users. Therefore, my path is C:\\ProgramData\\Anaconda3. I will use this path as the example in the following guide.

3. To use conda in your bash, add the following code from [`.bashrc`](msys64/home/username/.bashrc) to the same file on your computer:
    ```
    # Anaconda
    # Activate virtual environment
    source /c/ProgramData/Anaconda3/Scripts/activate
    ```
4. Open a new bash shell, you should see `"(base)"` conda environment is activated

4. In your bash, run:
    ```
    conda info
    ```
    If `conda` is not recognized as a command, you might need to add Anaconda to system PATH
