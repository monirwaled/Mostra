double calculoVazao;
volatile int contador;
float fluxoAcumulado =0;
float metroCubico = 0;
float ContaAgua = 0;

void setup() {
  // put your setup code here, to run once:
 pinMode(2 , INPUT);
 attachInterrupt(0, Vazao, RISING);
 Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
  contador = 0;
  interrupts();
  delay(1000);
  noInterrupts();

 calculoVazao= (contador * 2.25);
 fluxoAcumulado = fluxoAcumulado + (calculoVazao / 1000);
 metroCubico =  fluxoAcumulado / 1000;
 ContaAgua = metroCubico * 3,50;
 calculoVazao = calculoVazao * 60;
 calculoVazao = calculoVazao / 1000;

 Serial.println( "Litros por minutos : ");
 Serial.println(calculoVazao);
 Serial.println("Gasto total L : "); 
 Serial.println(fluxoAcumulado);
 Serial.println("Metros cubicos totais :");
 Serial.println(metroCubico);
 Serial.println("R$ : ");
 Serial.println(ContaAgua);


 
}
 void Vazao()
 {
 contador ++;
 }
