# ✅ Pre-Installation Checklist for Windows OS
Before creating a bootable USB and installing Windows on your laptop, make sure to go through the following steps:

### ⚙ 1. Backup Important Data
- Backup all important and personal files from the laptop, especially `Desktop` and `Download` folder of C drive.
- Use usb drive or cloud storage or any other drive (except c drive) if have.

### 🖥 2. Check Laptop Compatibility
- Make sure there is at least 64GB storage (for windows 11) free space. [Larger is better] 
- Minimum 4GB of RAM (8GB is recommended).
- Check system firmware **(UEFI / Legacy BIOS)**:
    - Enter BIOS (usually - F2, Del, Esc) on startup and Check firmware

    - `or`

    - #### Check current disk partition type: (Gpt=UEFI, Mbr=Legacy)
        - open terminal(admin) or powershell(admin) and run the commnads: `diskpart` > `list disk`.
    
    - #### **Decide the partition plan:**
        - if the disk has * in Gpt, then the partition type supports **UEFI** bios system, hence the partition type will be **GPT**.
        - if the disk doesn't have * in Gpt, the partition type will be **MBR**.

### 🧰 3. Download ISO & Tools
- Download the latest official Windows ISO ([Windows 11 ISO from Microsoft](https://www.microsoft.com/en-us/software-download/windows11)).
- Use tools like [**Rufus**](https://rufus.ie/en/) or [**Ventoy**](https://www.ventoy.net/en/download.html) to create a bootable USB.
    - usb pendrive must be of 8GB or more.
    - format the usb to **FAT32** for UEFI or **NTFS** for legacy BIOS before making it bootable.