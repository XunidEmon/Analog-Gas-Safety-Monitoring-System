# Analog-Gas-Detector

| Safe Mode | Warning Mode | Danger Mode |
|-----------|--------------|-------------|
| 🟢 Green LED  |  🟡 Yellow LED  | 🔴 Red LED + 🔊 Buzzer |
|   Gas < 3.3V  | 3.3V < Gas < 4V  |        Gas > 4V        |


## 📊 Serial Plotter Output

*Real-time gas concentration graph from Arduino Serial Plotter*

## 🛠️ Project Status

| Status | Description |
|--------|-------------|
| ✅ **Completed** | Circuit design & testing done |
| ✅ **Working** | System works perfectly |
| 📝 **Documented** | Full documentation available |

/*
 * Gas Detection System - Serial Plotter Graph View
 * 
 * Purpose: ONLY for showing gas concentration graph in Serial Plotter
 * Circuit works perfectly WITHOUT Arduino!
 * 
 * How to use:
 * 1. Connect sensor output to Arduino A0
 * 2. Upload this code
 * 3. Open Tools → Serial Plotter (9600 baud)
 * 4. See real-time graph!
 */


'''c
int sensorPin = A0;        // Gas sensor output pin
int sensorValue = 0;       // Raw ADC value (0-1023)
float voltage = 0.0;       // Voltage (0-5V)

void setup() {
  Serial.begin(9600);      // Start serial communication
}

void loop() {
  // Read sensor value
  sensorValue = analogRead(sensorPin);
  
  // Convert to voltage (0-5V)
  voltage = sensorValue * (5.0 / 1023.0);
  
  // Print ONLY voltage for Serial Plotter
  // Serial Plotter expects only numbers separated by space or newline
  Serial.println(voltage, 3);  // 3 decimal places
  
  delay(100);  // Read 10 times per second (smooth graph)
}
'''
