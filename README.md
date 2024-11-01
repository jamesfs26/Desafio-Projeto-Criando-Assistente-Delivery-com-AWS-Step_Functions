 # Desafio de Projeto 2: 📲🚴🏼 Criando um Assistente de Delivery 🚚
 
 ## 📔📲🚴🏼 Resumo do Desafio: Criando um Assistente de Delivery

O assistente de delivery deve responder a perguntas comuns, como status de pedido, recomendações de jantar, como cancelar pedidos, entre outras. Cada cliente fictício tem um paladar e preferências diferentes, e o assistente oferece respostas adequadas para resolver o problema ou dúvida rapidamente.

**Código:**

{
  "Version": "2024-10-14",
  "StartAt": "AtendimentoCliente",
  "States": {
    "AtendimentoCliente": {
      "Type": "Choice",
      "Choices": [
        {
          "Variable": "$.pergunta",
          "StringEquals": "Qual o status do meu pedido?",
          "Next": "StatusPedido"
        },
        {
          "Variable": "$.pergunta",
          "StringEquals": "Como faço para cancelar meu pedido?",
          "Next": "CancelarPedido"
        },
        {
          "Variable": "$.pergunta",
          "StringEquals": "O que você recomenda para o jantar?",
          "Next": "RecomendacaoJantar"
        },
        {
          "Variable": "$.pergunta",
          "StringEquals": "Como aplico um cupom de desconto?",
          "Next": "AplicarCupom"
        },
        {
          "Variable": "$.pergunta",
          "StringEquals": "Meu pedido está atrasado. O que posso fazer?",
          "Next": "PedidoAtrasado"
        }
      ],
      "Default": "PerguntaNaoEncontrada"
    },
    "StatusPedido": {
      "Type": "Task",
      "Resource": "VerificarStatusDoPedido",
      "End": true
    },
    "CancelarPedido": {
      "Type": "Task",
      "Resource": "CancelarPedido",
      "End": true
    },
    "RecomendacaoJantar": {
      "Type": "Task",
      "Resource": "RecomendarRestaurante",
      "End": true
    },
    "AplicarCupom": {
      "Type": "Task",
      "Resource": "AplicarCupomDeDesconto",
      "End": true
    },
    "PedidoAtrasado": {
      "Type": "Task",
      "Resource": "AjudarComPedidoAtrasado",
      "End": true
    },
    "PerguntaNaoEncontrada": {
      "Type": "Fail",
      "Error": "PerguntaNaoEncontrada",
      "Cause": "A pergunta feita não está cadastrada no sistema."
    }
  }
}

## **Informações dos Clientes 👤 e Respostas do Assistente:** 💬🤖

* **Nome:** Ana Clara Souza **Idade:** 25 anos **Sexo:** Feminino **Preferência de paladar:** Vegetariana **Pergunta:** "O que você recomenda para o jantar?" **Resposta:** "Ana, que tal experimentar o restaurante Green Garden? Eles oferecem opções deliciosas de saladas e pratos vegetarianos, como o 'Risoto de Cogumelos'. Uma ótima escolha para um jantar leve e saudável!"

* **Nome:** João Marcos Silva **Idade:** 30 anos **Sexo:** Masculino **Preferência de paladar:** Comida apimentada **Pergunta:** "Qual o status do meu pedido?" **Resposta:** "João, seu pedido está a caminho! O entregador chegará em aproximadamente 15 minutos com o seu 'Tacos Mexicanos Apimentados'. Fique de olho no mapa de rastreamento!"

* **Nome:** Pedro Alencar **Idade:** 40 anos **Sexo:** Masculino **Preferência de paladar:** Comida italiana **Pergunta:** "Meu pedido está atrasado. O que posso fazer?" **Resposta:** "Pedro, verificamos que seu pedido está com 10 minutos de atraso. Estamos entrando em contato com o restaurante para obter mais informações e garantir que o entregador chegue o quanto antes. Agradecemos sua paciência!"

* **Nome:** Fernanda Costa **Idade:** 22 anos **Sexo:** Feminino **Preferência de paladar:** Sobremesas e doces **Pergunta:** "Como aplico um cupom de desconto?" **Resposta:** "Fernanda, para aplicar o seu cupom, vá até o carrinho de compras e insira o código no campo 'Adicionar Cupom'. Não se esqueça de verificar a validade do cupom e o valor mínimo de compra!"

* **Nome:** Carlos Mendes **Idade:** 35 **Sexo:** Masculino **Preferência de paladar:** Comida brasileira **Pergunta:** "Como faço para cancelar meu pedido?" **Resposta:** "Carlos, você pode cancelar o pedido acessando a aba 'Meus Pedidos' e selecionando o botão 'Cancelar Pedido'. Caso o pedido já tenha sido confirmado pelo restaurante, entre em contato com o suporte para verificar a possibilidade de cancelamento."
 
 ### 👷📋 **Uso de Engenharia de Prompt neste desafio de Projeto!**

O intuito do Prompt neste projeto foi criar uma **simulação de um ciclo 🔄 de atendimento em um aplicativo 📲 de entrega 🚚 de refeições online**, o recorte foi feito com 5 pessoas ficticias aleatórias com idades entre 20-50 anos de ambos os sexos.

* 📋 **Prompt Usado:** *Crie uma orquestração de workflows referente a um Projeto de um Assistente de Delivery! Crie perguntas pertinentes que um cliente faria em um aplicativo (Ifood etc.) e gere respostas efetivas que solucione o problema do cliente. Crie 5 clientes fictícios de forma aleatória dos sexos, com paladares diferentes.*

 ### O que é o AWS Step Functions? ➡️⬆️⬅️⬇️🔄

O AWS Step Functions é um serviço de orquestração de workflows que ajuda a criar, executar e monitorar **fluxos de trabalho** automatizados, facilitando a coordenação de múltiplos serviços da AWS e sistemas distribuídos. Ele permite definir fluxos de trabalho com etapas bem delineadas e estados controlados, sendo **ideal para a automação de processos complexos**.

O AWS Step Functions foi **lançado pela Amazon** Web Services **em 2016** para ajudar desenvolvedores a criar fluxos de trabalho robustos e escaláveis sem a necessidade de gerenciar manualmente a infraestrutura subjacente. A ideia central do serviço é **fornecer um ambiente para definir a lógica de processos de negócios e fluxos de dados complexos através de uma abordagem de "State Machine" (máquina de estados)**. Esse serviço foi desenvolvido para facilitar a criação de aplicações distribuídas, quebrando grandes processos em etapas discretas e automatizadas.

**O AWS Step Functions é usado principalmente para:**
* **Orquestração de serviços:** Permite que diferentes serviços da AWS trabalhem juntos de forma coordenada, como **Lambda**, **S3**, **DynamoDB**, **ECS**, entre outros.

* **Automação de workflows:** Automatiza processos complexos que envolvem múltiplas etapas, como **pipelines de dados**, **workflows em machine learning**, e **processamento de eventos**.

* **Divisão de processos:** Permite dividir aplicações monolíticas em fluxos de trabalho modulares e reutilizáveis.

* **Controle de estados:** Cada tarefa dentro de um workflow pode ser configurada para executar de acordo com condições específicas, permitindo gerenciar processos de longa duração, reexecuções e erros.

A linguagem do Step Functions é um tipo de **linguagem de definição de estados** chamada _Amazon States Language_ (**ASL**), que **permite descrever de forma declarativa o fluxo de trabalho que será executado**. Essa linguagem **é baseada em JSON** e é usada para definir o comportamento do workflow, incluindo estados, transições, manipulação de erros, e muito mais.

A ASL define como os passos do workflow são coordenados e executados. Nessa linguagem, você descreve uma série de estados e transições entre eles, além de condicionar como cada estado pode ser acionado ou repetido.

**Cada estado pode ser de um tipo específico, como:**

* **Task:** Executa uma tarefa, como uma função Lambda, ou invoca outro serviço da AWS.
* **Choice:** Implementa lógica condicional (if/else), permitindo que o fluxo tome diferentes caminhos.
* **Parallel:** Permite a execução de tarefas em paralelo.
* **Wait:** Introduz um atraso temporário.
* **Map:** Executa um conjunto de operações em cada item de uma lista.
* **Fail:** Termina o workflow em caso de erro.
* **Succeed:** Finaliza o workflow com sucesso.

**Exemplo Simples de ASL (em JSON):**

{
  "Comment": "Exemplo simples de um workflow do Step Functions",
  "StartAt": "PrimeiraTarefa",
  "States": {
    "PrimeiraTarefa": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGION:ACCOUNT_ID:function:PrimeiraFuncao",
      "Next": "SegundaTarefa"
    },
    "SegundaTarefa": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGION:ACCOUNT_ID:function:SegundaFuncao",
      "End": true
    }
  }
}

### Como funciona o Workflow Studio: 🏢🎨

O Workflow Studio é a **interface low-code e visual do AWS Step Functions**, onde os usuários podem **desenhar seus fluxos de trabalho de maneira intuitiva**, **arrastando e soltando componentes, sem necessariamente escrever o código JSON** da Amazon States Language **manualmente**. O Workflow Studio simplifica a construção de workflows, especialmente para usuários que não têm experiência com codificação.

**Principais Funcionalidades do Workflow Studio:**
* **Editor Visual:** Permite a construção de workflows arrastando componentes como tarefas, estados de decisão (Choice), ciclos (Map), entre outros.

* **Ajustes no JSON:** Apesar de ser uma ferramenta visual, o Workflow Studio ainda permite que você veja e edite o código JSON gerado em tempo real, permitindo ajustes manuais avançados, se necessário.

* **Templates e Exemplos:** O Workflow Studio fornece vários templates prontos para tarefas comuns (ex: processamento de imagens com Lambda, pipeline de dados com S3 e Glue), facilitando a criação de workflows sem a necessidade de partir do zero.

* **Simulação e Depuração:** Ele permite simular a execução do fluxo de trabalho antes de implantá-lo, facilitando o ajuste fino e a detecção de erros antes de entrar em produção.

### 👷📋 Uso de Engenharia de Prompt neste desafio de Projeto!

Como este é um projeto ligado a um curso sobre **Engenharia de Prompt e Claude 3**, eles naturalmente devem ser utilizados nesta etapa de finalização. Para o prompt foi usado o modelo Claude 3 Haiku da Antrhopic. Por questões de permissão e disponibilidade regional, não são todos os modelos do Bedrock que estão disponiveis a todos os usuários (ex: Amazon Titan), de maneira que ao escolher o modelo a ser usado, deve-se verificar quais estão disponiveis ao seu perfil, e deve ser dada as devidas permissões para uso de algum novo modelo desenvolvido pelo Bedrock.

**Pré-Requisitos para usar os modelos no Step Functions:**

* Configuração de Permissão do Usuário (IAM);
* Verificação de restrições de disponibilidade regional do modelo;
* Inserir o Prompt seguindo as epecificações do JSON.


## 👔💬💻 **Meus Comentarios:**

O uso do Amazon Step Functions **é básicamente um Fluxograma de Programação Interativo com uso de Inteligência Artificial**.

No modelo de **Hello World** escolhido pelo Professor Felipão para apresentação do uso do Step Functions, foi usada básicamente a mesma estrutura encontrada na criação de um fluxograma de Lógica de Programação, com o acréscimo de caixas interativas de código (JSON), o próprio Felipão foi quem me ensinou sobre lógica de Programação e Fluxograma no curso patrocinado pelo Ifood (Ifood - Programação do Zero) o curso era focado em Lógica de Programação e tinha como linguagem de programação o JavaScript, do qual é derivado o JSON, logo há muitas semelhanças na estrutura de código usado no Step Functions, portanto, este desafio de projeto foi para mim uma volta ao inicio dos meus primeiros passos.

O Step Functions pode ser usado em grande escala para criar fluxos de trabalho, já que permite a integração com vários serviços AWS, o uso de serviços de IA potêncializam em larga escala as possibilidades de criação nesta ferramenta.

Essa combinação é uma poderosa aliada para desenvolvedores de software, e por ser uma plataforma low-code permite que muitos profissionais de diversas áreas desenvolvam projetos, aplicações e serviços com ela.

Cada **caixa interativa** adicionada gera um estado (os tipos de estados estão listados acima), esse estado contém um bloco de código (JSON), eles podem ser alteradas para diversos fins ou outras funções de serviços podem ser adicionadas (ex: Bedrock, Lambda, S3 etc.).

Foi uma boa expêriencia fazer este Desafio de Projeto! Entretanto tenho muitas reclamações a respeito da Amazon (do qual sou cliente do ecommerce há muitos anos) em especial a AWS, eu deveria ter concluido esse curso 2 semanas, após ter iniciado (17 de Setembro) entretanto, só agora consegui resolver, devido a um problema de autenticação de segurança da plataforma, que não reconhecia minha documentação bancaria, sendo que é a mesma que utilizo em outras plataformas concorrentes, como Azure, e Google Cloud (ao qual nunca tive problema).

Devido a ter ficado quase 30 dias com este problema, tive um atraso significativo neste curso. Com isso, a AWS caiu muito aos meus olhos, e ficará em terceiro plano como opção de Cloud.
