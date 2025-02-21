
#  Simple Terminal Tool for Viper

This repository provides a simple terminal interface for Viper, utilizing USB communication on **Linux OS**. 

It includes the necessary components to compile and link the system for usage.

## Additional OS Info

### For Windows User

The official SDK web source provided by Polhemus can be found at [HERE](https://ftp.polhemus1.com/hidden/Viper/Software/SDK/). 

You may want to check out the VPcmdIF web documentation and VPcmdIF libraries (first download link), which include a command-line software that utilizes the .dll dependency to extract data from Viper.

### For Linux User

Additionally, my modified repository, which publishes POSE data as a ROS2 topic, can be found at [this repo](https://github.com/enhanced-telerobotics/viper_cpp). This version has only been tested on ROS 2 Humble with Ubuntu 22.04.

## Dependencies

- **g++**: Compiler to build the C++ files.
- **libusb-1.0**: USB library required for communication.
- **pthread**: For multi-threading.

## **Polhemus Viper USB udev Rule Setup**

This guide explains how to set up a **udev rule** to grant proper permissions for the Polhemus Viper device on a Linux system.

### **1. Create the udev Rule**
Run the following command to create the rule file:  
```bash
echo 'SUBSYSTEM=="usb", ATTRS{idVendor}=="0f44", ATTRS{idProduct}=="bf01", MODE="0666"' | sudo tee /etc/udev/rules.d/99-polhemus-viper.rules
```

### **2. Apply the Rule**
Reload and apply the new udev rule:
```bash
sudo udevadm control --reload-rules
sudo udevadm trigger
```

### **3. Verify the Device**
Unplug and reconnect the device, then check if the rule is applied:
```bash
ls -l /dev/bus/usb/*/*
udevadm info -q all -n /dev/bus/usb/001/003  # Replace with correct bus/device number
```

### **4. Restart udev (if needed)**
If the rule does not apply automatically, restart the udev service:
```bash
sudo systemctl restart udev
```

Now, the Polhemus Viper device should automatically get the correct permissions when plugged in.
## Files

- **main.cpp**: The main entry point for the program.
- **viper_queue.cpp**: Manages the queue for Viper data.
- **viper_ui.cpp**: User interface for interacting with Viper.
- **viper_usb.cpp**: Handles USB communication with the Viper device.

## Compilation

1. **To compile the program:**

   Run the following command:

   ```bash
   make
   ```

   This will build the executable `vpr_simp_term` using the object files generated from the source files.

2. **To clean the project:**

   Run the following command:

   ```bash
   make clean
   ```

   This will remove any generated object files and temporary files (e.g., `*~`).

## Usage

After compilation, you can run the `vpr_simp_term` executable to interact with the Viper system.

## License

No license, public avaliable.
