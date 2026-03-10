# Control of Discrete Outputs of Industrial PLC Controllers

Course project  
Discipline: Software and Hardware Support of Computer-Integrated Systems

Controllers used in the project:

- Lomikont L-110
- PLC154
- MIK-51

The project demonstrates the development of control algorithms for discrete outputs of PLC controllers using industrial programming environments and IEC 61131-3 languages.

---

# Project Highlights

⚙️ Development of discrete output control algorithms for industrial PLCs  

🧠 Implementation using IEC 61131-3 languages (ST, FBD)

🖥 Programming and simulation in CoDeSys and Alfa environments

📊 Comparative analysis of three industrial controllers

---

# Problem Statement

The goal of the project is to develop a control algorithm for programmable logic controllers that controls discrete outputs based on input signals.

The system operates using:

Inputs:

- **di2** – discrete input
- **ai1** – analog input
- **ai2** – analog input

Outputs:

- **do1**
- **do2**
- **do3**
- **do4**

The switching time for outputs is **3 seconds**.

---

# Control Logic

The control system operates in three modes.

### Mode 1

Condition: ai1 > ai2 AND di2 = OFF



Action:

Sequential activation:do1 + do2 then do3 + do4


Each state lasts **3 seconds**.

---

### Mode 2

Condition: ai1 < ai2 AND di2 = ON


Action:

Sequential activation: do1 + do3 then do2 + do4


Each state lasts **3 seconds**.

---

### Mode 0

If none of the conditions are satisfied: all outputs OFF



A technological message is displayed indicating the current system state.

---

# PLC154 Implementation

The PLC154 controller was programmed using **CoDeSys**.

Two program implementations were developed:

- **Structured Text (ST)**
- **Function Block Diagram (FBD)**

Timers used in the program:

- TON
- TOF

Example ST implementation:

```ST
timer3(IN := NOT reset, PT := t#6s, Q => reset, ET => chas);

IF (din2 = FALSE) AND (ai1 > ai2)
THEN
    IF chas < t#3s THEN
        out1 := TRUE;
        out2 := TRUE;
    ELSE
        out3 := TRUE;
        out4 := TRUE;
    END_IF
END_IF
```


---

# Visualization Interface

A visualization interface was implemented in CoDeSys for testing the algorithm.

Screens developed:

* Main menu
* Input control panel
* Output monitoring panel

The interface allows simulation of input signals and visualization of output states.

---

# Controllers Used

### Lomikont L-110

Industrial PLC used for multi-channel automation systems.
Supports expansion modules and industrial communication interfaces.

---

### PLC154

PLC controller supporting IEC 61131-3 programming languages.
Used with the CoDeSys development environment.

---

### MIK-51

Compact controller with extended communication capabilities and flexible configuration.

---

# Comparative Analysis

The developed algorithms were implemented for all three controllers.

The comparison showed that:

* all controllers successfully implement the required control logic
* each controller has different advantages depending on the automation task
* PLC154 provides flexible programming through IEC 61131-3 languages
* Lomikont L-110 is suitable for large industrial systems
* MIK-51 offers compact design and flexible communication options

---

# Technologies Used

* PLC Programming
* IEC 61131-3
* Structured Text (ST)
* Function Block Diagram (FBD)
* CoDeSys
* Alfa programming environment

---

# Conclusion

The project demonstrates the development of control algorithms for discrete outputs in industrial PLC systems.

The algorithms were implemented and tested on three different controllers, and a comparative analysis of their implementation was performed.

The results show that PLC controllers provide flexible and reliable solutions for industrial automation tasks.
