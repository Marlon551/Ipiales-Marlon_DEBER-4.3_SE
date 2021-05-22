# Ipiales-Marlon_DEBER-4.3_SE
Ipiales Marlon_DEBER 4.3_SE
/*
*CAPITULO IV: PERIFERICOS ESPECIALES
*CODIGO 18: Uso timer 2
*OBJETIVO: Reloj con timer 2
*NOMBRE: Marlon Ipiales
*FUNCIONES:  MsTimer2::set(1000,flash);   //1s que dura el periodo
*           MsTimer2::star();
*           MsTimer2::stop(); 
*NOTA: Si no funcionara la compilacion escoger arduino uno WIFI caso contrario solo arduino uno , en caso de que el codigo muestre errores, ponga "Guardar como " al archivo y compile varias veces
*/
#include <MsTimer2.h>   //Libreria Timer 2
#include <LiquidCrystal.h>  //Libreria LCD
LiquidCrystal lcd(13,12,11,10,9,8);  //Objeto para la libreria de LCD 
int segundos=0;  //Variables de segundos, horas y minutos
int minutos=0;
int horas=0;    
void setup() {
  lcd.begin(20,4);   //Inicia la LCD
  MsTimer2::set(1000,reloj); //Configura el timer 2 a 1 segundo 
  MsTimer2::start();  //Inicia timer

}
void loop() {
}
void reloj(){
  if(segundos<60){   //Condicion de segundo
    segundos++;  //Incremento de variable
  }
  else{
    segundos=0;
    if(minutos<60){   //Condicion de minutos
      minutos++;   //Incrementa la variable
    }
    else{
      minutos=0;  
      if(horas<24){   //Condicion de horas
        horas++;  //Incrementa la variable
      }
      else{
        horas=0;
      }
    }
  }
  lcd.clear(); //Borrar el anterior mensaje
  lcd.setCursor(0,0); //Ubicacion de lcd
  lcd.print(String("Bienvenido usuario 1"));  //Mensaje de impresion
  lcd.setCursor(0,1); //Ubicacion de lcd
  lcd.print(String("Marlon Ipiales"));  //Mensaje de impresion
  lcd.setCursor(0,2); //Ubicacion de lcd
  lcd.print(String(horas)+String(":")+String(minutos)+String(":")+String(segundos));  //Mensaje de impresion
  lcd.setCursor(5,3); //Ubicacion de lcd
  lcd.print(String("1000,reloj"));  //Mensaje de impresion
}
