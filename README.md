#include <IRremote.h>
#include <LiquidCrystal.h>
 
const int RS = 12, EN = 11, D4 = 5, D5 = 4, D6 = 3, D7 = 2;
LiquidCrystal lcd(RS, EN, D4, D5, D6, D7);
int RECV_PIN = 6;
IRrecv irrecv(RECV_PIN);
decode_results results;
 
 
void setup()
{
  irrecv.enableIRIn(); 
  lcd.begin(16, 2);
}
 
void loop() {
  if (irrecv.decode(&results)) {
  lcd.setCursor(0,0);
  lcd.clear();
  lcd.print("IR remote Code");
  lcd.setCursor(0,1);
  lcd.print("Code : ");
  lcd.print(results.value);
  irrecv.resume(); 
  }
  delay(100);
}
