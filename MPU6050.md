#include <Wire.h>

#define SENS_MPU 0x68
  

void setup() {
  Wire.begin();
  Wire.beginTransmission(SENS_MPU);
  Wire.write(0x6B);
  Wire.write(0);
  Wire.endTransmission(true);
  Serial.begin(9600);
  }
  
void loop() {
 int AX,AY,AZ,Tmp,GX,GY,GZ;
 Wire.beginTransmission(0x68);
 Wire.write(0x3B);
 Wire.endTransmission(false);
 Wire.requestFrom(SENS_MPU,14,true);
 AX=Wire.read()<<8|Wire.read();    
 AY=Wire.read()<<8|Wire.read();  
 AZ=Wire.read()<<8|Wire.read();  
 Tmp=Wire.read()<<8|Wire.read(); 
 GX=Wire.read()<<8|Wire.read();  
 GY=Wire.read()<<8|Wire.read();  
 GZ=Wire.read()<<8|Wire.read();
 Serial.print ("AX = ");  Serial.println(AX);
 Serial.print ("AY = "); Serial.println(AY);
 Serial.print ("AZ = "); Serial.println(AZ);
 Serial.print ("Tmp = "); Serial.println(Tmp/340.00+36.53);
 Serial.print ("GX = ");Serial.println(GX);
 Serial.print ("GY = "); Serial.println(GY);
 Serial.print ("GZ = "); Serial.println(GZ);
 delay (350);
}
  
 
