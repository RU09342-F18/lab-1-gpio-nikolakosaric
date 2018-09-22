# Multiple Blink

## Code

The following code blinks an onboard LED on an MSP430G2553 at the reigster level. This is a d

### Step 1: Configure the Watchdog Timer

The watchdog timer is a preventative measure to ensure that the microcontroller is not left in a state where it cannot function, such as an infinite loop. It works by resetting the processor if the processor does not acknowledge it. In order to ignore the watchdog timer, the watch dog control register is set to WDTPW ored with WDTHOLD. This results in the watchdog timer being disabled. 

### Step 2: Configure Pin #.# to the Output Direction

In order to drive an LED, the registers must be set to output. This is done by setting the direction register values to 1 by orring it with a 1.

##### G2553: 

On the G2553, P1.0 and P1.6 are selected as the output pin as they are connected to the onboard LEDs.

### Step 3: Infinite Loop

In order to make the continue the functionality, the remainder of the code will be nested in a infinite loop. This is done by utilizing a while loop with the condition of 1 or true. Every time the while loop reitterates, it checks the condition, and sees a true, thus continuing the loop. This is a reason why the watchdog timer is disabled.

### Step 4: Toggle LED1 State

In order to toggle the state of LED1, the pinout register value is xored with a 1 in order to changs its state within every itteration of the while loop. 

### Step 6: Toggle LED2 State

In order to toggle LED2 at a different frequency from which LED1 is toggled, a for loop is utilized, itterating 3 times before completing.  In order to make the LED blink, a delay must be utilized so that the toggling of the LED can be visible. For this a delay cycle of 100000, resulting in a delay of 100 milliseconds. Then the pinout of LED2 is toggled by xorring the register value with a 1. The toggle is done 3 times withing the loops, and then returns to the begginging of the while loop. This results in LED2 blinking 3 times for every 1 time LED 1 blinks, changing the frequency at which the LED1 and LED2 blink.

## Hardware

In order to utilize the G2553 out of the launcpad, the IC is placed on a breadboard. 

- DVCC (pin 1) is connect to 3.3V. 
- P1.0 (pin 2) is connected to a 110 ohm resistor and then to a green led.
- P1.6 (pin 14) is connected to a 160 ohm resistor and then to a red led.
- rst (pin 16) can be connected to DVCC.

With the following setup, the G2553 can be utilized on a breadboard rather than the launchpad.

Photo and videos of the offboard blink can be seen in the repo.
