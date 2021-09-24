###Cryptocurrency Python HW
##A hierarchical deterministic(HD) wallet is a digital wallet commonly used to store the keys for holders of cryptocurrencies such as Bitcoin and Ethereum. HD wallets enable a series of key pairs to be created from one random seed, providing convenience and manageability as well as high-level security.
#HD wallets are cryptocurrency wallets that can generate public and private addresses (keys) randomly from a single seed key. They use a pattern that prevents other users from guessing your combinations and passwords.

##How HD Wallets work...
#If you use a cryptocurrency wallet to store your tokens, you need a public address to receive funds and a private key for spending the funds. Thanks to this public/private combination of keys, wallets can ensure the safety of your tokens and the privacy of all your transactions.

However, the number of combinations grows with every new transaction you do, making storage and backup more complicated with every new purchase.

Without a special algorithm in place, it’s unmanageable for users to keep generating new pairs of public/private keys. Especially since every pair that you create also needs to be backed up after the configuration.

HD wallets solve this problem. They use an SHA-256 hash algorithm to produce a tree structure of children addresses without any errors. As a user, you no longer need to create new addresses continually, nor wait for the secure key to be generated.

You only need to take care of the backup, which becomes faster and easier as you can do it using a single seed phrase.Hierarchical deterministic wallets require a single backup that enables the user to fully restore the data at any time in the future. This is because of the wallet’s ability to drive all the private keys of the tree using BIP 32. This is a transfer protocol that enables parent keys to create child keys in a hierarchy.

#### Installation Process

Open a terminal and execute the following commands to install `web3.py` and `bit`, respectively. Windows users **MUST** use the _Anaconda Prompt_ in this section.

* Open the terminal and run the following command to create a brand new Python virtual environment for this unit.

  ```shell
  conda create -n ethereum python=3.7 anaconda
  ```

* Activate the new environment.

  ```shell
  conda activate ethereum
  ```

* Use the `pip install` command to download and install the `web3.py` module.

  ```shell
  pip install web3
  ```

  ![web3-install](Images/web3-install.png)

* Use the `pip install` command to download and install the `bit` module.

  ```shell
  pip install bit
  ```
  ## Verify Installation

Once the `web3.py` and `bit` modules are downloaded and installed, verify that both installations completed successfully. Windows users **MUST** use `git-bash` in this section.

* Use the `conda list package_name` command, substituting `package_name` with `web3` to verify if the `web3` library installed successfully.

  ```shell
  conda list web3
  ```

  ![web3-verify](Images/web3-verify.png)

* Use the `conda list package_name` command, substituting `package_name` with `bit` to verify if the `bit` library installed successfully.

  ```shell
  conda list bit
  ```# HD-Wallet-Derive Install Guide

This guide serves as a step by step process for setting up the [`hd-wallet-derive` library](https://github.com/dan-da/hd-wallet-derive) used to derive `BIP32` addresses and private keys for Bitcoin and other alternative coins or "altcoins."

If you need additional help in the installation process, you can follow the step by step video guides in the following links.

<details><summary>Microsoft Windows Users</summary>

* [Installing PHP Version 7.3 for Windows](https://youtu.be/IvcZZaIEL_4)

* [HD Derive Wallet Install for Windows](https://youtu.be/A_tqm4j4vsY)

</details>

<details><summary>macOS Users</summary>

* [Installing PHP Using the Homebrew Package Manger for Mac](https://youtu.be/SNRQSwlOKbs)

* [HD Derive Wallet Install for Mac](https://youtu.be/c-Qc3Pss6oM)

</details>

## Step 1 - Environment Setup

The `hd-wallet-derive` library is written in the PHP language; therefore, you will be required to first set up PHP on your machines before installing and then running the `hd-wallet-derive` library.

<details><summary>Environment Setup in Microsoft Windows Operating System</summary>

For those with a **Windows operating system**, execute the following steps:

1. Windows machines do not come with a pre-built PHP and Apache Web Server, and therefore will require both. Luckily, some installers bundle these two together! Visit the [XAMPP website](https://www.apachefriends.org/index.html) and download the installer for Windows; the XAMPP is a popular PHP development environment that is easy to install and configure. Be sure to download version 7, as version 8 can cause issues with the `hd-wallet-derive` library.

    <img alt=XAMPP-website src=Images/download_xampp.gif width=700>

2. Use the XAMPP package to install PHP and its associated dependencies. Keep the defaults for now unless there is a dependency conflict.

    <img alt=XAMPP-install src=Images/XAMPP-install.png width=350>

3. Then, once the XAMPP package is installed, navigate to the folder where the PHP binaries are located. This should be at `C:\xampp\php`.

    <img alt=xampp-path src=Images/xampp-path.png width=700>

4. Edit the `php.ini` file (`C:\xampp\php\php.ini`) using Notepad and add the following line at the end of the file: `extension=php_gmp.dll`. This will enable a necessary PHP extension that `hd-wallet-derive` relies on.

   <img alt=edit-php-ini.gif src=Images/edit-php-ini.gif width=700>

5. Next, you need to update the System Environment Variables and add the path containing the PHP binaries (`C:\xampp\php`) to the `PATH` environment variable.

6. For this particular step, we will use the Windows Command Prompt as Administrator as follows: 

      * In the Cortana search field, type in CMD; you will see the Command Prompt application in the search results, choose the "Run as administrator" option to continue.

        <img alt=Open-CMD-as-Admin src=Images/cmd-as-admin.png width=700>

      * You will be asked if you want the Command Prompt to make changes in your system, click on the "Yes" button to continue.

        <img alt=Open-CMD-as-Admin-2 src=Images/cmd-as-admin-2.png width=400>

      * You will be able to run commands as administrator if you see the title `Administrator: Command Prompt` in the window. In the administrator's prompt, it’ll say `Administrator`, while other prompts will not.

        <img alt=Open-CMD-as-Admin-3 src=Images/cmd-as-admin-3.png width=700>

7. In this new terminal, type the following command to update the `PATH` system variable.

    ```shell
    setx /M PATH "%PATH%;C:\xampp\php"
    ```

8. If everything was successful, you will see a confirmation message.

   !<img alt=Open-CMD-as-Admin-4 src=Images/cmd-as-admin-4.png width=700>

9. Test that the newest version of PHP is working. Close all the terminal windows (`git-bash` and Windows Command Prompt), open a new `git-bash` terminal windows, and execute the following command.

    ```shell
    php -version
    ```

10. If you see the following output, then congratulations! Your machine is now updated to the newest version of PHP!

    <img alt=Open-CMD-as-Admin-5 src=Images/cmd-as-admin-5.png width=700>

 ### Troubleshooting

 ---

 If you do not see something similar to the above output when running ` php -version`, or if you see the error `The data being saved is truncated to 1024 characters`, then your environement variables may not be set correctly. Perform the following steps to make sure your environment variables are correctly set:

  1. Click the Windows search and search for `System Properties` or `Edit System`, then launch the application.

  2. Next at the bottom of the dialog click `Environment variables`.

  3. Then under `System Variables` find the `Path` variable and click `edit`.

  4. Now click `New` and enter your XAMP path, e.g.  `C:\xampp\php`.

  5. Finish by clicking `OK` on each window.

  <img alt=System-Properties-Add-environment-Variable src=Images/windows-set-environment_variables.png width=700>

</details>

</details>
 
<details><summary>Environment Setup in macOS Operating System</summary>

For those using **macOS**, execute the following steps:

1. macOS users will need to update their machine's prebuilt version of PHP to the full version using a package manager for macOS called Homebrew.

2. To do this, visit the [Homebrew website](https://brew.sh/) and install Homebrew using the given install command.
   
   <img alt=homebrew-install src=Images/homebrew-install.png width=700>

3. Once Homebrew is installed, execute the following command in your terminal. This should install the latest version of PHP (7.3 at this current time).

    ```shell
    brew install php@7.3
    ```

4. Next, execute the command appropriate for your system:

    * macOS Catalina and above (`zsh` shell):

      ```shell
      echo "export PATH=/usr/local/opt/php@7.3/bin:$PATH" >> ~/.zshrc
      ```

    * Versions prior to macOS Catalina (`bash` shell):

      ```shell
      echo "export PATH=/usr/local/opt/php@7.3/bin:$PATH" >> ~/.bash_profile
      ```

    * **Note:** If you are on macOS Catalina and up (10.15+), your default shell is now `zsh`, instead of `bash` as in previous versions. No worries, however, since `zsh` can handle the same tasks. If you have yet to upgrade to Catalina, you will be using `bash` as your default shell, which will affect the commands you need to run. Make sure you are running the commands appropriate for your system!  

5. **Close the terminal**. 

6. Open a **NEW** terminal, then verify that PHP version 7.3 is the current version in your system by executing the following command:

    ```shell
    php -version
    ```

7. If you see the following output, then congratulations! Your machine is now updated to the newest version of PHP!

   <img alt=PHP-macOS-install-3 src=Images/php-os-x-3.png width=700>

</details>



## Step 2 - Installing hd-wallet-derive 

With the latest version of PHP installed on our machines, we can now proceed to the installation of the `hd-wallet-derive` library.

<details><summary>Installation</summary>

1. Begin by opening a fresh terminal. Windows users **must** open their terminal as administator as follows:

    * Input `C:\Program Files\Git\bin\bash.exe` directly into the system search bar and launch the program as _Administrator_ from the resulting menu. 
    
    * **This step is required or the installation will fail!**

    * <img alt=bash-exe.png src=Images/bash-exe.png height=500>

2. With your terminal open as indicated for your operating system, cd into your `Blockchain-Tools folder and run the following code:

    ```shell
      git clone https://github.com/dan-da/hd-wallet-derive
      cd hd-wallet-derive
      curl https://getcomposer.org/installer -o installer.php
      php installer.php
      php composer.phar install
    ```

3. You should now have a folder called `hd-wallet-derive` containing the PHP library!

## Troubleshooting macOS hd-wallet-derive

If you run into an issue with the installation of `hd-wallet-derive` due to `php extension gmp` missing on macOS installation of PHP, here are the steps to resolve:

1. Run the command `brew unlink php@7.3` this unlinks the current version of PHP running on mac. 

2. Run the command `brew upgrade php@7.3` this will update your current version of PHP to the latest version of `php7.3.x`. 
  - If you receive the message that PHP `7.3.x` version is already installed proceed to the next step.

3. Run the command `brew link php@7.3 --overwrite` this will relink the corresponding path and connect the extensions (including gmp).

4. With your terminal open as indicated for your operating system, cd into your `Blockchain-Tools folder and run the following code:

    ```shell
      git clone https://github.com/dan-da/hd-wallet-derive
      cd hd-wallet-derive
      curl https://getcomposer.org/installer -o installer.php
      php installer.php
      php composer.phar install
    ```

</details>

<details><summary>Verification</summary>

1. Run the command to `cd` in your `hd-wallet-derive` folder.

2. Once you've confirmed your are in your `hd-wallet-derive` folder, execute the following command:

    ```shell
    ./hd-wallet-derive.php -g --key=xprv9tyUQV64JT5qs3RSTJkXCWKMyUgoQp7F3hA1xzG6ZGu6u6Q9VMNjGr67Lctvy5P8oyaYAL9CAWrUE9i6GoNMKUga5biW6Hx4tws2six3b9c --numderive=3 --preset=bitcoincore --cols=path,address --path-change
    ```

3. If installation was successful, you should see output similar to what you see in the following image:

