# 2N2222-vs.-TIP122-Darlington-Transistors-
A hardware test comparing the efficiency of a 2N2222 BJT and a TIP122 Darlington pair driving a 5V DC, 0.9W Sunon MagLev Fan
### Transistor Performance Comparison
*(Driving 0.9W, 5V Fan. 330 Ohm resistor used for Base of Transistors)*

| Measurement / Calculation | 2N2222 (Standard BJT) | TIP122 (Darlington Pair) | What this means for your circuit |
| :--- | :--- | :--- | :--- |
| **— MEASURED VOLTAGES —** | | | |
| **Base to Emitter (V_BE)** | 0.82 V | 1.41 V | TIP122 takes double the voltage just to turn on because it has two internal transistors. |
| **Base to Collector (V_BC)**| 0.75 V | 0.72 V | Both are forward-biased, confirming both transistors hit full saturation. |
| **Collector to Emitter (V_CE)**| 0.07 V | 0.69 V | **The Darlington Tax:** TIP122 steals 10x more voltage from the fan compared to the 2N2222. |
| **Voltage at Resistor (V_RB)**| 3.54 V | 3.06 V | Voltage leftover for the 330 ohm base resistor after the transistor takes its share. |
| **Voltage at Fan (V_Fan)** | 4.21 V | 3.72 V | 2N2222 delivers roughly half a volt more to the motor, resulting in faster fan speed. |
| **— CALCULATED CURRENTS —**| | | |
| **Base Control Current (I_B)**| 10.7 mA | 9.27 mA | Both draw a very safe amount of current from the Arduino (well below the 20mA limit). |
| **Actual Fan Current (I_C)**| 151.0 mA | 134.0 mA | 2N2222 allows the fan to pull more current because it doesn't restrict the voltage. |
| **Forced Amplification (Beta)**| 14.1 | 14.4 | Both are heavily over-driven by the 330 ohm resistor to ensure they act as hard switches. |
| **— POWER & EFFICIENCY —** | | | |
| **Actual Fan Power (Output)**| 635 mW (0.63 W) | 498 mW (0.49 W) | 2N2222 drives the fan at ~70% of its max rating. TIP122 only drives it at ~55%. |
| **Transistor Heat (Wasted)**| 10.5 mW (0.01 W) | 92.4 mW (0.09 W) | TIP122 burns nearly 9x more power as heat, which is why it felt mildly warm to the touch. |
| **Total Circuit Efficiency**| **~98 %** | **~84 %** | **The Winner: 2N2222 is significantly more efficient for this low-voltage 5V application.** |
| **Effective Power Bank Supply**| ~4.28 V to 4.36 V | ~4.41 V to 4.47 V | Shows slight natural voltage variations from your power bank while under different load strains. |
