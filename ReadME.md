
#  Simple Terminals for Viper

This repository provides a simple terminal interface for Viper, utilizing USB communication on Linux OS. It includes the necessary components to compile and link the system for usage.

## Dependencies

- **g++**: Compiler to build the C++ files.
- **libusb-1.0**: USB library required for communication.
- **pthread**: For multi-threading.

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

MIT
