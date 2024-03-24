# h1 Create Task
```c
#include "FreeRTOS.h"
#include "task.h"

// Task prototype
void vTaskFunction(void *pvParameters);

int main() {
    // Create a task with vTaskFunction as the task function
    TaskHandle_t xTaskHandle; // Variable to hold the task handle

    BaseType_t xTaskCreated = xTaskCreate(
        vTaskFunction,               // Task function prototype
        "TaskName",                 // Task name
        configMINIMAL_STACK_SIZE,   // Stack size
        NULL,                       // Task parameters
        tskIDLE_PRIORITY,           // Task priority
        &xTaskHandle                // Reference to task handle variable
    );

    if (xTaskCreated == pdPASS) {
        // Task created successfully
    } else {
        // Error: Couldn't create task
    }

    // Start FreeRTOS scheduler
    vTaskStartScheduler();

    // Code never reaches here
    return 0;
}
