# DDD - Domain-Driven Design
O DDD (Domain-Driven Design) é uma abordagem ao desenvolvimento de software que foca na modelagem do domínio de negócios central e na tradução desse modelo em código. Quando aplicamos DDD em uma aplicação Node.js, a estrutura de pastas reflete as camadas e os componentes do domínio, separando bem as responsabilidades.

<img src="./ddd-structure.png" />


## Descrição das Pastas:
/src: Diretório raiz que contém todo o código-fonte da aplicação. <br/>
/application: Esta camada contém a lógica de aplicação, ou seja, o que a aplicação faz. Não deve conter regras de negócio, apenas orquestra a execução dos casos de uso. <br/>
/use-cases: Casos de uso que descrevem as ações que a aplicação pode realizar, como criar, atualizar ou completar uma tarefa. <br/>
/dto: Objetos de transferência de dados (Data Transfer Objects) que servem para transportar dados entre diferentes partes da aplicação. <br/>
/interfaces: Definições de interfaces, como repositórios e serviços, que os casos de uso irão consumir. <br/>
/domain: Representa o domínio de negócio central e é a parte mais importante do DDD. <br/>
/entities: Entidades do domínio, como Task, que representam objetos do mundo real ou conceitos de negócio. <br/>
/repositories: Interfaces que definem como os dados devem ser persistidos ou recuperados, independentemente de qual banco de dados é usado. <br/>
/services: Serviços de domínio que contêm lógica de negócio que não se encaixa perfeitamente em uma entidade. <br/>
/infrastructure: Contém a infraestrutura que a aplicação necessita para funcionar, como persistência de dados, comunicação com outras APIs, etc. <br/>
/persistence: Implementações específicas dos repositórios para diferentes bancos de dados, como MongoDB, PostgreSQL ou armazenamento em memória. <br/>
/config: Configurações específicas da infraestrutura, como conexões de banco de dados.<br/>
/http: Camada que lida com a comunicação HTTP, incluindo controladores que processam as requisições e rotas que mapeiam essas requisições para os controladores.<br/>
/log: Serviço para gerenciamento de logs da aplicação.<br/>
/shared: Contém código e utilitários compartilhados entre diferentes partes da aplicação.<br/>
/kernel: Contém classes e funções essenciais para a aplicação, como tratamento de erros (AppError) e padronização de resultados (Result).<br/>
/utils: Funções utilitárias que podem ser usadas em todo o projeto, como formatadores de data, geradores de UUID, etc.<br/>

## Fluxo de Trabalho
O usuário envia uma requisição para criar uma tarefa. Essa requisição chega ao Controller na camada /infrastructure/http/controllers.<br/>
O Controller chama um caso de uso específico da camada /application/use-cases.<br/>
O caso de uso utiliza serviços de domínio e repositórios da camada /domain para executar a lógica de negócios e manipular as entidades.<br/>
O caso de uso também pode chamar repositórios específicos da camada /infrastructure/persistence para persistir dados no banco de dados.<br/>
Finalmente, a resposta é enviada de volta ao usuário via Controller.<br/>
Essa estrutura promove uma separação clara de responsabilidades, facilita testes unitários e torna a aplicação mais escalável e mantível.<br/>
