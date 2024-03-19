# STM32F103

Install ARM GNU Toolchain from https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads

Install gdb server: brew install stlink

Pull and build libopencm3: git submodule update --init && make -C libopencm3

Copy FreeRTOS to root:
curl -L https://github.com/FreeRTOS/FreeRTOS/releases/download/202212.01/FreeRTOSv202212.01.zip -o FreeRTOSv202212.01.zip && unzip FreeRTOSv202212.01.zip && rm FreeRTOSv202212.01.zip

Install Cortex-Debug extension for vscode