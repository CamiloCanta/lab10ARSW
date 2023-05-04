### Escuela Colombiana de Ingeniería
### Arquitecturas de Software - ARSW

## Julian Castillo y Camilo Cantillo

## Escalamiento en Azure con Maquinas Virtuales, Sacale Sets y Service Plans

### Dependencias
* Cree una cuenta gratuita dentro de Azure. Para hacerlo puede guiarse de esta [documentación](https://azure.microsoft.com/es-es/free/students/). Al hacerlo usted contará con $100 USD para gastar durante 12 meses.
Antes de iniciar con el laboratorio, revise la siguiente documentación sobre las [Azure Functions](https://www.c-sharpcorner.com/article/an-overview-of-azure-functions/)

### Parte 0 - Entendiendo el escenario de calidad

Adjunto a este laboratorio usted podrá encontrar una aplicación totalmente desarrollada que tiene como objetivo calcular el enésimo valor de la secuencia de Fibonnaci.

**Escalabilidad**
Cuando un conjunto de usuarios consulta un enésimo número (superior a 1000000) de la secuencia de Fibonacci de forma concurrente y el sistema se encuentra bajo condiciones normales de operación, todas las peticiones deben ser respondidas y el consumo de CPU del sistema no puede superar el 70%.

### Escalabilidad Serverless (Functions)

1. Cree una Function App tal cual como se muestra en las  imagenes.

![](images/part3/part3-function-config.png)

![](images/part3/part3-function-configii.png)

## Funcion creada

![image](https://user-images.githubusercontent.com/96396177/234867137-35a7c799-03fb-4712-b64d-1da417275f33.png)


2. Instale la extensión de **Azure Functions** para Visual Studio Code.

![](images/part3/part3-install-extension.png)

3. Despliegue la Function de Fibonacci a Azure usando Visual Studio Code. La primera vez que lo haga se le va a pedir autenticarse, siga las instrucciones.

![](images/part3/part3-deploy-function-1.png)

![](images/part3/part3-deploy-function-2.png)

4. Dirijase al portal de Azure y pruebe la function.

![](images/part3/part3-test-function.png)


![image](https://user-images.githubusercontent.com/108955358/234884151-bee6d082-554e-4a57-8c47-42b2a95d42d3.png)

5. Modifique la coleción de POSTMAN con NEWMAN de tal forma que pueda enviar 10 peticiones concurrentes. Verifique los resultados y presente un informe.



6. Cree una nueva Function que resuleva el problema de Fibonacci pero esta vez utilice un enfoque recursivo con memoization. Pruebe la función varias veces, después no haga nada por al menos 5 minutos. Pruebe la función de nuevo con los valores anteriores. ¿Cuál es el comportamiento?.


## funciona creada con memorizacion

![image](https://user-images.githubusercontent.com/96396177/235834608-da9d3a23-268c-4358-8b09-0ce1532a3cbd.png)





**Preguntas**

* ¿Qué es un Azure Function?


rta: Un Azure Function es un servicio de Azure que permite ejecutar código en la nube sin necesidad de preocuparse por el mantenimiento de los servidores
  
* ¿Qué es serverless?

rta: Serverless es un modelo de cómputo en el que los proveedores de servicios en la nube, como Azure, son los responsables de administrar y escalar la infraestructura subyacente en la que se ejecuta el código.


* ¿Qué es el runtime y que implica seleccionarlo al momento de crear el Function App?

es el entorno en el que se ejecutará el código de la función. Al crear una Function App en Azure, se puede seleccionar uno de los runtimes preconfigurados de Azure o crear un runtime personalizado


* ¿Por qué es necesario crear un Storage Account de la mano de un Function App?

Es necesario crear un Storage Account (Cuenta de almacenamiento) porque las Function Apps utilizan los servicios de almacenamiento de Azure para almacenar los datos necesarios para el funcionamiento de la aplicación.

* ¿Cuáles son los tipos de planes para un Function App?, ¿En qué se diferencias?, mencione ventajas y desventajas de cada uno de ellos.

Plan Consumo: Este es el plan más común y es adecuado para cargas de uso esporádico o de bajo a medio. Los recursos se escalan automáticamente según sea necesario y solo paga por el tiempo de actividad y el uso de recursos. 

Plan premium: este plan es adecuado para cargas de trabajo de alto uso y ofrece más recursos y funciones que el plan de consumo. La facturación se basa en la tasa de reserva mensual y el uso de recursos

Plan de App Service: este plan se ejecuta en una máquina virtual dedicada, lo que brinda mayor flexibilidad y control sobre la infraestructura subyacente. Es adecuado para cargas de trabajo de alta utilización o aplicaciones que requieren funciones específicas del sistema operativo. La facturación se basa en el precio de la máquina virtual subyacente.


* ¿Por qué la memoization falla o no funciona de forma correcta?

La memorización con enfoque recursivo requiere espacio de memoria para almacenar los resultados previamente calculados. Si la cantidad de datos almacenados en la memoria supera el límite disponible, la función puede fallar o no funcionar correctamente.

* ¿Cómo funciona el sistema de facturación de las Function App?

El sistema de facturación de las Function Apps de Azure se basa en el consumo de recursos, como el tiempo de ejecución, la memoria utilizada, el número de solicitudes y el almacenamiento de datos. Cada plan de precios tiene una estructura de tarifas diferente, que puede incluir una tasa de reserva mensual, un límite de tiempo de ejecución y un costo adicional por GB de almacenamiento. La facturación se calcula según la cantidad de recursos consumidos y se muestra en el portal de Azure.

* Informe

Informe de Pruebas de Rendimiento
Este informe describe los resultados de las pruebas de rendimiento de una API.

Resumen de Ejecución


Iteraciones Ejecutadas: 10


Solicitudes Enviadas: 10


Solicitudes Fallidas: 0


Duración Total de la Prueba: 2 minutos y 6 segundos


Rendimiento de las Solicitudes


Datos Recibidos: 2.09 MB (aproximadamente)


Tiempo de Respuesta Promedio: 12.5 segundos


Mínimo: 12.2 segundos


Máximo: 13.4 segundos


Conclusiones


Los resultados de las pruebas indican que la API o aplicación web es capaz de manejar el volumen de solicitudes enviadas durante las pruebas sin fallas. Sin embargo, el tiempo de respuesta promedio de 12.5 segundos puede ser considerado como un punto de mejora.
