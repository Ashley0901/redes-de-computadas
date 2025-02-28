🚀 Practica 1 redes de computadoras usando Flask 

Este proyecto implementa una API en Flask que permite enviar y recibir variables entre nodos a través de solicitudes HTTP.

📌 Características
Inicializa una variable y la envía a otro nodo.
Recibe la variable, la incrementa y la reenvía.
Finaliza el proceso cuando la variable alcanza un valor de 50.

📋 Requisitos

Python 3 instalado.

Dependencias necesarias instaladas:
flask
getmac
ngrok

🛠 Instalación y Ejecución:

Clona este repositorio o copia el código fuente.

Instala las dependencias necesarias con:
pip freeze > requirements.txt


Ejecuta el servidor Flask:
La forma de enviar un nodo a cada servidor es por medio de tuneles, en este caso estamos usando ngrok para transferir el valor de una variable
al siguiente nodo, la forma en que se realiza este procedimiento es de la siguiente forma:


1.cada integrante tendra un puerto diferente: app.run(port = 500X)
Integrante1 : puerto 5001
Integrante2 : puerto 5002
Integrante3 : puerto 5003
Integrante4 : puerto 5004

Esa url la copiamos y pegamos en la web.


-2. En una nueva terminal ejecutar el comando ngrok http 5001(en mi caso, ya que el puerto 5001 será mi puerto)
Esto creara la ruta para ese puerto la cual dejara de ser local y podremos copiar y pegar en el codigo en la parte de
la variable next_node del otro servidor
Esta sustituira la ruta local del puerto 5001 y creara un tunel que es el url al cual se mandara el mensaje
el puerto a donde se mandara la variable

-2. Ejecutar el servidor con el comando :
flask --app server run --port 5001
Esto iniciara el servidor


-3.una vez realizado los pasos anteriores
Yo el integrante1 dare inicio al proceso que mandara la variable al integrante 2 de la siguiente manera:
desde el url de ngrok que redirige a mi puerto lo copiaremos y lo pegaremos en la web
agregaremos  /start_process     al final del url y daremos enter

Esto empezara el proceso de enviar nodos a cada uno de los integrantes, en mi caso mandare la variable al integrante 2
y recibire la variable del integrante 4 (ya que el integrante 4 sera el que envie el valor de su variable en el ciclo)
esto se repetira hasta que se alcance un maximo de 50 en la variable


Endpoints:

GET /start_process
Inicia el proceso enviando la variable inicial al nodo siguiente.

Respuesta JSON:

{
  "message": "mensaje enviado",
  "variable": 0
}

POST /receive_variable
Recibe una variable, la incrementa y la reenvía al siguiente nodo.
Si la variable alcanza 50, el proceso finaliza.


🏗 Estructura del Código:

send_message(variable): Envía la variable al siguiente nodo mediante una solicitud POST.

start_process(): Inicia el proceso enviando la variable inicial 

receive_variable(): Recibe la variable, la incrementa y la reenvía o finaliza el proceso.



⚖ Licencia
Este proyecto es de código abierto bajo la licencia MIT.

👤 Autor
Ashley0901



