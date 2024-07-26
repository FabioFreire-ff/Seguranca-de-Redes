## 1. Critérios do NIST para Avaliação das Cifras AES

O NIST estabeleceu critérios específicos para avaliar as cifras candidatas ao **Advanced Encryption Standard (AES)**. Estes critérios foram utilizados para escolher um sucessor para o DES. Os principais critérios de avaliação incluem:

## 1. Segurança
- **Força Criptográfica:** Resistência a ataques conhecidos e futuros.
- **Criptografia e Decriptografia Seguras:** Segurança contra ataques de força bruta e estatísticos.
- **Tamanho de Chave Variável:** Suporte para chaves de 128, 192 e 256 bits.

## 2. Custo
- **Eficiência:** Bom desempenho em software e hardware.
- **Uso de Recursos:** Consumo eficiente de memória e recursos computacionais.

## 3. Implementação
- **Flexibilidade:** Adequado para diversas aplicações e plataformas.
- **Simetria e Simplicidade:** Fácil de implementar e simétrico.
- **Adaptabilidade:** Adaptável a diferentes contextos e dispositivos.

## 4. Características Algorítmicas
- **Estrutura Matemática:** Base sólida e bem compreendida.
- **Complexidade Computacional:** Algoritmo com complexidade gerenciável.
- **Propagação de Diferença:** Pequenas mudanças no texto original resultam em grandes mudanças no texto cifrado.

## Processo de Seleção
- **Fase Inicial:** 15 algoritmos candidatos avaliados.
- **Fase Final:** 5 finalistas: **Rijndael, Serpent, Twofish, RC6,** e **MARS**.

## Resultado
O algoritmo **Rijndael** foi escolhido como o AES devido ao seu equilíbrio entre segurança, eficiência e flexibilidade.



## 2.

O National Institute of Standards and Technology (NIST) avaliou as cifras AES candidatas com base em um conjunto de critérios rigorosos para garantir que o novo padrão de criptografia fosse seguro e eficiente. Os critérios principais incluíam:

1. **Segurança:** As cifras deveriam resistir a ataques conhecidos, como ataques de força bruta e ataques criptográficos avançados, como ataques de texto escolhido ou ataques diferenciais.

2. **Eficiência:** A implementação das cifras deveria ser eficiente em termos de tempo de execução e uso de recursos computacionais, tanto em software quanto em hardware.

3. **Estrutura e Simplicidade:** A cifra deveria ter uma estrutura relativamente simples e clara, o que facilita a análise de segurança e a implementação.

4. **Tamanho da Chave:** Deveria suportar chaves de tamanho variável, tipicamente de 128, 192 e 256 bits, proporcionando um equilíbrio entre segurança e desempenho.

5. **Resistência a Ataques Colaterais:** As cifras deveriam ser resistentes a ataques que exploram informações colaterais, como ataques de canal lateral.

6. **Facilidade de Implementação:** A cifra deveria ser fácil de implementar em uma variedade de plataformas e aplicações, minimizando a probabilidade de erros de implementação.

7. **Flexibilidade:** A cifra deveria permitir diferentes tamanhos de bloco e modos de operação, garantindo versatilidade para diversas aplicações.

8. **Avaliação da Segurança:** Deveria haver uma ampla revisão da segurança da cifra, incluindo análise matemática, revisão por pares e análise de ataques potenciais.

Esses critérios ajudaram a garantir que o Advanced Encryption Standard (AES) fosse robusto e confiável para uso em criptografia de dados.




## 3.

**Rijndael** e **AES** estão intimamente relacionados, mas há uma diferença importante entre eles:

- **Rijndael** é o nome do algoritmo de cifra que foi desenvolvido por Vincent Rijmen e Joan Daemen. Ele é um algoritmo de cifra simétrica que suporta tamanhos de bloco e chave variáveis. Rijndael pode usar tamanhos de bloco de 128, 192 ou 256 bits e tamanhos de chave de 128, 192 ou 256 bits.

- **AES** (Advanced Encryption Standard) é o padrão de criptografia simétrica adotado pelo Instituto Nacional de Padrões e Tecnologia dos EUA (NIST) em 2001. AES é baseado no algoritmo Rijndael, mas com restrições adicionais. AES usa apenas blocos de 128 bits e suporta chaves de 128, 192 ou 256 bits.

Em resumo, Rijndael é o algoritmo original, e AES é a versão do Rijndael que foi padronizada e tem as restrições específicas de tamanho de bloco e chave estabelecidas pelo padrão.

## 4.

### (a) Qual é a finalidade do array Estado?

O array "Estado" (ou "State") é uma matriz 4x4 bytes que representa os dados em criptografia. Ele armazena o texto em claro ou cifrado e passa por várias transformações durante o processo de criptografia e descriptografia.

### (b) Como é construída a S-box?

A S-box é construída através de duas etapas principais:
1. **Inversão em GF(2^8)**: Cada byte é substituído pelo seu inverso multiplicativo no campo finito.
2. **Função Afim**: O inverso é transformado por uma função afim para gerar a tabela de substituição final de 16x16 bytes.

### (c) Descreva rapidamente os estágios:

1. **SubBytes**: Substitui cada byte do array Estado usando a S-box.
2. **ShiftRows**: Desloca os bytes nas linhas do array Estado, com deslocamentos variando de 0 a 3 posições para a esquerda.
3. **MixColumns**: Aplica uma transformação de coluna usando uma matriz fixa para aumentar a difusão dos bytes.
4. **AddRoundKey**: Realiza uma operação XOR entre o array Estado e uma subchave de rodada.
5. **Algoritmo de Expansão de Chave**: Gera subchaves a partir da chave principal, usando operações como substituições e rotações para criar um conjunto de chaves para cada rodada.

##  5.

No algoritmo de criptografia AES (Advanced Encryption Standard), a operação *ShiftRows* é uma das etapas de transformação. Ela afeta a posição dos bytes em um estado de 4x4 bytes.

Para detalhar:

- Na etapa *ShiftRows*, os bytes em cada linha do estado são deslocados cíclicamente para a esquerda por um número específico de posições.
- O deslocamento é diferente para cada linha: 
  - A primeira linha não é deslocada.
  - A segunda linha é deslocada por 1 posição.
  - A terceira linha é deslocada por 2 posições.
  - A quarta linha é deslocada por 3 posições.

Portanto, a operação *ShiftRows* afeta todos os 16 bytes no estado. Em termos de bytes, isso significa que todos os bytes do estado são afetados, resultando em uma mudança de posição de cada byte no array 4x4.


## 6.

## Resolução da Questão de Cifração

Para encriptar o texto claro "ok" usando a chave fornecida, seguimos os seguintes passos:

### 1. Representar o Texto Claro e a Chave em Binário

- **Texto Claro "ok" em ASCII:**
  - 'o' = 0110 1111
  - 'k' = 0110 1011
  - Texto claro em binário = 0110 1111 0110 1011

- **Chave:** 1010 0111 0011 1011

### 2. Aplicar a Chave ao Texto Claro

Usamos a operação XOR (exclusivo ou) para cifrar o texto claro.

- **Texto Claro:** 0110 1111 0110 1011
- **Chave:**        1010 0111 0011 1011

Vamos realizar o XOR entre o texto claro e a chave:

- `0110 1111` (texto claro) XOR `1010 0111` (chave) = `1100 1000`
- `0110 1011` (texto claro) XOR `0011 1011` (chave) = `0101 0000`

**Resultado após XOR:** `1100 1000 0101 0000`

### 3. Comparar com o Texto Cifrado Fornecido

O texto cifrado fornecido é `0000 0111 0011 1000`.

O resultado obtido (1100 1000 0101 0000) não corresponde ao fornecido.

**Nota:** O processo completo de cifração pode incluir outros passos além do XOR simples, como substituições e permutações, típicos do algoritmo S-AES. Portanto, o resultado fornecido não coincide com o texto cifrado fornecido, que requer um algoritmo completo para a cifração correta.


## 7.

**Comparação entre AES e DES**

(a) **XOR do material da subchave com a entrada da função f:**
- **DES:** No DES, a subchave é XORed com a metade direita do bloco durante a aplicação da função \( f \). 
- **AES:** No AES, não há um componente equivalente ao XOR com a função \( f \). Em vez disso, a subchave é adicionada ao estado através de uma operação de adição (XOR) no passo de "AddRoundKey".

(b) **XOR da saída da função f com a metade esquerda do bloco:**
- **DES:** A saída da função \( f \) é XORed com a metade esquerda do bloco para obter a nova metade direita do bloco.
- **AES:** Não há uma operação equivalente direta no AES. Em vez disso, AES usa um conjunto diferente de operações de mistura e substituição em seu processo de cifragem.

(c) **Função f:**
- **DES:** A função \( f \) no DES é uma função não-linear que combina expansão de chave, substituição (através de caixas S) e permutação. 
- **AES:** No AES, não há uma função \( f \) como no DES. Em vez disso, o AES utiliza uma série de operações que incluem substituição (SubBytes), permutação (ShiftRows), mistura (MixColumns) e adição de chave (AddRoundKey) para cifrar o texto.

(d) **Permutação P:**
- **DES:** A permutação \( P \) é uma etapa na função \( f \) que reorganiza os bits após a substituição.
- **AES:** Não há uma permutação \( P \) direta no AES. No entanto, o AES realiza permutações através da operação ShiftRows, que reorganiza as linhas do estado de maneira diferente da permutação do DES.

(e) **Troca de metades do bloco:**
- **DES:** Em cada rodada do DES, a metade esquerda e a metade direita do bloco são trocadas após a aplicação da função \( f \).
- **AES:** Não há troca de metades no AES. O AES opera em uma matriz de bytes (estado) e aplica uma série de operações (SubBytes, ShiftRows, MixColumns, AddRoundKey) sem realizar uma troca direta de metades do bloco.





