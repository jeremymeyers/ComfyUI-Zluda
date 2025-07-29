## ALTERNATE OLD VERSION INSTALLATION

If the new install version gives you issues, use this method.

### Step 1: AMD HIP SDK
This app installs zluda for HIP SDK 5.7.1 by default.
*If you have a high-end GPU and want to use miopen and triton (experimental), skip these instructions and go to the High-End GPU sefction*

Install **HIP SDK 5.7.1** from [AMD.com](https://www.amd.com/en/developer/resources/rocm-hub/hip-sdk.html). You are looking for "Windows 10 & 11 5.7.1 HIP SDK". Then move on to the next step.



### Step 2: Set Environment Variables
To open the Environment Variables control panel, press Windows Key+R to open the Run menu and enter
```bash
rundll32.exe sysdm.cpl,EditEnvironmentVariables
```

1. In the System Variables box (on the bottom half) 
- Add the variable "HIP_PATH" with the value `C:\Program Files\AMD\ROCm\x.x\`  (where your version of the SDK was installed.
- Double click on "Path" (be sure you're editing system and not users)
- Hit "New" and add 'C:\Program Files\AMD\ROCm\x.x\bin` (where your version of the SDK is installed) *(Note the \bin at the end)*
- 

### Step 3: Patch ZLUDA 

To use 5.7.1 (default)  run
```bash
`patchzluda.bat'
```

To use HIP 6.x

Copy ZLUDA download link from [lshyqqtiger's ZLUDA Fork] https://github.com/lshqqytiger/ZLUDA/releases) to your clipboard (it will look something like `https://github.com/lshqqytiger/ZLUDA/releases/download/rel.d60bddbc870827566b3d2d417e00e1d2d8acc026/ZLUDA-windows-rocm6-amd64.zip`

Then run
```bash
patchzluda2.bat
```
and paste the URL to download and install the appropriate patch.

Reboot your PC.

### Step 4: Installation

From the start menu, launch Command Prompt (Powershell won't work correctly).

Navigate to the directory in which you want to install the app (best to use a root directory, do not install to a Windows Restricted folder like Program Files or your user directory.)

```bash
git clone https://github.com/patientx/ComfyUI-Zluda
```

```bash
cd ComfyUI-Zluda
```

```bash
install.bat
```
To run, 
```bash
comfyui.bat
```

Note: The first time you run the app, it will build a database and compile for your GPU. This may take up to 10 minutes without a prompt, so just let it run.

### Repairing ZLUDA
If for any reason your ZLUDA install gets changed or corrupted (for instance with ZLUDA, torch or graphics driver version changes, you can restore it to base install settings by running

```bash
patchzluda.bat
```
