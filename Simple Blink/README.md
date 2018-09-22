# Simple Blink

The following code blinks an onboard LED on an MSP430G2553 and MSP430FR2311 at the reigster level.

## Step 1: Configure the Watchdog Timer

The watchdog timer is a preventative measure to ensure that the microcontroller is not left in a state where it cannot function, such as an infinite loop. It works by resetting the processor if the processor does not acknowledge it. In order to ignore the watchdog timer, the watch dog control register is set to WDTPW ored with WDTHOLD. This results in the watchdog timer being disabled. 

## Step 2: Configure Pin #.# to the Output Direction

In order to drive an LED, the register must be set to output. This is done by setting the direction register value to 1 by orring it with a 1.

#### G2553: 

On the G2553, P1.0 is selected as the output pin as it is connected to the onboard LED.

#### FR2311: 

On the FR2311, P1.0 is selected as the output pin as it is connected to the onboard LED.

## Step 3: Infinite Loop

In order to make the continue the functionality, the remainder of the code will be nested in a infinite loop. This is done by utilizing a while loop with the condition of 1 or true. Every time the while loop reitterates, it checks the condition, and sees a true, thus continuing the loop. This is a reason why the watchdog timer is disabled.

## Step 4: Toggle LED State

In order to toggle the state of the LED, the pinout register value is xored with a 1 in order to changs its state within every itteration of the while loop. 

## Step 5: Delay

In order to make the LED blink, a delay must be utilized so that the toggling of the LED can be visible. For this a delay cycle of 100000, resulting in a delay of 100 milliseconds.
