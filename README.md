# DHT-22-CON-LCD
Esta practica además de mostrar temperatura y humedad, mostrara nuestro nombre, y el modulo que se esta cursando.

Cargamos las siguientes librerias:

![](https://github.com/IVANZAGAL996/DHT-22-CON-LCD/blob/main/LIBRERIAS%202.PNG)


Realizamos el siguiente codigo en el sketch:

```
 
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

 lcd.clear();
 lcd.setCursor(2,0);
 lcd.print("DIPLOMADO V");
  lcd.setCursor(2,1);
  lcd.print("AUTOMATIZACION");
  delay(2000);

  lcd.clear();
 lcd.setCursor(2,0);
 lcd.print("IVAN ZAGAL");
  lcd.setCursor(2,1);
  lcd.print("ING MECANICA");
  delay(2000);

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  lcd.clear();
  lcd.setCursor(2, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");
delay(2000);

 
}
 ```

Insertamos el display;

![](https://github.com/IVANZAGAL996/DHT-22-CON-LCD/blob/main/LCD12.PNG)

Realizamos la sig conexion

![](https://github.com/IVANZAGAL996/DHT-22-CON-LCD/blob/main/CONEXION%202.PNG)


CARGAMOS Y COMPILAMOS OBTENIENDO LOS SIGUIENTES RESULTADOS:

![](https://github.com/IVANZAGAL996/DHT-22-CON-LCD/blob/main/r1.png)

![](https://github.com/IVANZAGAL996/DHT-22-CON-LCD/blob/main/r2.png)

![](https://github.com/IVANZAGAL996/DHT-22-CON-LCD/blob/main/r3.png)

## CREDITOS
DESARROLLADO POR:

EDGAR IVAN PROSPERO ZAGAL PONCE

[GitHub](https://github.com/IVANZAGAL996)










