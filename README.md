# Manchester-Based Master-Slave Bus Interface 
### Important Note ⚠️ : Keep in mind that this is an informal report just to demonstrate what I learned and was able to accomplish with this work! The report is explained in English!

### Summary:
This project implements a Master-Slave communication system using Manchester encoding for data transmission. The system ensures synchronized communication, correct addressing of sensors, and error detection mechanisms to maintain data integrity.

### Key Components & Functionality:

**Communication Structure**

- The system follows a Master-Slave (bus-based) architecture.

- Data exchange occurs using Manchester encoding, which combines clock and data into a single signal.

**Data Transmission & Encoding**

- Before transmission, sensor data is encoded into Manchester code using an XNOR gate with the clock signal.

- The ACK signal is sent first and also encoded using an OR gate with the clock.

- The ENABLE signal ensures that the sensor only writes to the bus at the correct time.

**Address Recognition & Acknowledgment**

- Each sensor has a predefined address stored in buffers.

- When a matching address is detected, the sensor sends an ACK signal to confirm recognition.

- Transmission only starts once ACK is completed and ENABLE is active.

**Error Detection System**

- The system monitors synchronization between clock and busdata.

- An XNOR gate compares Dout (sensor output) and busdata to check for errors.

- If an error is detected, the ERROR signal is activated, forcing busdata to "1" and terminating communication.

**Communication Termination**

- The STOP signal detects the end of transmission when two idle states appear.

- The ERROR signal also triggers termination if synchronization issues occur.
