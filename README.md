<p align="center"><img alt="JavaScript With Fahim Banner" src="img/Banner.png"></p>

<h3 align="center"><b>Setup Windows Machine for ML/DL Using Nvidia Graphics Card (CUDA)</b></h3>

<br>

> **Follow [@Fahim_FBA](https://twitter.com/Fahim_FBA) on Twitter to learn more about it**.

<br>

This is a complete guideline that I use to set up my computer for CUDA specific workload on my Windows machine via WSL2.

<br>

<h3 align="center"><b>Make sure to :star: <a href="https://github.com/FahimFBA/CUDA-WSL2-Ubuntu">this</a> repository if you liked it!</b> </h3>

<br>

<h3 align="center">This repo is hosted at <a href="https://fahimfba.github.io/CUDA-WSL2-Ubuntu/">fahimfba.github.io/CUDA-WSL2-Ubuntu</a></h3> <br>


<details>
<summary> :arrow_right_hook: If you are also interested about my current specification that I use for this task. </summary>

* Processor: Ryzen 5 3500X 6 Core and 6 Threads <br>
* RAM: 32GB DDR4 3200MHz (16 GB + 8 GB + 8 GB) <br>
* GPU: Zotac RTX 3050 8GB GDDR6 <br>
* Motherboard: Gigabyte B450M Aorous Elite <br>
* Monitor: MSI Optix G24 Gaming Curved 75Hz <br>

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
3. The installation process is pretty straightforward. However, I will be guiding you throughout the entire process. Double click on the downloaded file. Then click `Next`. <br> ![msi software](img/3.png)
4. Keep everything as it is and click `Next`. <br> ![Next step](img/4.png)
5. I still prefer to keep everything as it is and simply click `Next`. <br> ![Next step](img/5.png)
6. I still prefer to keep everything as it is and simply click `Next`. <br> ![Next step](img/6.png)
7. Click `Install`. <br> ![Install](img/7.png)
8. Now click `Finish`. <br> ![Finish](img/8.png)


## Step 3: Windows Terminal

I really like the Windows Terminal as I can simply switch to any other WSL OSes (Ubuntu, Kali, Git Bash, etc.) whenever I want. But before proceeding further, I have to make sure that my current Windows Terminal is the updated one.

1. Open the **Microsoft Store** and search for `Windows Terminal`. <br> ![Windows Terminal on Microsoft Store](img/9.png)
2. Click on `Update` if it needs an update. 
3. Make sure that you are on the latest updated Windows Terminal already.
4. Now open the Windows Terminal, and we have to change some settings first. Click on `Open Settings`. <br> ![Windows Terminal Settings Customization](img/10.png)
5. If you do not see the `Open Settings` prompt, then simply click the drop-down arrow, and click on `Settings`. <br> ![Settings](img/11.png)
6. From `Startup`, make sure that the **Default profile** is set on `PowerShell` (The new PowerShell we installed in [Step 2](#step-2-latest-powershell)). The `Default terminal application` should be set on `Windows Terminal`. <br> ![Default startup config](img/12.png)
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
9. If you want to check the WSL OSes status (How many OSes are available, how many of them are running or stopped), use the command, `wsl --list --verbose`. <br> ![OSes status](img/24.png) <br> Here, it is telling me that I have **Ubuntu** installed on my WSL version 2 and it is currently stopped.
10. However, after working on a WSL OS, if you want to shut down the OS, then you can use the command `wsl -t distro_name`. For me, it is Ubuntu, therefore, I used `wsl -t Ubuntu`. `t` represents the **termination** command here. ![Terminate command](img/25.png)
11. If you have multiple OSes in WSL, and if you want to run any specific distribution, then use the command `wsl --distribution distribution_name`. For example, if I want to run Ubuntu specifically, the command would be `wsl --distribution Ubuntu`. If you only have one distribution, then you do not necessarily need to worry about this at all. <br> ![run specific distro](img/26.png)
12. You can simply use `exit` to exit a distro from the terminal. It might not necessarily shut down the distribution. You can specifically use the termination command for that. However, some regularly used commands are here. <br> ![regularly used command](img/27.png)
13. After installing a distribution, you would also be able to see and go there by using the drop-down menu from the Windows Terminal. <br> ![drop-down menu for other distributions](img/28.png)

## Step 6: Configure Ubuntu LTS

We need to update and install some apps now.

1. Open Ubuntu by using any method inside the Windows Terminal. You can obviously use the dedicated **Ubuntu App**. But I always prefer the Terminal as I can use multiple different distributions and command line applications here altogether. <br> ![start Ubuntu](img/29.png)
2. Update the system by using the command `sudo apt update`. <br> ![update](img/30.png)
3. If you get errors in updating/upgrading saying it can't reach to the server then change the nameserver with the command `echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null`.
4. After updating, upgrade the system using `sudo apt upgrade`. <br> ![Upgrade](img/31.png) <br> ![Upgrade system](img/32.png) <br> You can clear the terminal by using the `clear` command.
5. CUDA works with C. Thus, we need to install the gcc compiler first. Use the command `sudo apt install gcc --fix-missing`. <br> ![gcc](img/33.png) <br> ![gcc installing](img/34.png) <br> ![finishing installation](img/35.png)

## Step 7: CUDA

Now it is time to install CUDA from the [official website of Nvidia](https://developer.nvidia.com/cuda-downloads). 

Make sure to select the following: <br>
**Operating System**: Linux <br>
**Architecture**: x86_64 <br>
**Distribution**: WSL-Ubuntu <br>
**Version**: 2.0 <br>
**Installer Type**: deb(local) <br> 
<br> 

![Nvidia - CUDA](img/36.png) 

<br>

This will provide the necessary commands. <br> ![commands CUDA](img/37.png) <br> Now your task would be to apply each command serially in the WSL Ubuntu terminal. Make sure to use the first command twice. It normally resolves the problem keyring later.

<br>

Also, keep in mind that these commands might get changed later. Therefore, always follow the official website. For this guideline, I will be using the exact command I used to set up the CUDA in my machine. <br>

1. `wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin` <br> ![1st command](img/38.png) <br> I used the same command again after finishing the previous transactions.
2. `wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin` <br> ![1st command](img/39.png) <br>
3. `sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600` <br> ![2nd Command](img/40.png) <br>
4. `wget https://developer.download.nvidia.com/compute/cuda/12.1.1/local_installers/cuda-repo-wsl-ubuntu-12-1-local_12.1.1-1_amd64.deb` <br> ![3rd command](img/41.png) <br> This normally takes a lot of time as it downloads a large file (above 2GB file size). <br> ![large file](img/42.png)
5. `sudo dpkg -i cuda-repo-wsl-ubuntu-12-1-local_12.1.1-1_amd64.deb` <br> ![4th command](img/43.png)
6. `sudo cp /var/cuda-repo-wsl-ubuntu-12-1-local/cuda-*-keyring.gpg /usr/share/keyrings/` <br> ![5th command](img/44.png)
7. Then update the system using `sudo apt-get update`. <br> ![update system](img/45.png) <br> ![updating](img/46.png)
8. `sudo apt-get -y install cuda`. <br> ![install CUDA](img/47.png) <br> ![finish CUDA installation](img/48.png)

## Step 8: Post installation

The [official CUDA installation guide from Nvidia](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html) tells us to add `export PATH=/usr/local/cuda-12.1/bin${PATH:+:${PATH}}` to the **PATH** variable. <br> ![path](img/49.png) <br> I have changed the CUDA version `cuda-12.1` according to my installed CUDA version. Make sure to do the same for your updated CUDA version. <br>

Do the following to do that:

1. Open Ubuntu in the Windows Terminal.
2. Go to root directory using `cd ~`. Then open the `bashrc` in nano using `nano .bashrc` <br> ![root](img/50.png)
3. Go to at the end of the file and copy-paste the path there. For me, the path is `export PATH=/usr/local/cuda-12.1/bin${PATH:+:${PATH}}`. <br> ![path](img/51.png) <br> Then use `Ctrl` + `X` to close. Make sure to use `Y` to save in the same file.
4. To apply the changes, use `source ~/.bashrc`. You can check the path using `echo $PATH`. <br> ![path check](img/52.png)

## Step 9: Nvidia CUDA Toolkit

Install the Nvidia Cuda Toolkit using `sudo apt install nvidia-cuda-toolkit`. <br> ![toolkit 1](img/53.png) <br> ![toolkit 2](img/54.png) <br>

You can check the Driver and CUDA version using `nvidia-smi`. <br> ![smi](img/55.png) <br>

Also make sure to check whether the Nvidia Cuda Compiler Driver has installed or not by using `nvcc -V`. <br> ![nvcc](img/56.png)

## Step 9: PIP

* Ensure that you have python3 installed in your system. You can check the version using `python3 --version`. If that says that "python3 is not found" or something like that, then install python.
* Install **PIP** using `sudo apt-get install python3-pip`. <br> ![pip install](img/57.png)

## Step 10: PyTorch

For installing the PyTorch, go to the [official website of PyTorch](https://pytorch.org/get-started/locally/). Then make sure to select the relevant sections. After that, it will provide you a command. You have to use the command in your Ubuntu terminal. <br>

For me, the selections were:

* PyTorch Build: Stable (2.0.1) - Make sure to select the latest stable version always
* Your OS: Linux
* Package: Pip
* Language: Python
* Computer Platform: CUDA 11.8 - Make sure to select the latest available CUDA version

After that, I got the command `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118`. <br> ![PyTorch command](img/58.png) <br>

I simply used that exact command in my Ubuntu terminal. <br> ![PyTorch command](img/59.png) <br>

It also downloads a large file that can take a lot of time if you have a slower internet connection like me! <br> ![PyTorch download](img/60.png)

## Step 11: CUDA availability

You can directly check whether your CUDA has been installed or not by running two lines of Python code in the terminal.

* Run Python in terminal using `python3`.
* Import torch using `import torch`.
* Check the CUDA availability using `torch.cuda.is_available()`.

<br>

If it retursn `True`, then you have successfully finished installing CUDA on your system! <br> ![cuda yes](img/61.png)

## Step 12: Nvidia Developer Settings

You have to enable the Nvidia Developer Settings for using CUDA via WSL. Simply follow the procedures:

1. Open the **Nvidia Control Panel**. <br> ![nvidia control panel](img/62.png)
2. Click "Agree and Continue". <br> ![agree](img/63.png).
3. In the Nvidia Control Panel, Click Desktop > Enable Developer Settings. If the "Enable Developer Settings" does not have any check mark, then click on that to enable that feature. <br> ![not check mark](img/64.png) <br> ![check mark](img/65.png)
4. The **Developer** section will be visible. Click on **Manage GPU Performance Counters**. <br> ![GPU counters](img/66.png)
5. Check the radio button on "Allow access to the GPU performance counters to all users". <br> ![check](img/67.png)
6. Click "Apply" and "Yes" to approve the changes permanently. <br> ![approve changes](img/68.png)
7. At the end, it should look like this. <br> ![final](img/69.png)
8. You can again check the CUDA availability like earlier. <br> ![cuda availability](img/70.png)
   
## Step 12: Jupyter Notebook

I normally prefer the Jupyter Notebook. It is true that you can install that in various way, like `pip install notebook`. <br> ![notebook 1](img/71.png) <br> ![notebook 2](img/72.png) <br>

But I prefer the command `pip install jupyter notebook`. <br> ![jupyter notebook](img/73.png) <br>

To open a Jypyter Notebook, you can simply use `jupyter notebook` in the terminal. <br> ![notebook cli](img/74.png) <br>

The notebook will open instantly and you can use the given URL to open that in your web browser like me! <br> ![open notebook in browser](img/75.png)


## Step 13: Test

I ran two codes to check the performance of my CUDA.

1. Open a Python3 script in notebook. <br> ![open script](img/76.png)
2. I used the following code to check whether it is using my CPU or CUDA from GPU.

```python
import torch

if torch.cuda.is_available():
    device = torch.device("cuda")
else:
    device = torch.device("cpu")
print("using", device, "device") 
```

<br> ![cuda](img/77.png)

3. For the performance comparison between my CPU and GPU (CUDA), I used the following code.

```python
import time

matrix_size = 32*512

x = torch.randn(matrix_size, matrix_size)
y = torch.randn(matrix_size, matrix_size)

print("************* CPU SPEED *******************")
start = time.time()
result = torch.matmul(x, y)
print(time.time() - start)
print("verify device:", result.device)

x_gpu = x.to(device)
y_gpu = y.to(device)
torch.cuda.synchronize()

for i in range(3):
    print("************* GPU SPEED *******************")
    start = time.time()
    result_gpu = torch.matmul(x_gpu, y_gpu)
    torch.cuda.synchronize()
    print(time.time() - start)
    print("verify device:", result_gpu.device)
```

![CPU vs GPU](img/78.png)

<br> I also made side by side comparisons between the [Google Colab](https://colab.research.google.com/) and my computer. You can check them as well!

| Try | Google Colab                                                                                                      | My Computer                                                                               |
| --- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| 1   | [Google Colab]([GoogleCollab1.ipynb](https://github.com/FahimFBA/CUDA-WSL2-Ubuntu/blob/main/GoogleCollab1.ipynb)) | [My PC](https://github.com/FahimFBA/CUDA-WSL2-Ubuntu/blob/main/CUDA%20_TEST_Fahim1.ipynb) |
| 2   | [Google Colab](https://github.com/FahimFBA/CUDA-WSL2-Ubuntu/blob/main/GoogleCollab2.ipynb)                        | [My PC](https://github.com/FahimFBA/CUDA-WSL2-Ubuntu/blob/main/CUDA%20_TEST_Fahim2.ipynb) |

The result already states that my PC is working better than the Google Colab!

## Step 14: Remove CUDA Deb file

If you think that you do not need the CUDA deb file anymore, then you can remove that using the following command.

```bash
rm filename
```

For me it was,

```bash
rm cuda-repo-wsl-ubuntu-12-1-local_12.1.1-1_amd64.deb
```

It does not remove the CUDA from your system. It just removes the deb file from your system.

<br> ![remove deb](img/79.png)

## Conclusion

I hope that you have successfully installed CUDA on your Windows 11 system using WSL2. If you have any questions, feel free to reach out to me, or create issues. I will try my best to answer them. <br>