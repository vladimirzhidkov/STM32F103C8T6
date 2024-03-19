# STM32F103 with FreeRTOS

FreeRTOS/Demo/CORTEX_STM32F103_Primer_GCC/FreeRTOSConfig.h

is requred and specific to the application and must be located in the app directory


Changes in FreeRTOSConfig:

#define configUSE_TICK_HOOK 0

#define configSYSTICK_CLOCK_HZ ( configCPU_CLOCK_HZ / 8 )  /* fix for vTaskDelay() */