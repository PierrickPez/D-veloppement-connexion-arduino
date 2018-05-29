# D-veloppement-connexion-arduino
#en branchant le port bluetooth au serial 1 et en envoyant a b et c au téléphone
# http://gilles.thebault.free.fr/spip.php?article51
int a = 10;
int b = 20;
int c = 45;
 
void setup() {
  // put your setup code here, to run once:
  Serial1.begin(9600);
}
 
void loop() {
  Serial1.print(a);
  Serial1.print(",");
  Serial1.print(b);
  Serial1.print(",");
  Serial1.print(c);
  delay(1000);
}

//

#https://openclassrooms.com/forum/sujet/echange-de-donnees-android-arduino-bluetooh

#include <SoftwareSerial.h>
 
SoftwareSerial HC06(11,10);
const char DOUT_LED = 13;
String messageRecu;
int temps = 0;
int temperature = 45;
int rh = 70;
int qnh = 1013;
void setup() {
  Serial.begin(9600);
  HC06.begin(9600); 
  pinMode(DOUT_LED, OUTPUT);
  digitalWrite(DOUT_LED, HIGH);
  temps = millis() + 1000;
}
  
void loop()
{
  if(HC06.available()){
    Serial.println(HC06.read());
  }
  if(millis() > temps){
    HC06.write(temperature);
    Serial.write(temperature);
    delay(30);
    HC06.write("T");
    delay(30);
    HC06.write(rh);
    delay(30);
    HC06.write("R");
    delay(30);
    HC06.write(qnh);
    delay(30);
    HC06.write("Q");
    temps = millis() + 3000;
  }
}
when ( dataAvailable() ) {
 
    c = ReadData()
 
    if ( c == ';' ) {
 
        list = str.split("=");
 
        key = list[0];
        val = list[1];
 
        if        ( key == "T") {
            // ICI: traiter le cas d'une réception de température
        } else if ( key == "...") {
            ...
        }
 
    else {
        str = str + c;
    }
 
}
HC06.print("T=");
HC06.print(temperature);
HC06.print(';');
 
HC06.print("R=");
HC06.print(...);
HC06.print(';');
