# Microserviço de Envio de E-mails com RabbitMQ

Bem-vindo ao Microserviço de Envio de E-mails! Este projeto é um exemplo de como usar o RabbitMQ para implementar a comunicação assíncrona e o envio de e-mails em um ambiente de microsserviços.

## Requisitos

Certifique-se de que você tenha os seguintes requisitos instalados:

- Java 17

## Configuração

1. Clone este repositório para o seu ambiente local.

2. Abra o arquivo `application.properties` localizado no diretório `src/main/resources`.

3. Configure as seguintes propriedades com as informações relevantes:

   ```properties
   spring.mail.host=<SEU SMTP AQUI>
   spring.mail.port=<SUA PORTA AQUI>
   spring.mail.username=<SEU EMAIL AQUI>
   spring.mail.password=<SUA CHAVE DE APLICATIVO AQUI>

   spring.rabbitmq.addresses= <SUA CHAVE AQUI>
   spring.rabbitmq.queue=<SUA FILA AQUI>
    

## Uso Síncrono
Além do envio assíncrono, você pode usar a API síncrona para enviar e-mails imediatamente. Use a rota adequada para enviar um e-mail diretamente:

   ```REQUEST
   POST /sending-email

   {
     "ownerRef":"<SEU NOME>",
      "emailFrom" : "EXEMPLOfrom@gmail.com",
      "emailTo" : "EXEMPLOto@hotmail.com",
      "subject" : "TESTE ENVIO!",
      "text" : "TEXTO DO EMAIL."
   }
   ````
  
     
## Uso Assíncrono

Execute o aplicativo e ele estará pronto para receber mensagens de e-mail assíncronas através do RabbitMQ.


Para enviar um e-mail assíncrono, envie uma mensagem formatada em JSON para a fila apropriada no RabbitMQ. O serviço de envio de e-mails processará essas mensagens e enviará os e-mails correspondentes.

Exemplo de mensagem para a fila de envio de e-mails assíncronos:

   ```json   
   {
      "ownerRef":"<SEU NOME>",
      "emailFrom" : "EXEMPLOfrom@gmail.com",
      "emailTo" : "EXEMPLOto@hotmail.com",
      "subject" : "TESTE ENVIO!",
      "text" : "TEXTO DO EMAIL."
   }
   ````