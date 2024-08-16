
## 1  O que é Encriptação Tripla?

A encriptação tripla, ou *Triple DES* (Triple Data Encryption Standard), é um método de criptografia que aplica o algoritmo DES (Data Encryption Standard) três vezes a cada bloco de dados. Isso aumenta a segurança em relação ao DES simples, que, apesar de ter sido bastante utilizado, é considerado vulnerável por conta do avanço na capacidade de processamento dos computadores.

O processo de encriptação tripla geralmente segue estes passos:

1. **Encriptação**: O bloco de dados é encriptado com uma chave DES.
2. **Decriptação**: O resultado da primeira etapa é então decriptado usando uma segunda chave DES.
3. **Encriptação novamente**: Finalmente, o bloco é encriptado uma terceira vez com uma terceira chave DES.

Isso proporciona uma segurança muito maior em comparação ao DES único, reduzindo a possibilidade de ataques de força bruta. A chave utilizada no Triple DES pode ter 56, 112 ou 168 bits de comprimento, dependendo de como as chaves são geradas e utilizadas.

## 2 O que é ataque meet-in-the-middle?

O ataque meet-in-the-middle é um tipo de ataque criptográfico usado para reduzir a complexidade de certos algoritmos de criptografia. Ele é mais comum em cenários de criptografia de bloco, como o algoritmo DES (Data Encryption Standard), e funciona da seguinte maneira:

### Descrição do Ataque

O ataque meet-in-the-middle é uma técnica de força bruta que é usada para quebrar criptografia com uma chave de comprimento intermediário. Em vez de tentar todas as possíveis chaves de uma vez (o que seria uma abordagem de força bruta completa), o ataque divide o problema em duas partes menores.

### Funcionamento

1. **Divisão do Espaço de Chaves**: O atacante divide o espaço de chaves em duas metades e realiza uma busca para cada metade de forma independente.
   
2. **Criptografia e Armazenamento**:
   - O atacante criptografa todas as possíveis entradas para a primeira metade da chave e armazena os resultados.
   
3. **Descriptografia e Comparação**:
   - Em seguida, o atacante descriptografa todas as possíveis saídas para a segunda metade da chave e verifica se algum dos resultados descriptografados corresponde a um dos resultados criptografados armazenados anteriormente.
   - Se houver uma correspondência, o atacante encontrou uma chave que pode ter sido usada para criptografar a mensagem.


## 3 Quantas chaves são usadas na encriptação tripla?

Na encriptação tripla (Triple DES ou 3DES), são usadas três chaves. Isso significa que o algoritmo aplica o DES (Data Encryption Standard) três vezes para cada bloco de dados, com três chaves distintas, o que aumenta significativamente a segurança em comparação ao DES simples.

## 4 Por que a parte do meio do 3DES é decriptação, em vez de encriptação?

O 3DES (Triple Data Encryption Standard) é uma evolução do DES (Data Encryption Standard) que visa aumentar a segurança ao aplicar o algoritmo DES três vezes a cada bloco de dados. A razão pela qual a parte do meio do 3DES é decriptação (e não encriptação) está ligada à forma como a criptografia e a descriptografia são combinadas para alcançar a segurança desejada.

O 3DES utiliza três chaves diferentes, geralmente denominadas K1, K2 e K3. O processo é o seguinte:

1. **Encriptação com K1**: O dado é inicialmente encriptado com a primeira chave K1 usando o DES.
2. **Decriptação com K2**: O dado resultante da primeira encriptação é então decriptado com a segunda chave K2 usando o DES. Essa etapa é a que se refere a "decriptação" no meio do processo.
3. **Encriptação com K3**: Finalmente, o dado resultante da segunda etapa é novamente encriptado com a terceira chave K3 usando o DES.

A razão pela qual a etapa do meio é decriptação é que o DES é um algoritmo de cifra de bloco simétrico que opera de forma reversível. Ao usar a decriptação no meio, o 3DES pode, de fato, alcançar um aumento significativo na segurança em comparação com o uso de uma única aplicação do DES.

Esse esquema de encriptação-decriptação-encriptação (EDE) garante que a criptografia final ofereça uma proteção muito mais robusta do que uma simples aplicação do DES, sem introduzir vulnerabilidades que poderiam surgir se a mesma operação fosse repetida três vezes consecutivas.

## 5 Por que alguns modos de operação de cifra de bloco só utilizam a encriptação, enquanto outros empregam encriptação e decriptação?

A razão para alguns modos de operação de cifra de bloco utilizarem apenas encriptação enquanto outros utilizam tanto encriptação quanto decriptação está relacionada à forma como eles manipulam e transformam os blocos de dados para garantir a segurança e a integridade.

### Modos que utilizam apenas encriptação (como o ECB - Electronic Codebook):

- **Simples e Rápido:** Esses modos são simples de implementar e rápidos, mas oferecem menos segurança. No modo ECB, cada bloco de texto plano é encriptado de forma independente. Isso pode ser problemático porque blocos idênticos de texto plano serão criptografados para blocos idênticos de texto cifrado, o que pode revelar padrões no texto cifrado e facilitar a análise de criptografia.

### Modos que utilizam tanto encriptação quanto decriptação (como o CBC - Cipher Block Chaining e o CFB - Cipher Feedback):

- **Segurança Adicional:** Estes modos fornecem maior segurança ao introduzir uma forma de dependência entre os blocos. Por exemplo, no modo CBC, o texto cifrado de um bloco é usado como parte da operação de encriptação do próximo bloco, criando uma cadeia de blocos cifrados. Isso ajuda a evitar a repetição de padrões e torna mais difícil para um atacante deduzir qualquer informação sobre o texto cifrado.
  
- **Integração com Operações de Decodificação:** Em alguns modos, a decriptação também é necessária para garantir a integridade dos dados ou para aplicar certas operações que precisam ser feitas em ambos os lados (encriptação e decriptação) para manter a confidencialidade e integridade dos dados. Esses modos ajudam a garantir que quaisquer alterações ou corrupções em um bloco sejam propagadas para os blocos subsequentes, melhorando a segurança geral.

Em resumo, os modos de operação que utilizam apenas encriptação são mais simples e rápidos, mas menos seguros, enquanto os modos que utilizam tanto encriptação quanto decriptação oferecem uma camada adicional de segurança ao introduzir dependências e garantir a integridade dos dados criptografados.

## 6 Você deseja construir um dispositivo de hardware para realizar encriptação de bloco no modo cipher block chaining (CBC) usando um algoritmo mais forte do que DES. 3DES é um bom candidato. A Figura 1 mostra duas possibilidades, ambas acompanhando a definição do CBC.
Qual das duas você escolheria:
(a) Por segurança?
(b) Por desempenho?

### (a) Por Segurança:

CBC com 3 loops pois oferece uma maior segurança.

### (b) Por Desempenho:

CBC com um loop pois oferece uma maior rapidez no tempo.
