# Food Microservice

Este projeto consiste em uma aplicação de microserviços chamada Food Microservice. A aplicação é construída em Java utilizando Spring Boot, MySQL e RabbitMQ, e é composta por cinco serviços: Pedido, Pagamento, Eureka, Gateway e Avaliação.

## Serviços

### Pedido
O serviço de Pedido é responsável por gerenciar os pedidos dos clientes. Ele permite as seguintes operações:

- Adicionar um novo pedido
- Ler detalhes de um pedido
- Deletar um pedido

Quando um pedido é concluído, uma mensagem é enviada pelo RabbitMQ para o serviço de Pagamento.

### Produto
O serviço de Produto é responsável por gerenciar o cadastro e a organização dos produtos disponíveis na loja. Ele permite as seguintes operações:

- Adicionar um novo produto
- Atualizar os detalhes de um produto existente
- Consultar as informações de um produto
- Remover um produto
Cada produto pode ser cadastrado com múltiplas categorias, valor e quantidade disponível. Isso permite uma gestão mais flexível e detalhada do inventário da loja.

### Pagamento
O serviço de Pagamento é responsável por processar os pagamentos dos pedidos. Ele recebe mensagens do serviço de Pedido via RabbitMQ e, em caso de pagamento bem-sucedido, reenvia uma confirmação ao serviço de Pedido e ao serviço de Avaliação.

### Avaliação
O serviço de Avaliação permite que os clientes avaliem os pedidos após o pagamento. Quando o pagamento é confirmado, uma mensagem é enviada ao serviço de Avaliação via RabbitMQ, que então cria uma nova avaliação.

### Eureka
Eureka é o serviço de descoberta utilizado para registrar e localizar os serviços da aplicação, permitindo que os serviços se comuniquem entre si de maneira eficiente.

### Gateway
O Gateway é responsável por rotear as requisições para os serviços apropriados, agindo como um ponto de entrada único para a aplicação.

## Tecnologias Utilizadas

- Java
- Spring Boot
- MySQL
- RabbitMQ
- Eureka (Spring Cloud Netflix)
- Spring Cloud Gateway

## Como Rodar o Projeto

Para rodar o projeto, siga os passos abaixo:

Clone o repositório do docker-compose no GitHub:
```sh
git clone https://github.com/Tessaro03/docker-compose-food.git
```

Navegue até o diretório do projeto clonado:
```sh
cd Docker-Compose-food-microservice
```

Execute o comando para subir os serviços utilizando Docker Compose:
```sh
docker-compose up
```

Isso irá baixar as imagens necessárias, criar e iniciar os contêineres definidos no arquivo docker-compose.yml.

## Futuras Atualizações

- Adicionar o serviço de Usuário
