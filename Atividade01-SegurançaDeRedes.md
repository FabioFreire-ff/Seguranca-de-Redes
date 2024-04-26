# Resposta - Atividade Cap. 01 - Introdução

**Aluno:** Fábio dos Santos Batalha Freire

## 1. O que é a arquitetura de segurança OSI?

A Arquitetura de Segurança OSI (Open Systems Interconnection) é um modelo conceitual que define as funções de segurança necessárias para proteger as comunicações em redes de computadores. Ela é baseada no modelo OSI, que é um modelo de referência para comunicações de rede que divide as funções de comunicação em sete camadas.

## 2. Qual é a diferença entre ameaças à segurança passivas e ativas?

Ameaças passivas são aquelas em que o atacante monitora ou obtém informações sem alterar ativamente os dados. Exemplos incluem interceptação de tráfego e análise de informações.

Ameaças ativas são aquelas em que o atacante interfere ativamente no sistema, modificando, destruindo ou criando dados. Exemplos incluem ataques de negação de serviço (DoS) e ataques de injeção de código.

## 3. Liste e defina resumidamente as categorias de ataques passivos e ativos à segurança.

### Ataques passivos:
- Vazamento de conteúdo de mensagem: Captura de informações sensíveis ou confidenciais durante a transmissão.
- Análise de tráfego: Observação do padrão de comunicação para extrair informações, mesmo que o conteúdo esteja encriptado.

### Ataques ativos:
- Disfarce: Uma entidade finge ser outra para obter acesso não autorizado.
- Repasse: Captura passiva de dados seguida pela sua retransmissão para efeitos não autorizados.
- Modificação de mensagens: Alteração, adiamento ou reordenação de partes de uma mensagem legítima.
- Negação de serviço: Impedimento ou inibição do uso normal das instalações de comunicação, podendo ter como alvo específico um destino ou toda uma rede.

## 4. Liste e defina resumidamente as categorias dos serviços de segurança.

### Autenticação: Certificação de que a entidade comunicante é quem afirma ser.
- Autenticação de Entidade Pareada: Garante a identidade das entidades conectadas em uma conexão lógica.
- Autenticação da Origem de Dados: Assegura que a fonte dos dados recebidos é conforme alegada.

### Controle de Acesso: Prevenção do uso não autorizado de recursos, determinando quem pode acessar, sob quais condições e o que é permitido.

### Confidencialidade dos Dados: a proteção dos dados contra divulgação não autorizada.
- Confidencialidade da Conexão: Protege todos os dados do usuário em uma conexão.
- Confidencialidade sem Conexão: Protege todos os dados do usuário em um único bloco de dados.
- Confidencialidade com Campo Seletivo: Mantém a confidencialidade de campos selecionados dentro dos dados do usuário.
- Confidencialidade do Fluxo de Tráfego: Protege as informações derivadas dos fluxos de tráfego.

### Integridade dos Dados: a certeza de que os dados recebidos são exatamente conforme enviados por uma entidade autorizada.
- Integridade da Conexão com Recuperação: Garante a integridade de todos os dados do usuário em uma conexão e permite recuperação em caso de modificação.
- Integridade da Conexão sem Recuperação: Detecta alterações na integridade dos dados sem tentativa de recuperação.
- Integridade da Conexão com Campo Seletivo: Assegura a integridade de campos selecionados nos dados do usuário.
- Integridade sem Conexão: Garante a integridade de um único bloco de dados sem conexão.
- Integridade sem Conexão com Campo Seletivo: Mantém a integridade de campos selecionados dentro de um único bloco de dados sem conexão.

### Irretratabilidade: oferece proteção contra negação, por parte de uma das entidades envolvidas em uma comunicação, de ter participado de toda ou parte dela. 
- Irretratabilidade, Origem: Prova de que a mensagem foi enviada pela parte especificada.
- Irretratabilidade, Destino: Prova de que a mensagem foi recebida pela parte especificada.

### Serviço de disponibilidade: Garante que um sistema ou recurso esteja acessível e utilizável sob demanda por uma entidade autorizada, de acordo com especificações de desempenho.

## 5. Liste e defina resumidamente as categorias dos mecanismos de segurança.

### Mecanismos de Segurança Específicos:

- Codificação: Utilização de algoritmos matemáticos para transformar dados em um formato não facilmente inteligível, dependendo de chaves de encriptação.
- Assinatura Digital: Anexa dados a uma unidade de dados ou sua transformação criptográfica, permitindo ao destinatário provar origem e integridade e protegê-la contra falsificação.
- Controle de Acesso: Mecanismos para impor direitos de acesso aos recursos.
- Integridade de Dados: Mecanismos para garantir a integridade de uma unidade de dados ou fluxo de unidades de dados.
- Troca de Autenticação: Garante a identidade de uma entidade por meio da troca de informações.
- Preenchimento de Tráfego: Inserção de bits nas lacunas de um fluxo de dados para dificultar análises de tráfego.
- Controle de Roteamento: Seleção de rotas fisicamente seguras para dados e mudanças de roteamento, especialmente em casos de suspeita de brechas de segurança.
- Notarização: Utilização de um terceiro confiável para garantir certas propriedades de uma troca de dados.

### Mecanismos de Segurança Difusos:

- Funcionalidade Confiada: Percepção de correção de acordo com critérios, como estabelecido por políticas de segurança.
- Rótulo de Segurança: Marcação associada a um recurso que designa seus atributos de segurança.
- Detecção de Evento: Identificação de eventos relevantes à segurança.
- Trilha de Auditoria de Segurança: Dados coletados para facilitar uma auditoria de segurança independente.
- Recuperação de Segurança: Lida com solicitações de mecanismos de tratamento e gerenciamento de eventos, tomando medidas de recuperação.

## 6. Requisitos de segurança para um caixa eletrônico (ATM)

### Confidencialidade:
- Requisito: Manter os dados pessoais do usuário, como número do cartão, PIN e informações de transações, confidenciais e protegidos contra acesso não autorizado.
- Importância: Extremamente alta. A violação da confidencialidade pode levar a fraudes financeiras, roubo de identidade e comprometimento da segurança dos clientes.

### Integridade:
- Requisito: Garantir que as transações financeiras dos usuários sejam registradas com precisão e não sejam alteradas após a conclusão, protegendo os dados contra adulteração.
- Importância: Muito alta. A integridade dos dados é crucial para garantir a precisão das transações e a confiança dos clientes no sistema. Qualquer alteração não autorizada pode resultar em perda financeira ou disputas.

### Disponibilidade:
- Requisito: Assegurar que o sistema esteja disponível para os usuários realizar transações a qualquer momento, dentro das limitações operacionais normais.
- Importância: Alta. A indisponibilidade do sistema pode causar frustração aos usuários, impactar negativamente a reputação do banco e resultar em perda de negócios. Os ATMs são frequentemente utilizados em situações de emergência, tornando a disponibilidade ainda mais crítica.


### 7. Para responder as letras abaixo, por favor, consulte o livro-texto da disciplina:

(a) Desenhe uma matriz similar ao Quadro 1.4 que mostre o relacionamento entre serviços de segurança e ataques.

| Serviço/Ataque                              | Ataque Passivo | Ataque Ativo: Disfarce | Ataque Ativo: Repasse | Ataque Ativo: Modificação das Mensagens  | Ataque Ativo: Negação de Serviço | 
|---------------------------------------------|----------------|------------------------|-----------------------|------------------------------------------|----------------------------------|
| Autenticação                                | X              | X                      | X                     | X                                        |                                  |              
| Controle de Acesso                          |                | X                      | X                     | X                                        |                                  |              
| Confidencialidade                           | X              |                        |                       |                                          |                                  |              
| Integridade                                 |                |                        |                       | X                                        |                                  |              
| Irretratabilidade                           |                |                        |                       |                                          | X                                |              
| Disponibilidade                             |                |                        |                       |                                          | X                                |              

(b) Desenhe uma matriz similar ao Quadro 1.4 que mostre o relacionamento entre mecanismos de segurança e ataques.

| Mecanismo/Ataque                            | Ataque Passivo | Ataque Ativo: Disfarce | Ataque Ativo: Repasse | Ataque Ativo: Modificação das Mensagens | Ataque Ativo: Negação de Serviço |
|---------------------------------------------|----------------|------------------------|-----------------------|------------------------------------------|----------------------------------|
| Codificação                                 |                |                        |                       | X                                        |                                  |
| Assinatura digital                          |                |                        |                       | X                                        |                                  |
| Controle de acesso                          |                | X                      | X                     |                                          |                                  |
| Integridade dos dados                       |                |                        |                       | X                                        |                                  |
| Troca de autenticação                       |                | X                      |                       |                                          |                                  |
| Preenchimento de tráfego                    |                |                        |                       |                                          | X                                |
| Controle de Roteamento                      |                |                        |                       |                                          | X                                |
| Notarização                                 |                |                        |                       |                                          | X                                |
