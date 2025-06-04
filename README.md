# EXPERIMENT-04-INTERRUPT-GENERATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR

### DATE: 03/05/2025

### NAME: Roopak C S

### ROLL NO : 212223220088

### DEPARTMENT: B.Tech IT

### Aim:

To Interface a IR Sensor to digital port of iot development board and generate an interrupt and visualize on the serial monitor

### Components required:

STM32 CUBE IDE, serial port utility monitor,IR Pair Sensor .

## Theory :

An infrared (IR) sensor a proximity sensor, or a ‘nearness’ sensor senses whether there is an object near it or not. The IR stands for Infrared sensor. Infrared is the light out of our visible spectrum.

Working of an IR Sensor
The white LED here is an IR LED which works as the transmitter and the component next to the IR LED is a photodiode that works as the receiver in the IR sensor.

The IR transmitter continuously emits the IR light and the IR receiver keeps on checking for the reflected light. If the light gets reflected back by hitting any object in front it, the IR receiver receives this light. This way the object is detected in the case of the IR sensor.

The blue knob here is a potentiometer. You can control the range i.e. from how far you want to detect the object by changing the value of the potentiometer.

An IR sensor has two small LED indicators – one for power, which is ON the entire time the sensor is ON; the other is the Signal LED which detects the object. The signal LED has two states or situations:

ON (Active) when it detects an object
OFF (Inactive) when it doesn’t detect any object

![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/9bf61298-1deb-48d7-b88f-bd08e3cc6a83)

Now that we have a little idea about its works, let’s take a look at how to interface it with evive and see it in action.

Connect VCC pin to the +5V pin on evive.
Connect GND pin to evive’s GND pin.
Connect OUT to any gpio and configure that pin as EXTI mode

### Interrupts

Interrupts are asynchronous (i.e. can happen anytime) events that disrupt the normal flow of your program. This allows the microcontroller to focus on a key task and attend to these events (e.g. pressing a button) as they come without needing to wait for them.

With interrupt, we do not need to continuously check the state of the digital input pin. When an interrupt occurs (a change is detected), the processor stops the execution of the main program and a function is called upon known as ISR or the Interrupt Service Routine. The processor then temporarily works on a different task (ISR) and then gets back to the main program after the handling routine has ended.

![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/cb4ac7aa-30ed-4b97-b3b4-1986db9f1558)
The STM32 ARM microcontroller interrupts are generated in the following manner:

The system runs the ISR and then goes back to the main program. The NVIC and EXTI are configured. The Interrupt Service Routine (ISR) also known as the interrupt service routine handler is defined to enable the external interrupts.

Interrupt Lines (EXTI0-EXTI15)
The STM32 ARM microcontroller features 23 event sources which are divided into two sections. The first section corresponds t external pins on each port which are P0-P15. The second section corresponds to RTC, ethernet, USB interrupts. Therefore, in the first section, we have 16 lines corresponding to line0 till line15. All of these map to a pin number.

![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/1110746f-6be2-4d12-9a34-66004e4b307b)

The diagram below shows how the GPIO pins are connected to the 16 interrupt lines:

## Procedure:

1.  click on STM 32 CUBE IDE, the following screen will appear

![image](https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png)

2.  click on FILE, click on new stm 32 project

![image](https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png)

![image](https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png)

3. select the target to be programmed as shown below and click on next

![Screenshot 2025-03-11 134231](https://github.com/user-attachments/assets/09e61f3d-224f-4ca8-96d4-7336869df5c7)

4.select the program name

![image](https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png)

5. corresponding ioc file will be generated automatically

   ![Screenshot 2025-03-11 134528](https://github.com/user-attachments/assets/df427edd-e24a-4612-a858-aeae859b379f)

6.select the appropriate pins as gipo, in or out, USART or required options and configure

![Screenshot 2025-03-11 134617](https://github.com/user-attachments/assets/125ee548-30b1-4c88-932f-adf07984522f)
![Screenshot 2025-03-11 134642](https://github.com/user-attachments/assets/0adfbb58-4cad-408a-9300-f4808b53cac4)

7.click on cntrl+S , automaticall C program will be generated

![Screenshot 2025-03-11 134709](https://github.com/user-attachments/assets/70b83b79-1569-4f14-99d5-e2adbb4e692d)

8. edit the program and as per required

![image](https://user-images.githubusercontent.com/36288975/226189461-a573e62f-a109-4631-a250-a20925758fe0.png)

9. use project and build all

![image](https://user-images.githubusercontent.com/36288975/226189554-3f7101ac-3f41-48fc-abc7-480bd6218dec.png)

10. once the project is build

![image](https://user-images.githubusercontent.com/36288975/226189577-c61cc1eb-3990-4968-8aa6-aefffc766b70.png)

11. connect the iot board to power supply and usb

12. After connecting open the STM cube programmer

![Screenshot 2025-03-11 135208](https://github.com/user-attachments/assets/bb67ab6b-81a5-450c-b170-4276a9b87ef2)

13. Connect the STM board through the COM port, then upload the corresponding project ELF file/Hex file or Bin file in Erasing & Programming Window,while ensuring the board is in flash mode, and click on 'Start Program'.

    ![image](https://github.com/user-attachments/assets/9383531d-8204-4697-9321-55afb6abee2e)

14. After the file download is complete, switch your board to run mode and press the reset button to see the output

15. click on the serial port utility
    ![image](https://github.com/user-attachments/assets/72d35bbb-5261-4986-a24f-cfa2c00e26d6)

16. click on the run to observe the values

## STM 32 CUBE PROGRAM :

```c
#include "main.h"
#include "stdio.h"
#if defined (__ICCARM) || defined (__ARMCC_VERSION)
#define PUTCHAR_PROTOTYPE int fputc(int ch, FILE *f)
#elif defined(__GNUC__)
#define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#endif

UART_HandleTypeDef huart2;

void SystemClock_Config(void);
static void MX_GPIO_Init(void);
static void MX_USART2_UART_Init(void);

int main(void)
{
    HAL_Init();

    SystemClock_Config();

    MX_GPIO_Init();
    MX_USART2_UART_Init();
    while (1)
  {

  }
  }
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
	if(HAL_GPIO_ReadPin(GPIOB,GPIO_PIN_4)==1)
	{
		printf("INTERRUPT GENERATED\n");
	}
}
PUTCHAR_PROTOTYPE{
	HAL_UART_Transmit(&huart2, (uint8_t*)&ch,1,0xFFFF);
	return ch;
}
```

## Output screen shots of serial port utility :

![Screenshot 2025-04-10 111850](https://github.com/user-attachments/assets/13f863ac-ac66-44d0-bf0e-d67e7c42ddd8)

## Circuit board :

![EXP04IOT circuit](https://github.com/user-attachments/assets/05be8f2d-3aea-4f58-b86b-8f3f557ff3f0)

## Result :

Interfacing a IR SENSOR and interrupt is generated using external interrupt mode , visualized on serial port
