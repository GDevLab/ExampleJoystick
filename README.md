# ExampleJoystick

Using the joystick pins
- VCC
- GND
- VRx -> Variable resistance x
- VRY -> Variable resistance Y
- SW -> Switch / Button

Connection
- MODULE -> ARDUINO
- VCC -> 5V
- GND -> GND
- VRx -> A0
- VRy -> A1
- SW -> Pin 2

Set Pin
~~~C
int VRx = A0;
int VRy = A1;
int SW = 2;
~~~
Set Variable
~~~C
int xPosition = 0;
int yPosition = 0;
int SW_state = 0;
int mapX = 0;
int mapY = 0;
~~~
กำหนดค่าเริ่มต้นของโปรแกรม
~~~C
void setup() {
  Serial.begin(9600); 
  
  pinMode(VRx, INPUT);
  pinMode(VRy, INPUT);
  pinMode(SW, INPUT_PULLUP); 
  
}
~~~
กระบวนการ การทำงานของโปรแกรม
~~~C
void loop() {
  xPosition = analogRead(VRx);
  yPosition = analogRead(VRy);
  SW_state = digitalRead(SW);
  mapX = map(xPosition, 0, 1023, -512, 512);
  mapY = map(yPosition, 0, 1023, -512, 512);
  
  Serial.print("X: ");
  Serial.print(mapX);
  Serial.print(" | Y: ");
  Serial.print(mapY);
  Serial.print(" | Button: ");
  Serial.println(SW_state);

  delay(100);  
}
~~~
