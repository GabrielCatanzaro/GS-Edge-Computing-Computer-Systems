# GS-Edge-Computing-Computer-Systems
GS  01 de Edge Computing com todos entregáveis, links e participantes


Participantes:

RM: 98765 - Filipe Prado Menezes
RM: 93445 - Gabriel Gomes Catanzaro
RM: 88166 - Pedro Henrique Salvitti
RM: 98766 - Lucas Gomes Alcantara

Ideia: Sistema de monitoramento de umidade do solo em tempo real

Descrição: O sketch em Arduino consiste em um sistema de monitoramento de umidade do solo em tempo real. Ele utiliza um sensor de umidade do solo conectado a um microcontrolador Arduino, que é programado para ler os 
dados do sensor e transmiti-los através de uma interface LCD

Passos para implementação:

1.	Materiais necessários:
  •	Arduino Uno ou outra placa compatível.
  •	Sensor de umidade do solo.
  •	Motor CC.
  •	Jumpers e componentes eletrônicos necessários.
  •	Display LCD.
  •	Potenciômetro.
  •	Resistores.
  
2.	Conexões:
  •	Conecte o sensor de umidade do solo ao Arduino de acordo com as instruções do fabricante.
  •	Conecte o motor de acordo com as instruções do fabricante.
  •	Conecte o display LCD de acordo com as instruções do fabricante
  
3.	Programação:
  •	Escreva um código Arduino que leia os dados do sensor de umidade do solo em intervalos regulares.
  •	Inclua um botão de ligar e desligar o display LCD (foi usado um potenciômetro para futuras atualizações).
  •	Escreva um código que ligue o motor de irrigação quando o solo estiver no estado “seco”.
  
4.  Benefícios:
  •	O agricultor pode monitorar a umidade do solo em tempo real tendo um controle melhor, podendo configurar manualmente os valores de acordo com o que precisar.
  •	Com base nos dados de umidade do solo, o agricultor pode tomar decisões informadas sobre irrigação, evitando tanto o desperdício quanto a escassez de água.
  •	A detecção precoce de problemas de umidade, como solos muito secos ou excessivamente úmidos, permite a implementação de medidas corretivas oportunas, como ajustar os ciclos de irrigação.
  
--------------------------------------------------------------------------------
 
 Codigo usado no arduíno:
  
// ## Display LCD 16x2
//FUNCIONANDO
#include <LiquidCrystal.h>
//conecta os pinos no arduino isso vem da biblioteca
const int rs = 3, en = 4, d4 = A2, d5 = A3, d6 = A4, d7 = A5;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
float valor_potencia;
int umidade;//recebe do sensor os valores 
int motorPin =5;//pino do motor
int motorState = 1;//estado do motor
void setup() { 
  // inicia a tela
  lcd.begin(16, 2);//inicia 
  lcd.print("Iniciando...");
  delay(1000);
  lcd.clear();//limpa
  pinMode(motorPin, OUTPUT);  
} 
void loop() { 
  umidade=analogRead(A0);
// define a entrada analogica na porta A01
  lcd.begin(16, 2); 
  // Print a message to the LCD. 
  lcd.setCursor(0, 0); // posição que ira imprimir na tela
  //lcd.print("PROJECT");
  delay(1000);
  lcd.setCursor(4, 1);//seta a posição do texto
  if (umidade > 450){//se for maior que 450 
  lcd.print("Solo Umido");
  lcd.setCursor(0, 0);//imprimi no inicio da tela
  digitalWrite(motorPin, LOW);//desliga motor
    
  if (umidade == analogRead(LOW)){
    digitalWrite(motorPin, LOW);//liga motor
  }    
  }else if (umidade < 450){ 
    lcd.print("Solo Seco");
    motorState = digitalRead(motorPin);  
     digitalWrite(motorPin, HIGH);//liga motor  
  }  
  delay(2000);
  lcd.clear();
}

--------------------------------------------------------------------------------

Link de acesso para o tinkercad:

https://www.tinkercad.com/things/3oNG4DrvHZP-glorious-jofo/editel?sharecode=gAU9-2lpuSkxAbAUMTwTRvXsOVlts4tu7rnMKlaSMQU


