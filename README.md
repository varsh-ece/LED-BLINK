# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
   ![WhatsApp Image 2025-11-06 at 11 16 54_e8a2701f](https://github.com/user-attachments/assets/8de2ad7c-e69a-4e70-a079-d35ad18bd27c)


2. Click **File → New STM32 Project**.
   ![WhatsApp Image 2025-11-06 at 11 17 27_cbcb8a7a](https://github.com/user-attachments/assets/f0f50190-fc83-4f68-9d55-b74ac475248a)
   <img width="1705" height="906" alt="image" src="https://github.com/user-attachments/assets/10c40fb2-2fff-4e08-9704-e579aa1396ff" />



3. Select the **target microcontroller** or board and click **Next**.
  ![WhatsApp Image 2025-11-06 at 11 19 05_3dbc9ffe](https://github.com/user-attachments/assets/a44e2c12-075d-40aa-9b4c-8ea7cca92438)



4. Name the project.
   
  ![WhatsApp Image 2025-11-06 at 11 19 47_386a82a0](https://github.com/user-attachments/assets/b1b1c39f-a058-4cf2-b2a1-30530c92245c)

7. The corresponding `.ioc` file will be generated automatically.
 <img width="1479" height="782" alt="image" src="https://github.com/user-attachments/assets/c436bf2e-c7b4-44a9-8333-8fb4a3e5fbea" />



5. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   ![WhatsApp Image 2025-11-06 at 11 25 15_fa46caa2](https://github.com/user-attachments/assets/79dc632e-9189-4d45-9ffb-7296be58d91e)
   <img width="1602" height="852" alt="image" src="https://github.com/user-attachments/assets/d6ce1379-d793-40f2-97b4-dd44dd773941" />



6. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
    
   ![WhatsApp Image 2025-11-06 at 11 29 39_d41a1c8d](https://github.com/user-attachments/assets/1cbe40d7-3f01-4914-a4d4-aeeb82309373)

 
7. Edit the generated main program as required.
  ![WhatsApp Image 2025-11-06 at 11 30 53_1d0a6bc3](https://github.com/user-attachments/assets/5a19d464-3d54-447d-97c5-0d778702fa55)


8. Click **Project → Build All**.
   ![WhatsApp Image 2025-11-06 at 11 37 10_13cafa8d](https://github.com/user-attachments/assets/e70e7b63-0359-49ea-8503-5fe63dd4b253)


9. Link the **HEX file** using the post-build process.
<img width="1536" height="617" alt="image" src="https://github.com/user-attachments/assets/388bea66-37d6-41ce-80ac-d9c706052458" />


10. Click **Debug** and connect the **STM Nucleo Board**.
   <img width="1483" height="822" alt="image" src="https://github.com/user-attachments/assets/eb9179a5-09bc-4ffb-971b-79d44c052c5b" />

11. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

<img width="673" height="506" alt="image" src="https://github.com/user-attachments/assets/ba214fc6-c9fe-4fe9-9508-162c2bbbbd7f" />


CASE 2: LED OFF

<img width="827" height="741" alt="image" src="https://github.com/user-attachments/assets/e9db98a0-85e9-4949-9e1c-6ccefdb6b365" />


---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
