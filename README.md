# Component Lab: Active and Passive Buzzers
In previous labs, you learned to read temperature and humidity using a DHT11 sensor and display that information on a 16×2 LCD screen.

In this lab, you will add to your existing circuit by adding a buzzer. You will experiment with two types of buzzers, active and passive, to see how they produce sound with the Arduino controlling them.

## 1. Understand Buzzers
Locate the active and passive buzzers in your kits. Use the images below to help locate them.
|       |     |
| :---:   |  :---:  |
|![Active buzzer](active.png) | ![Passive buzzer](passive.png) |
| **Active buzzer** | **Passive buzzer** |

The following table breaks down the major differences.

| Buzzer Type  | Arduino Function   | Pitch(es) Available | Typical Usage |
| --- | ---  | --- | --- |
| Active | `digitalWrite()` | Simple tone | Basic alarms |
| Passive | `tone()`        | 100Hz - 65,535Hz | Musical notes, custom alarms| 

### Predict
1. What will happen if you connect an active buzzer to a digital output set to HIGH?
    > your answer

2. What do you predict will happen if you use the same program with a passive buzzer?
    > your answer


## 2. Build the circuit
Keep your DHT11 and LCD connected like they were in the previous labs.

### Wiring
| Component | Arduino	| Connection |	Purpose |
| ---  | --- | --- | --- |
| DHT11 DATA |	Digital Pin 2 |	Sensor input |
| LCD RS	| Digital Pin 7	| Register select |
| LCD E	| Digital Pin 8 | Enable| 
| LCD D4–D7	 |Digital Pins 9–12	| LCD data| 

Connect the **active buzzer** to digital pin 3. You will swap this out later for the passive buzzer.

| Component | Arduino	| Connection |	Purpose |
| ---  | --- | --- | --- |
| Buzzer +	| Digital Pin 3	| Audio output
| Buzzer −	| GND	| Ground |


## 3. Program the active buzzer
The program code in `buzzer.ino` contains the work you did in the previous lab. 

### Task 1: Define and initialize the buzzer pin
Fine the `TODO` comments for each of the steps below. Once you've implemented the code, remove the word `TODO:` but keep the comment.

Add a constant for the buzzer.

```c++
const int buzzerPin = 3;
```

In `setup()`, set the buzzer pin to output.
```c++
pinMode(buzzerPin, OUTPUT);
```

### Task 2: Play a sound
Use `digitalWrite()` to get the buzzer to play a sound. Play a short sound after every LCD update.

```c++
digitalWrite(buzzerPin, HIGH);
delay(200);
digitalWrite(buzzerPin, LOW);
```
### Task 3: Experiment with patterns
Change the program to create each of the following patterns after the LCD updates.
- Single short beep
- Double short beep
- Long beep

### Reflect
1. Which part of the code controls how long the buzzer sounds?
    > your answer

2. What code would you use to create three short beeps?
    ```c++

    ```

3. Can you change the pitch of the active buzzer using `digitalWrite()`?
    > your answer

## 4. Try the passive buzzer
Disconnect the power and replace the active buzzer with the passive buzzer. Keep the same pin connections.

### Task 1: Create a tone
The passive buzzer requires a rapidly changing electrical signal to produce a tone. Use the Arduino `tone()` function.

```c++
tone(buzzerPin, 425);
delay(200);
noTone(buzzerPin);
```

The `tone()` function takes two arguments: the pin the buzzer is on, and the frequency. The frequency is measured in Hertz (Hz), which is cycles per second. The `tone()` function in theory can take a frequency up to 65,535Hz, but in reality the board and buzzer quality start failing around 10,000 - 15,000 Hz.


### Task 2: Experiment with frequency
Change the frequency argument and observe what happens. Record your observations.

| Frequency | Observation |
|  ---      |  ---        |
| 250 Hz    |             |
| 500 Hz    |             |
| 1000 Hz    |             |
| 2000 Hz    |             |
| 5000 Hz    |             |

### Reflect
1. How are frequency and pitch related? As frequency increases, pitch _____.
    > your answer

2. Why would a designer choose a passive buzzer for an alarm system?
    > your answer


# 5. Set an alert
Modify your system so that the buzzer **only sounds when the temperature or humidity goes above/below a specific threshold.**

Write your alert as a function

```c++
void tooHotAlert() {

}
```

# 6. Wrap up
1. What is the major difference between active and passive buzzers?
    > your answer

2. What is an advantage of a passive buzzer when creating an alert system?
    > your answer

3. Why is it useful to separate code that reads sensors from the code that controls output devices?
    > your answers

