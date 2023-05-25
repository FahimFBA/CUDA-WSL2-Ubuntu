# Setup Windows Machine for ML/DL Using CUDA (Nvidia RTX GPU)

This is a complete guideline that I use to set up my computer for CUDA specific workload on my Windows machine via WSL2.


<details>
<summary> :arrow_right_hook: If you are also interested about my current specification that I use for this task. </summary>

Processor: Ryzen 5 3500X 6 Core and 6 Threads <br>
RAM: 32GB DDR4 3200MHz (16 GB + 8 GB + 8 GB) <br>
GPU: Zotac RTX 3050 8GB GDDR6 <br>
Motherboard: Gigabyte B450M Aorous Elite <br>
Monitor: MSI Optix G24 Gaming Curved 75Hz <br>

Fun fact! I hate RGB!
</details>

For this guideline, I will be using the Windows 11 Pro (Version 22H2) and WSL2 (of course!).

## Step 1: Internet & Electricity

This whole processes can take a lot of time. Therefore, make sure to ensure proper connectivity of the internet and the electricity. For me, it took almost 7 hours in total. You would also need to download some pretty huge packages along the way.

## Step 2: Latest PowerShell

I will be using the latest PowerShell. You can download that from the Microsoft store, but I will download from the official website as the store might create some problems later.
Go to [the official website](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows). This normally redirects you to the latest version of PowerShell available on that moment. For me, the latest version is 7.3 (24 May 2023). For you, it might be the updated version. Don't worry about that. Simply download the latest stable version.

1. Click on **Download PowerShell** button. <br> ![Download Powershell button](img/1.png)
2. Find the latest PowerShell of `win-x64.msi`. Download that. <br> ![latest powershell msi file](img/2.png)
3. The installation process is pretty straightforward. However, I will be guiding you througout the entire processes. Double click on the downloaded file. Then click `Next`. <br> ![msi software](img/3.png)
4. Keep everything as it is and click `Next`. <br> ![Next step](img/4.png)
5. I still prefer to keep everything as it is and simply click `Next`. <br> ![Next step](img/5.png)
6. I still prefer to keep everything as it is and simply click `Next`. <br> ![Next step](img/6.png)
7. Click `Install`. <br> ![Install](img/7.png)
8. Now click `Finish`. <br> ![Finish](img/8.png)


## Step 3: Windows Terminal

I really like the Windows Terminal as I can simply switch to any other WSL OSes (Ubuntu, Kali, Git Bash, etc.) whenever I want. But before proceeding further, I have to make sure that my current Windows Terminal is the updated one.

1. Open the **Microsoft Store** and search for `Windows Terminal`. <br> ![Windows Terminal on Microsoft Store](img/9.png)
2. Click on `Update` if it needs the update. 
3. Make sure that you are on the latest updated Windows Terminal already.
4. Now open the Windows Terminal, and we have to change some settings first. Click on `Open Settings`. <br> ![Windows Terminal Settings Customization](img/10.png)
5. If you do not see the `Open Settings` prompt, then simply click the drop-down arrow, and click on `Settings`. <br> ![Settings](img/11.png)
6. From `Startup`, make sure that the **Default profile** is set on `PowerShell` (The new PowerShell we installed in [Step 2](#step-2-latest-powershell)). The `Default terminal appplication` should be set on `Windows Terminal`. <br> ![Default startup config](img/12.png)
7. Then click `Save` and exit the terminal. <br> ![Save](img/13.png)

## Step 4: Hardware Virtualization

For using the WSL, we have to make sure that our CPU virtualization is enabled. You can check the status through your task manager. <br> ![Virtualization](img/14.png)

## Step 5: WSL & Ubuntu LTS

Now we need to install the WSL2 and Ubuntu LTS.

1. Open the Windows Terminal as an **Administrator**. <br> ![Open terminal as an administrator](img/15.png)
2. For installing the **WSL**, use the command `wsl --install`. <br> ![VMP install](img/16.png) <br> ![WSL install](img/17.png)
3. Then, it would automatically install the latest LTS version of Ubuntu. <br> ![Ubuntu install](img/18.png)
4. After the tasks get finished, it would prompt you for rebooting your PC. Save other works and simply restart your computer. <br> ![Reboot PC](img/19.png)
5. After restarting the PC, it would automatically open the terminal and ask you for the username and password for your Linux OS. <br> ![After rebooting PC](img/20.png)
6. Give the Username and Password. Make sure to use the same Password on Retype Password! <br> ![username and password](img/21.png)
7. After a while, it will install the necessary components. <br> ![Complete Ubuntu](img/22.png)
8. Now, make sure that **WSL2** becomes the default WSL in this terminal. Apply the command, `wsl --set-default-version 2`. <br> ![WSL 2 default](img/23.png)
9. If you want to check the WSL OSes status (How many of OSes are available, how many of them are running or stopped), use the command, `wsl --list --verbose`. <br> ![OSes status](img/24.png) <br> Here, it is telling me that I have **Ubuntu** installed on my WSL version 2 and it is currently stopped.
10. However, after working on a WSL OS, if you want to shut down the OS, then you can use the command `wsl -t distro_name`. For me, it is Ubuntu, therefore, I used `wsl -t Ubuntu`. `t` represents the **termination** command here. ![Terminate command](img/25.png)
11. If you have multiple OSes in WSL, and if you want to run any specific distribution, then use the command `wsl --distribution distribution_name`. For example, if I want to run Ubuntu specifically, the command would be `wsl --distribution Ubuntu`. If you only have one distribution, then you do not necessarily need to worry about this at all. <br> ![run specific distro](img/26.png)
12. You can simply use `exit` to exit a distro from the terminal. It might not necessarily shut down the distribution. You have specifically use the termination command for that. However, some regularly used commands are here. <br> ![regularly used command](img/27.png)
13. After installing a distribution, you would also be able to see and go there by using the drop-down menu from the Windows Terminal. <br> ![drop-down menu for other distributions](img/28.png)

## Step 6: Configure Ubuntu LTS

We need to update and install some apps now.

1. Open Ubuntu by using any method inside the Windows Terminal. You can obviously use the dedicated **Ubuntu App**. But I always prefer the Terminal as I can use multiple different distributions and command line applications here altogether. <br> ![start Ubuntu](img/29.png)
2. Update the system by using the command `sudo apt update`. <br> ![update](img/30.png)
3. If you get errors in updating/upgrading saying it can't reach to the server then change the nameserver with the command `echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
`.
4. After updating, upgrade the system using `sudo apt upgrade`. <br> ![Upgrade](img/31.png) <br> ![Upgrade system](img/32.png) <br> You can clear the terminal by using the `clear` command.
5. CUDA works with C. Thus, we need to install the gcc compiler first. Use the command `sudo apt install gcc --fix-missing`. <br> ![gcc](img/33.png) <br> ![gcc installing](img/34.png) <br> ![finishing installation](img/35.png)