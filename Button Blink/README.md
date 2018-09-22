# Button Blink

The following code blinks an onboard LED on an MSP430G2553 and MSP430FR2311 at the reigster level.

## Step 1: Configure the Watchdog Timer

The watchdog timer is a preventative measure to ensure that the microcontroller is not left in a state where it cannot function, such as an infinite loop. It works by resetting the processor if the processor does not acknowledge it. In order to ignore the watchdog timer, the watch dog control register is set to WDTPW ored with WDTHOLD. This results in the watchdog timer being disabled. 

## Step 2: Configure Pin #.# to the Output Direction

In order to drive an LED, the registers must be set to output. This is done by setting the direction register values to 1 by orring it with a 1.

#### G2553: 

On the G2553, P1.0 is selected as the output pin as it is connected to the onboard LED.

#### FR2311: 

On the FR2311, P1.0 is selected as the output pin as it is connected to the onboard LED.

## Step 3: Configure Pin #.# to the input direction.

In order to drive an check the state of a pin, the registers must be set to input. This is done by setting the direction register values to 0 by anding it with a 0.

#### G2553: 

On the G2553, P1.3 is selected as the input pin as it is connected to the onboard button.

#### FR2311: 

On the FR2311, P1.1 is selected as the input pin as it is connected to the onboard button.

## Step 4: Enabling Pull Down Resistor

In order to ensure that the button input is not addected by any noise, a pull down resistor is utilized. The MSP430 contains an onboard pulldown and pullup resistor. In order to configure this, the input pin resistor enable is set to a 1 by orring it with a 1 to configure it as a pullup resistor.

## Step 5: Infinite Loop

In order to make the continue the functionality, the remainder of the code will be nested in a infinite loop. This is done by utilizing a while loop with the condition of 1 or true. Every time the while loop reitterates, it checks the condition, and sees a true, thus continuing the loop. This is a reason why the watchdog timer is disabled.

## Step 6: Button Polling

An if statement is utilized to poll the state of the button to see when it is pressed. When the button is pressed, the processor reads a 1 for the register value. The register value is compared to a one, once it is true, the LED pinout is set to a 1. Otherwise, the LED pinout is set to a 0. Although this is not the most efficient, it is the simplest. An interupt can be utilized to minimize usage of the proccessor and thus consume less energy.
