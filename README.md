# EXPERIMENT-04-INTERRUPT-GENERATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR

###  DATE: 15-09-2025

###  NAME: Vamsi Krishna G
###  REG NO : 212223220120
###  DEPARTMENT: B.Tech-IT
### Aim:
To Interface a IR Sensor to digital port of iot development board  and generate an interrupt and visualize on the serial monitor 

### Components required:
STM32 CUBE IDE,  serial port utility monitor,IR Pair Sensor .


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

 1. click on STM 32 CUBE IDE, the following screen will appear
    
 ![image](https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png)

 2. click on FILE, click on new stm 32 project
  
 ![image](https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png)
 
![image](https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png)

3. select the target to be programmed  as shown below and click on next 

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

14.  After the file download is complete, switch your board to run mode and press the reset button to see the output

15. click on the serial port utility 
![image](https://github.com/user-attachments/assets/72d35bbb-5261-4986-a24f-cfa2c00e26d6)

16. click on the run to observe the values 
 

## STM 32 CUBE PROGRAM :

```
/* USER CODE BEGIN Header */
/**
  ******************************************************************************
  * @file           : main.c
  * @brief          : Main program body
  ******************************************************************************
  * @attention
  *
  * Copyright (c) 2025 STMicroelectronics.
  * All rights reserved.
  *
  * This software is licensed under terms that can be found in the LICENSE file
  * in the root directory of this software component.
  * If no LICENSE file comes with this software, it is provided AS-IS.
  *
  ******************************************************************************
  */
/* USER CODE END Header */
/* Includes ------------------------------------------------------------------*/
#include "main.h"
#include "stdio.h"
#if defined(__GNUC__)
#define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#endif
/* Private includes ----------------------------------------------------------*/
/* USER CODE BEGIN Includes */

/* USER CODE END Includes */

/* Private typedef -----------------------------------------------------------*/
/* USER CODE BEGIN PTD */

/* USER CODE END PTD */

/* Private define ------------------------------------------------------------*/
/* USER CODE BEGIN PD */

/* USER CODE END PD */

/* Private macro -------------------------------------------------------------*/
/* USER CODE BEGIN PM */

/* USER CODE END PM */

/* Private variables ---------------------------------------------------------*/
UART_HandleTypeDef huart2;

/* USER CODE BEGIN PV */

/* USER CODE END PV */

/* Private function prototypes -----------------------------------------------*/
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
static void MX_USART2_UART_Init(void);
/* USER CODE BEGIN PFP */

/* USER CODE END PFP */

/* Private user code ---------------------------------------------------------*/
/* USER CODE BEGIN 0 */

/* USER CODE END 0 */

/**
  * @brief  The application entry point.
  * @retval int
  */
int main(void)
{

  /* USER CODE BEGIN 1 */

  /* USER CODE END 1 */

  /* MCU Configuration--------------------------------------------------------*/

  /* Reset of all peripherals, Initializes the Flash interface and the Systick. */
  HAL_Init();

  /* USER CODE BEGIN Init */

  /* USER CODE END Init */

  /* Configure the system clock */
  SystemClock_Config();

  /* USER CODE BEGIN SysInit */

  /* USER CODE END SysInit */

  /* Initialize all configured peripherals */
  MX_GPIO_Init();
  MX_USART2_UART_Init();
  /* USER CODE BEGIN 2 */

  /* USER CODE END 2 */

  /* Infinite loop */
  /* USER CODE BEGIN WHILE */
  while (1)
  {
    /* USER CODE END WHILE */

    /* USER CODE BEGIN 3 */
  }
  /* USER CODE END 3 */
}
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
	if(HAL_GPIO_ReadPin(GPIOB,GPIO_PIN_3)==1)
	{
		printf("INTERRUPT GENERATED\n");
	}
}
PUTCHAR_PROTOTYPE
{
	HAL_UART_Transmit(&huart2,(uint8_t*)&ch,1,0xFFFF);
	return ch;
}
/**
  * @brief System Clock Configuration
  * @retval None
  */
void SystemClock_Config(void)
{
  RCC_OscInitTypeDef RCC_OscInitStruct = {0};
  RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};

  /** Configure the main internal regulator output voltage
  */
  __HAL_PWR_VOLTAGESCALING_CONFIG(PWR_REGULATOR_VOLTAGE_SCALE2);

  /** Initializes the CPU, AHB and APB buses clocks
  */
  RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_MSI;
  RCC_OscInitStruct.MSIState = RCC_MSI_ON;
  RCC_OscInitStruct.MSICalibrationValue = RCC_MSICALIBRATION_DEFAULT;
  RCC_OscInitStruct.MSIClockRange = RCC_MSIRANGE_6;
  RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;
  if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK)
  {
    Error_Handler();
  }

  /** Configure the SYSCLKSource, HCLK, PCLK1 and PCLK2 clocks dividers
  */
  RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK3|RCC_CLOCKTYPE_HCLK
                              |RCC_CLOCKTYPE_SYSCLK|RCC_CLOCKTYPE_PCLK1
                              |RCC_CLOCKTYPE_PCLK2;
  RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_MSI;
  RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
  RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;
  RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV1;
  RCC_ClkInitStruct.AHBCLK3Divider = RCC_SYSCLK_DIV1;

  if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
  {
    Error_Handler();
  }
}

/**
  * @brief USART2 Initialization Function
  * @param None
  * @retval None
  */
static void MX_USART2_UART_Init(void)
{

  /* USER CODE BEGIN USART2_Init 0 */

  /* USER CODE END USART2_Init 0 */

  /* USER CODE BEGIN USART2_Init 1 */

  /* USER CODE END USART2_Init 1 */
  huart2.Instance = USART2;
  huart2.Init.BaudRate = 9600;
  huart2.Init.WordLength = UART_WORDLENGTH_8B;
  huart2.Init.StopBits = UART_STOPBITS_1;
  huart2.Init.Parity = UART_PARITY_NONE;
  huart2.Init.Mode = UART_MODE_TX_RX;
  huart2.Init.HwFlowCtl = UART_HWCONTROL_NONE;
  huart2.Init.OverSampling = UART_OVERSAMPLING_16;
  huart2.Init.OneBitSampling = UART_ONE_BIT_SAMPLE_DISABLE;
  huart2.Init.ClockPrescaler = UART_PRESCALER_DIV1;
  huart2.AdvancedInit.AdvFeatureInit = UART_ADVFEATURE_NO_INIT;
  if (HAL_UART_Init(&huart2) != HAL_OK)
  {
    Error_Handler();
  }
  if (HAL_UARTEx_SetTxFifoThreshold(&huart2, UART_TXFIFO_THRESHOLD_1_8) != HAL_OK)
  {
    Error_Handler();
  }
  if (HAL_UARTEx_SetRxFifoThreshold(&huart2, UART_RXFIFO_THRESHOLD_1_8) != HAL_OK)
  {
    Error_Handler();
  }
  if (HAL_UARTEx_DisableFifoMode(&huart2) != HAL_OK)
  {
    Error_Handler();
  }
  /* USER CODE BEGIN USART2_Init 2 */

  /* USER CODE END USART2_Init 2 */

}

/**
  * @brief GPIO Initialization Function
  * @param None
  * @retval None
  */
static void MX_GPIO_Init(void)
{
  GPIO_InitTypeDef GPIO_InitStruct = {0};
/* USER CODE BEGIN MX_GPIO_Init_1 */
/* USER CODE END MX_GPIO_Init_1 */

  /* GPIO Ports Clock Enable */
  __HAL_RCC_GPIOB_CLK_ENABLE();
  __HAL_RCC_GPIOA_CLK_ENABLE();

  /*Configure GPIO pin : PB3 */
  GPIO_InitStruct.Pin = GPIO_PIN_3;
  GPIO_InitStruct.Mode = GPIO_MODE_IT_RISING;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  HAL_GPIO_Init(GPIOB, &GPIO_InitStruct);

  /* EXTI interrupt init*/
  HAL_NVIC_SetPriority(EXTI3_IRQn, 0, 0);
  HAL_NVIC_EnableIRQ(EXTI3_IRQn);

/* USER CODE BEGIN MX_GPIO_Init_2 */
/* USER CODE END MX_GPIO_Init_2 */
}

/* USER CODE BEGIN 4 */

/* USER CODE END 4 */

/**
  * @brief  This function is executed in case of error occurrence.
  * @retval None
  */
void Error_Handler(void)
{
  /* USER CODE BEGIN Error_Handler_Debug */
  /* User can add his own implementation to report the HAL error return state */
  __disable_irq();
  while (1)
  {
  }
  /* USER CODE END Error_Handler_Debug */
}

#ifdef  USE_FULL_ASSERT
/**
  * @brief  Reports the name of the source file and the source line number
  *         where the assert_param error has occurred.
  * @param  file: pointer to the source file name
  * @param  line: assert_param error line source number
  * @retval None
  */
void assert_failed(uint8_t *file, uint32_t line)
{
  /* USER CODE BEGIN 6 */
  /* User can add his own implementation to report the file name and line number,
     ex: printf("Wrong parameters value: file %s on line %d\r\n", file, line) */
  /* USER CODE END 6 */
}
#endif /* USE_FULL_ASSERT */

```

## Output screen shots of serial port utility   :
 <img width="1919" height="1017" alt="Screenshot 2025-09-15 114523" src="https://github.com/user-attachments/assets/76b7a3f8-1cde-4e21-96e3-87efc6f523d0" />

 
 ## Circuit board :
 
 ![WhatsApp Image 2025-09-15 at 11 50 57_a2edf002](https://github.com/user-attachments/assets/81c0ebd5-5352-4af5-bc53-a53571c53e91)

 
## Result :
Interfacing a  IR SENSOR and interrupt is generated using external interrupt mode , visualized on serial port 
