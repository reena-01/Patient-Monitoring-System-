// Patient-Monitoring-System-
//sensors
//contribute
//source-code
//web-ubidots linked
//arduino version

#
#
#



void setup() 
{ 
Serial.begin(115200);
ubidots.wifiConnect(WIFI_SSID, WIFI_PASS);
pinMode (A0, INPUT);
sensors.begin(); 
}
void loop() 
{
int h = analogRead(A0); 40
sensors.requestTemperatures(); 
floattempC = sensors.getTempCByIndex(0);
floattempF = sensors.getTempCByIndex(0);
Serial.print("Heart rate: ");
Serial.println(h);
Serial.print(tempC);
Serial.println("ºC");
Serial.print(tempF);
Serial.println("ºF");
ubidots.add("Heart", h);
ubidots.add("Temp", tempC);
ubidots.add("Temp", tempF);
boolbufferscent=false;
bufferscent=ubidots.send();
if(bufferscent)
 {
Serial.println("values sent");
 } 
delay(5000);
}
