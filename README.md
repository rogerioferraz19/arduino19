# arduino19
  #include <IRremote.h> // Biblioteca para controlar o led infravermelho  
  IRsend irsend; // Variável para poder enviar o código a TV 
 
  // Variáveis constantes para o controle remoto  
  // Pino onde estará o botão para aumentar o volume 
  const int mais_volume = 4;   
  
  // Pino responsavél por diminuir o volume
  const int menos_volume = 5;  
  
  // Pino onde estará o botão para mudar o canal em ordem crescente
  const int mais_canal = 6;  
  
  // Pino responsavél por mudar o canal em ordem decrescente  
  const int menos_canal = 7;   
  
  // Pino onde estará o botão que iremos ligar/desligar a TV 
  const int liga_desliga = 8;  
  
  // Pino onde iremos conectar o LED emissor de infravermelho
  const int ledIR = 3;         
 
  // Inicia o botão com o valor do estado em 0   
  int buttonState = 0;     
 
  void setup() {      
  pinMode(ledIR ,OUTPUT); // Definimos o LED de infra como de saída 
 
  Serial.begin(9600);   // Iniciamos o Serial Monitor
 
  // Configurando as entradas dos botões como de entrada
  pinMode(mais_volume, INPUT);   
  pinMode(menos_volume, INPUT);   
  pinMode(mais_canal, INPUT);   
  pinMode(menos_canal, INPUT); 
  pinMode(liga_desliga, INPUT);
  }  
 
  void loop(){  
  // Se o botão mais_volume for pressionado ele ira enviar o código...
  //para aumentar o volume na TV 
  if (digitalRead(mais_volume) == HIGH) { 
  
  // Código que será enviado a TV para aumentar o volume  (Como a... 
  //sintaxe manda devemos iniciar com 0x + número em hexadecimal, 32) 
  irsend.sendNEC(0xE0E0E01F, 32); 
  
  }     
 
// Se o botão menos_volume for pressionado ele irá enviar o código para... 
//diminuir o volume na TV
  if (digitalRead(menos_volume) == HIGH) { 

// Código que será enviado a TV para diminuir o volume    
   irsend.sendNEC(0xE0E0D02F, 32);  
  }    
 
// Se o botão mais_canal for pressionado ele irá enviar o código para... 
//aumentar o canal na TV 
  if (digitalRead(mais_canal) == HIGH) {      
   irsend.sendNEC(0xE0E048B7, 32);    
  }     

// Se o botão menos_canal for pressionado ele irá enviar o código para... 
//diminuir o canal na TV
  if (digitalRead(menos_canal) == HIGH) {      
   irsend.sendNEC(0xE0E008F7, 32);    
  }    
 
// Se o botão liga_desliga for pressionado ele irá enviar o código para... 
//ligar/desligar a TV 
  if (digitalRead(liga_desliga) == HIGH) {
    irsend.sendNEC(0xE0E040BF, 32);
   }  
   }
