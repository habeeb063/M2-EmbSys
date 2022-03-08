## Test Plan


|  Test ID | Description  | Input  | Output  |
|---|---|---|---|
|TID_01|` `Press ‘#’ to reset the password.|Pressed = #|Success|
|TID_02|` `Press ‘*’ to lock the door.|Pressed = * |Door Locked|
|TID_03|` `Green LED ON| LED pin High | Door is Open|
|TID_04|` `Red LED ON| LED pin High | Door is Locked|
|TID_05|` `Buzzer is ON|  After 3 false attempts | Buzzer pin High|
|TID_06|` `Door is open|Correct Password |Servo shaft on 0 degree angle|
|TID_07|` `Door is Closed|Wrong Password |Servo shaft on 90 degree angle|
|TID_08|` `Variable Out door light|LDR Sensor |Variable Intensity of light|


 
