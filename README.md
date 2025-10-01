# Secure Code Lock System Using CD4017 with Wrong Code Alert

## Authors

- **Md. Faisal Iftekhar**  
  Department of Computer Science and Engineering  
  BRAC University, Dhaka, Bangladesh  
  Email: [md.faisal.iftekhar@g.bracu.ac.bd](mailto:md.faisal.iftekhar@g.bracu.ac.bd)

- **Sriti Peach Catiloc Sikdar**  
  Department of Computer Science and Engineering  
  BRAC University, Dhaka, Bangladesh  
  Email: [sritipeach.catiloc.sikdar@g.bracu.ac.bd](mailto:sritipeach.catiloc.sikdar@g.bracu.ac.bd)

- **Muftasim Fuad Mahee**  
  Department of Computer Science and Engineering  
  BRAC University, Dhaka, Bangladesh  
  Email: [muftasim.fuad.mahee@g.bracu.ac.bd](mailto:muftasim.fuad.mahee@g.bracu.ac.bd)

---

## Abstract

This project demonstrates the design, construction, and analysis of a secure sequential code lock system built using only discrete digital logic ICs. The system uses cascaded **CD4017 decade counters** to manage the code sequence, **CD4081 AND gates** for precise error detection, and an **NE555 timer** to ensure reliable system-wide resets.

Unlike microcontroller-based systems, this fully hardware-based approach ensures immunity from software vulnerabilities and provides educational insight into the core principles of digital logic and sequential state management.

---

## Table of Contents

- [System Overview](#system-overview)
- [Components Used](#components-used)
- [Working Principle](#working-principle)
- [Error Detection Mechanisms](#error-detection-mechanisms)
- [Construction Challenges](#construction-challenges)
- [Future Improvements](#future-improvements)
- [References](#references)
- [Acknowledgment](#acknowledgment)

---

## System Overview

- **Code format**: `A-BB-C-D-E`
- **Functionality**: Accepts only the correct sequence of key presses to unlock.
- **Security feature**: Any incorrect or out-of-sequence input triggers a system reset and activates a wrong-code alert.

---

## Components Used

- **CD4017** – Decade counter (5 ICs cascaded)
- **CD4081** – Quad 2-input AND gate (used for error detection)
- **NE555 Timer** – Configured in monostable mode for system reset pulse
- **1N4148 Diodes** – Used for wired-OR logic and protection
- **LEDs** – Indicate stage completions and unlock status
- **Pushbuttons** – Used as input keys
- **Capacitors (100nF)** – Used for switch debouncing
- **Breadboards** – Circuit assembled on two 830-point breadboards

---

## Working Principle

### Correct Code Entry Sequence (`A-BB-C-D-E`)

1. **Stage 1 - 'A'**: Advances first CD4017; enables Stage 2.
2. **Stage 2 - 'BB'**: Requires two 'B' presses; uses diodes for counting; enables Stage 3.
3. **Stage 3 - 'C'**: Advances third CD4017; enables Stage 4.
4. **Stage 4 - 'D'**: Advances fourth CD4017; enables Stage 5.
5. **Stage 5 - 'E'**: Final input; unlocks system by turning on the "Unlock" LED.

---

## Error Detection Mechanisms

1. **Unused Key Press**: Any invalid key immediately triggers the NE555 reset circuit.
2. **Out-of-Sequence Press**: AND gates detect premature key presses and reset the system.
3. **Repeated Key Press**: Extra presses after a correct stage completion are detected and trigger reset.

---

## Construction Challenges

- **Switch Debouncing**: Solved using 100nF capacitors in parallel with switches.
- **Reset Signal Reliability**: NE555 timer ensures a stable 70ms reset pulse across all counters.
- **Wiring Complexity**: Managed with color-coded wires and structured layout for easier troubleshooting.

---

## Future Improvements

- **Security Enhancement**: Remove stage-completion LEDs to prevent feedback to attackers.
- **Lockout Feature**: Implement a failed-attempt counter and timed lockout after 3 wrong attempts.
- **Customizable Codes**: Integrate DIP switches to allow users to set/change the unlock code.
- **Scalability**: Add more stages with additional CD4017 ICs for longer codes.

---

## Acknowledgment

Special thanks to the **Friendly Wire** website for offering detailed guidance and educational resources that inspired and informed the development of this project.

---
