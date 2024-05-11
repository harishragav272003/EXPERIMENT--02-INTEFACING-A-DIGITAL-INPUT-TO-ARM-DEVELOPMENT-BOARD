# EXPERIMENT 02 INTERFACING A DIGITAL INPUT TO ARM DEVELOPMENT BOARD

### NAME : HARISH RAGAV S
### REG NO:212222110013

## Aim: 
To Interface a Digital Input  (userpush button  ) to ARM   development board and write a  program to obtain  the data and flash the led  

## Components required: 
STM32 CUBE IDE, ARM IOT development board,  STM programmer tool.

## Theory 
The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

 
  
## Procedure:
 1. click on STM 32 CUBE IDE, the following screen will appear 

 2.click on FILE, click on new stm 32 project 

3. select the target to be programmed  as shown below and click on next 

4.select the program name 

5. corresponding ioc file will be generated automatically 

6.select the appropriate pins as gipo, in or out, USART or required options and configure 

7.click on cntrl+S , automaticall C program will be generated 

8. edit the program and as per required 

9. use project and build all 

10. once the project is bulild

11. click on debug option
 
13. connect the  ARM board to power supply and usb 



## STM 32 CUBE PROGRAM :
```
#include "main.h"


void SystemClock_Config(void);
static void MX_GPIO_Init(void);
void ledblink();

int main(void)
{

  HAL_Init();

  SystemClock_Config();

  MX_GPIO_Init();

  while (1)
  {
   ledblink();
  }
}

void ledblink()
{
	HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,GPIO_PIN_SET);
	HAL_Delay(2000);
	HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,GPIO_PIN_RESET);
	HAL_Delay(1000);
}

void SystemClock_Config(void)
{
  RCC_OscInitTypeDef RCC_OscInitStruct = {0};
  RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};


  HAL_PWREx_ControlVoltageScaling(PWR_REGULATOR_VOLTAGE_SCALE1);

  RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_HSI;
  RCC_OscInitStruct.HSIState = RCC_HSI_ON;
  RCC_OscInitStruct.HSIDiv = RCC_HSI_DIV1;
  RCC_OscInitStruct.HSICalibrationValue = RCC_HSICALIBRATION_DEFAULT;
  RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;
  if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK)
  {
    Error_Handler();
  }

  RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK|RCC_CLOCKTYPE_SYSCLK
                              |RCC_CLOCKTYPE_PCLK1;
  RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_HSI;
  RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
  RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;

  if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
  {
    Error_Handler();
  }
}

static void MX_GPIO_Init(void)
{
  GPIO_InitTypeDef GPIO_InitStruct = {0};


  __HAL_RCC_GPIOA_CLK_ENABLE();


  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);


  GPIO_InitStruct.Pin = GPIO_PIN_5;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);

}

void Error_Handler(void)
{
  __disable_irq();
  while (1)
  {
  }
}

#ifdef  USE_FULL_ASSERT

void assert_failed(uint8_t *file, uint32_t line)
{

}
#endif
```


## Output  :
## output 1
<img src="https://github.com/Bala1511/EXPERIMENT--02-INTEFACING-A-DIGITAL-INPUT-TO-ARM-DEVELOPMENT-BOARD/assets/118680410/706d3431-dc70-4c02-b31f-7c137825237e" width="450" height="450">



## output 2
 <img src="https://github.com/Bala1511/EXPERIMENT--02-INTEFACING-A-DIGITAL-INPUT-TO-ARM-DEVELOPMENT-BOARD/assets/118680410/4430414b-a259-4a8c-ac99-6cb38fdb9239" width="450" height="450">
 
## Result :
Interfacing a digital Input (Pushbutton ) with ARM microcontroller based IOT development is executed and the results are verified.
