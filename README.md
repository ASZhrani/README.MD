

# Quest2XInput

**Quest2XInput** is a C++ Meta Quest to Xbox Controller Input Converter code that designed to convert the input signals from Meta Quest 2 and Meta Quest 3 controllers into normal Xbox controller inputs. This allows you to use your Meta Quest controllers for games and applications that support Xbox controllers on Windows. This project is aimed at junior developers who are interested in input mapping and game development.

## Problem Project Aims To Solve

When you connect the VR headset to a Windows device using the Meta Quest Link app (the only way to connect Meta Quest controllers to Windows), you can only play games specifically designed for the Meta Quest controller.

With **Quest2XInput**, you can play any game using the Meta Quest controllers!

> [!IMPORTANT]
>  Unfortunately, **Quest2XInput** is not supported on **Linux** and **macOS** since Meta does not provide a way to connect Meta Quest headsets to these operating systems.
 However, you can still run **Quest2XInput** on **Linux**, as it is essentially a codebase.

<br>

## Key Features

- **Controller Input Mapping**: Maps Meta Quest controller inputs to Xbox controller inputs seamlessly.
- **Simple Installation**: Easy to set up using CMake.
- **Custom Input Profiles**: Create and use custom profiles for different games.
- **Optional Scripting**: Integrate scripts for advanced functionality and automation.

## Installation Guide

### Prerequisites

Make sure you have the following installed:

- CMake
- A C++ compiler
- **ViGEmBus Driver**: Required for emulating Xbox controller inputs on Windows. You can download it from [ViGEmBus Releases](https://github.com/ViGEm/ViGEmBus/releases).

### Installation Steps

#### Windows

1. Download the [CMake](https://cmake.org/download/) installer and install it.
2. Install the **ViGEmBus Driver** by downloading the latest release and running the installer.
3. Open a command prompt and run the following commands **(One line at a time)**:

   ```bash
   git clone https://github.com/yourusername/meta-quest-to-xbox-controller.git
   cd meta-quest-to-xbox-controller
   mkdir build
   cd build
   cmake ..
   cmake --build .
   ```

#### Linux

1. Open a terminal and install CMake if it's not already installed:

   ```bash
   sudo apt-get install cmake
   ```

2. Run the following commands **(One line at a time)**:

   ```bash
   git clone https://github.com/yourusername/meta-quest-to-xbox-controller.git
   cd meta-quest-to-xbox-controller
   mkdir build
   cd build
   cmake ..
   cmake --build .
   ```

## How It Works

The converter uses input mapping techniques to read data from Meta Quest controllers and simulate Xbox controller inputs through the **ViGEmBus** driver. The program listens for input events from the Meta Quest controllers and translates them into corresponding Xbox controller signals using a predefined mapping table.

### Code Snippet

Here's a simple example of how the program captures Meta Quest controller inputs and maps them to Xbox controller inputs using **ViGEmBus**:

```cpp
#include <iostream>
#include <OpenXR/OpenXR.h> // OpenXR library
#include <ViGEm/Client.h> // ViGEm library for Xbox inputs

void mapInput(XR_INPUT_ACTION action, PVIGEM_CLIENT vigemClient, PVIGEM_TARGET vigemTarget) {
    switch (action) {
        case XR_INPUT_ACTION_BUTTON_A:
            vigemTarget->ButtonPressed(vigemClient, VIGEM_BUTTON_A); // Map to Xbox A button
            break;
        case XR_INPUT_ACTION_BUTTON_B:
            vigemTarget->ButtonPressed(vigemClient, VIGEM_BUTTON_B); // Map to Xbox B button
            break;
        // Add additional mappings as needed
    }
}
```

## Usage Instructions

1. Connect your Meta Quest controllers to your computer via the Meta Quest App.
2. Run the program by navigating to the build directory and executing the binary:

   ```bash
   ./meta-quest-to-xbox-controller
   ```

3. The program will start mapping the inputs. You can check the console for any errors or messages.

## Troubleshooting

- **Controller Not Recognized**: Ensure that the controllers are properly connected and recognized by your operating system.
- **Input Lag**: Check for any background applications that may interfere with input processing.
- **Compilation Errors**: Ensure that you have installed all prerequisites and are using the correct compiler version.

## Advanced Features

- **Custom Input Profiles**: You can create custom input profiles by editing the configuration file located in the `config` directory.
- **Optional Scripting**: Use scripts to automate certain actions or to create complex input mappings.

## Tools Used

- **OpenXR**: A cross-platform open standard for VR and AR applications, enabling access to VR hardware.  [^1]
- **ViGEmBus**: A virtual gamepad driver that allows applications to emulate gamepad inputs. [^2]

## Contributing

We welcome contributions! If you'd like to contribute, please fork the repository and submit a pull request. For major changes, please open an issue first to discuss what you would like to change.

---

Feel free to reach out if you have any questions or need further assistance!

> [!NOTE]
> - Make sure to include any specific implementation details for how ViGEmBus is used in your code.
> - Update the GitHub URL in the installation steps according to your username. 
> - Ensure that the code snippet accurately represents how you will implement the input mapping using ViGEmBus in your application.

<br>

---

[^1]: [OpenXR website](https://www.khronos.org/openxr/)
[^2]: [ViGEm GitHub repository](https://github.com/ViGEm/ViGEmBus)
