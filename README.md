# Kube-Magic

_Proyecto realizado para el módulo de proyecto de ASIR sobre Kubernetes._

 <div align="justify"> Con este proyecto lo que pretendo es utilizar Kubernetes y otras herramientas complementarias a esta tecnología para establecer un entorno funcional de distintas aplicaciones desplegándolas a través de Kubernetes, implementando Azure Kubernetes Service y monitorearlas con Prometheus, Grafana y Azure Monitor. Para ello voy a seguir las siguientes partes/fases que he diferenciado de las que constará este proyecto. </div>

## Primera Parte:
 <div align="justify">En esta primera parte voy a explicar de manera general los conceptos básicos necesarios para entender bien que es Kubernetes, cómo funciona y que podemos hacer con él. también repasaremos los conceptos y objetos que forman parte de Kubernetes. Además de cómo yo lo he usado para llevar a cabo mi proyecto. Estimo que esta parte de investigación y documentación me tome toda la duración del proyecto. </div> <br>

![Alt text](https://github.com/JavierRamirezMoral/Kube-Magic/assets/101793125/2e29e27a-7dad-4717-b9d2-6b3f443cf460)

## Segunda Parte:

Voy a desplegar dos aplicaciones para hacer un típico set up de aplicaciones web con bases de datos:
* Una aplicación Web (Wordpress o Apache, por ejemplo)
* Una base de datos (MariaDB o MySQL, por ejemplo)
 <div align="justify"> Primero instalo minikube para crear el clúster y luego me sirvo de kubectl para interactuar y hacer todas las operaciones pertinentes en él. Voy a crear el pod para MariaDB con un Deployment y un internal service para comunicarme con él y que no reciba peticiones del exterior del clúster, solo los elementos que estén dentro del mismo clúster. Después voy a crear el pod para WordPress con un deployment donde tendré la URL de MariaDB dentro de un ConfigMap para poder conectarme a ella. Además de que tendrá  una autentificación para acceder a la base de datos, esto lo haré en el deployment (archivo  yaml) que tendrá dentro definido un Secret con las credenciales. Una vez tenga todo esto, voy a necesitar que Wordpress sea accesible a través de un navegador, para ello voy a crear un External service. Con esto voy a permitir peticiones desde el exterior para hablar con el pod. </div> <br>

Sería algo así: 

1. La petición llega del navegador.
2. Llega al External service del Wordpress.
3. Se envía así al pod de WordPress.
4. El pod de WordPress se conecta al internal service de MariaDB.
5. Y llega al pod de MariaDB donde se autentifica con las credenciales.
      
Elementos de configuración que también incluiré en esta parte:

* Namespaces para cada pod.
* Cuotas y límites de recursos.
* Uso de labels.
* Stateful and deployment.
* Volúmenes persistentes.

<div>
    <img  width="100%" src="https://github.com/JavierRamirezMoral/Kube-Magic/blob/main/Documentaci%C3%B3n%20Presentaci%C3%B3n/2.jpg">
</div>

## Tercera Parte:

 <div align="justify">Para esta parte me serviré de Azure Kubernetes Service que es un servicio de orquestación de contenedores completamente administrado que se ejecuta en Microsoft Azure. AKS proporciona un entorno de clúster de Kubernetes que simplifica la implementación, la administración y la escalabilidad de aplicaciones en contenedores. Con AKS, podemos implementar rápidamente aplicaciones de contenedores en un entorno altamente disponible y escalable. Integrar el clúster de la segunda parte. En esta parte lo que pretendo es integrar el clúster donde tenemos el primer escenario ya creado para poder administrarlo de manera más eficiente desde Azure. Y posteriormente montar el segundo set up creando un nuevo clúster con dos aplicaciones desplegadas por HELM en el también para la segunda página web con su correspondiente base de datos.</div> <br>

  * Integrar el clúster recién creado en la segunda parte en la nube de Azure.
  * Crear un clúster nuevo, mediante el portal de Azure.
  * Desplegar las dos aplicaciones similares a las de la segunda parte mediante HELM CHARTS.
      
<div>
    <img  width="100%" src="https://github.com/JavierRamirezMoral/Kube-Magic/blob/main/Documentaci%C3%B3n%20Presentaci%C3%B3n/3.jpg">
</div>

## Cuarta Parte:
 <div align="justify"> En esta parte vamos a añadir y configurar el monitoreo de nuestro escenario usando las siguientes herramientas que iremos viendo a continuación. Para asegurarnos de que todo funciona correctamente en nuestros escenarios.Con Prometheus, Grafana y Azure Monitor empleando reglas, parámetros y métricas.Azure Monitor es un servicio de monitoreo y diagnóstico de aplicaciones y recursos en la nube de Microsoft Azure. Prometheus es un sistema de monitoreo y alerta de código abierto que se utiliza para recopilar y almacenar métricas de diferentes componentes de un clúster de Kubernetes, como pods, contenedores, nodos, servicios y redes. Grafana, por su parte, es una herramienta de visualización y análisis de datos que permite a los usuarios crear paneles y gráficos personalizados a partir de las métricas recopiladas por Prometheus.</div> <br>

<div>
    <img  width="100%" src="https://github.com/JavierRamirezMoral/Kube-Magic/blob/main/Documentaci%C3%B3n%20Presentaci%C3%B3n/4.jpg">
</div>

