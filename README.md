# STM32

clone libopencm3 from https://github.com/libopencm3/libopencm3.git

copy FreeRTOS from https://github.com/FreeRTOS/FreeRTOS/releases/download/202212.01/FreeRTOSv202212.01.zip

FreeRTOSConfig.h is requred and specific to the application and must be located in the app directory

Copy it from FreeRTOS/Demo/CORTEX_STM32F103_Primer_GCC/FreeRTOSConfig.h to your_project/include


Changes in Free:

#define configUSE_TICK_HOOK 0

#define configSYSTICK_CLOCK_HZ ( configCPU_CLOCK_HZ / 8 )  /* fix for vTaskDelay() */