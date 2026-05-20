# ESP32 Keypad Calculator

A fully functional calculator built using an ESP32, a 4x4 matrix keypad, and a 16x2 I²C LCD display.

This project allows users to perform basic arithmetic operations directly from a physical keypad while displaying all input and results on the LCD screen.

---

# Features

- Addition
- Subtraction
- Multiplication
- Division
- Divide-by-zero protection
- Real-time LCD display output
- Automatic reset after calculation
- Multi-digit number support
- Custom keypad matrix mapping
- Clean embedded-system structure

---

# Hardware Used

| Component | Quantity |
|---|---|
| ESP32 Dev Board | 1 |
| 4x4 Matrix Keypad | 1 |
| 16x2 I²C LCD Display | 1 |
| Jumper Wires | Multiple |
| Breadboard (optional) | 1 |

---

# Pin Layout

## LCD Connections (I²C)

| LCD Pin | ESP32 Pin |
|---|---|
| GND | GND |
| VCC | 5V |
| SDA | GPIO21 |
| SCL | GPIO22 |

---

## Keypad Connections

### Row Pins

| Keypad Row | ESP32 Pin |
|---|---|
| R1 | GPIO23 |
| R2 | GPIO25 |
| R3 | GPIO26 |
| R4 | GPIO27 |

### Column Pins

| Keypad Column | ESP32 Pin |
|---|---|
| C1 | GPIO16 |
| C2 | GPIO17 |
| C3 | GPIO18 |
| C4 | GPIO19 |

---

# Keypad Layout

Due to the physical wiring orientation of the keypad, the matrix was intentionally inverted in software.

Final keypad mapping:

|   |   |   |   |
|---|---|---|---|
| / | = | 0 | $ |
| * | 9 | 8 | 7 |
| - | 6 | 5 | 4 |
| + | 3 | 2 | 1 |

---

# Libraries Required

Install the following libraries inside Arduino IDE:

## Keypad Library
- Keypad by Mark Stanley and Alexander Brevig

## LCD Library
- LiquidCrystal_I2C

## Wire Library
- Included by default with Arduino IDE

---

# How It Works

The calculator operates in several stages:

1. User enters digits using the keypad
2. Digits are combined into full numbers
3. User selects an operator
4. First number gets stored
5. User enters second number
6. Pressing `=` calculates the result
7. LCD displays the final answer

The calculator supports multi-digit arithmetic using this logic:

```cpp
y = (y * 10) + inputDigit;
```

This shifts the current number left by one decimal place before adding the new digit.

Example:

```text
Current number: 12
Pressed digit: 3

12 * 10 = 120
120 + 3 = 123
```

---

# Controls

| Key | Function |
|---|---|
| 0-9 | Number Input |
| + | Addition |
| - | Subtraction |
| * | Multiplication |
| / | Division |
| = | Calculate Result |
| $ | Clear / Reset |

---

# User Manual

## Performing a Calculation

### Example:
```text
25 + 17
```

### Steps:
1. Press `2`
2. Press `5`
3. Press `+`
4. Press `1`
5. Press `7`
6. Press `=`

LCD output:
```text
Answer:
42
```

---

# Error Handling

## Division by Zero

If the user attempts:

```text
10 / 0
```

The LCD displays:

```text
Error
```

instead of crashing.

---

# Software Structure

## Main Components

| Function | Purpose |
|---|---|
| `datastore1()` | Builds multi-digit numbers |
| `resetCalculator()` | Clears LCD and resets variables |
| `loop()` | Main calculator logic |
| `keypad.getKey()` | Reads keypad input |

---

# Future Improvements

Possible upgrades:

- Decimal number support
- Negative number support
- Scientific calculator functions
- EEPROM memory storage
- Calculation history
- OLED display upgrade
- WiFi-based calculator logging
- Web interface using ESP32 WiFi

---

# Challenges Faced

One major challenge involved the keypad matrix orientation.

The keypad wiring order was physically reversed compared to the software layout, causing incorrect key outputs.

This was solved by:
- reversing the keypad matrix in software
- adjusting row and column mappings

This project helped develop:
- embedded systems debugging
- GPIO mapping
- matrix scanning understanding
- LCD interfacing
- state management
- hardware/software integration

---

# Project Showcase

Want to see the calculator in action?

Check out the build photos and demo videos on Instagram:

https://www.instagram.com/lord_equnox?igsh=YTVwenNkc2Jwb2oy

username of the account:

lord_equnox

# Built With

- ESP32
- Arduino IDE
- C++
- LiquidCrystal_I2C
- Keypad Library
- way too many semicolon investigations

---

# Author

###Sanu
