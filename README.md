# Gateway

API Gateway é um padrão arquitetural que consiste um único ponto de entrada central para todas as solicitações de API. 
O API Gateway atua como um proxy reverso que encaminha solicitações de clientes para os serviços apropriados nos 
bastidores.

Quando estamos trabalhando com arquitetura de microsserviço, o ideal é ter um ponto centralizado para as entradas de 
requisições na nossa aplicação através de uma aplicação web, mobile ou requisições pelo Postman.

Para fazer isso, adicionaremos um API gateway. Vamos usar o Spring Cloud Gateway, na versão 3.1.4, a mesma do 
Eureka Client, sendo a versão do Spring Cloud de forma geral.

Com isso, ele consegue identificar as rotas e fornecer esse ponto único, tendo integração com o Discovery Service e com 
outros aplicativos do Spring.

### Para iniciar o serviço de api gateway, seguir os seguintes passos:
1) Adicionar a dependência do Gateway - Spring Cloud Routing e Eureka Discovery Client - Spring Cloud Discovery ao seu 
arquivo pom.xml.
2) Configurar o arquivo `application.properties` com as informações de configuração do gateway:
* A porta do servidor do gateway será definido como 8082.
`server.port=8082`
* Definir o nome da aplicação
`spring.application.name=gateway`
* A primeira configuração é utilizada para ativar a descoberta de serviços do Spring Cloud Gateway e a segunda define
o nome das aplicaçoes sejam em letras minusculas.
`spring.cloud.gateway.discovery.locator.enabled=true`
`spring.cloud.gateway.discovery.locator.lowerCaseServiceId=true`
* Esta configuração é usada para definir a URL do servidor Eureka. O cliente Eureka usará essa URL para se conectar ao 
servidor Eureka e registrar ou descobrir serviços.
`eureka.client.serviceUrl.defaultZone=http://localhost:8081/eureka`
3) Anotar a classe principal da sua aplicação com a anotação `@EnableEurekaClient`
4) Acessar a página http://localhost:8081 no navegador para verificar se o servidor Eureka está em execução. 
Você deve ver a interface do usuário do Eureka, que mostra informações sobre os serviços registrados e as instâncias

### Documentação de referência

* [Using Spring Cloud Gateway](https://github.com/spring-cloud-samples/spring-cloud-gateway-sample)
* [Service Registration and Discovery with Eureka and Spring Cloud](https://spring.io/guides/gs/service-registration-and-discovery/)

