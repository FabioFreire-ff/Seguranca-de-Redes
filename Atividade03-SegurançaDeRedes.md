# Questionário de Segurança de Redes

## 1. Responda os questionamentos a seguir:

### (a) Por que é importante estudar a cifra de Feistel?
A cifra de Feistel é importante porque serve como base para muitos algoritmos de criptografia simétrica amplamente utilizados, como o DES (Data Encryption Standard) e o AES (Advanced Encryption Standard). A estrutura de Feistel permite a criação de algoritmos robustos e seguros, e o estudo dessa cifra ajuda a entender como dividir a tarefa de encriptação em várias rodadas para melhorar a segurança.

### (b) Qual é a diferença entre uma cifra de bloco e uma cifra de fluxo?
- **Cifra de Bloco:** Processa o texto em blocos de tamanho fixo (por exemplo, 64 ou 128 bits) de uma vez. Cada bloco é encriptado ou decriptado independentemente usando uma chave secreta.
- **Cifra de Fluxo:** Encripta o texto um bit ou byte de cada vez, gerando um fluxo de chaves pseudo-aleatórias que são combinadas com o texto claro.

### (c) Por que não é prático usar uma cifra de substituição reversível qualquer do tipo mostrado na Tabela 3.1?
Uma cifra de substituição reversível simples é vulnerável a ataques de análise de frequência, onde um atacante pode analisar a frequência de letras ou padrões de texto cifrado para deduzir a chave ou o texto claro. Além disso, a criação e armazenamento de uma tabela de substituição grande podem ser impraticáveis.

### (d) O que é uma cifra de produto?
Uma cifra de produto é uma combinação de duas ou mais cifras simples aplicadas em sequência para criar uma cifra mais complexa e segura. Por exemplo, a combinação de substituição e transposição para aumentar a segurança.

### (e) Qual é a diferença entre difusão e confusão?
- **Difusão:** A difusão espalha a estrutura do texto claro ao longo do texto cifrado, de forma que cada parte do texto cifrado depende de várias partes do texto claro.
- **Confusão:** A confusão visa a tornar a relação entre a chave de cifragem e o texto cifrado o mais complexa possível.

### (f) Que parâmetros e escolhas de projeto determinam o algoritmo real de uma cifra de Feistel?
Os parâmetros incluem o tamanho do bloco, o número de rodadas, a chave de encriptação, a função de rodada, e o esquema de geração de sub-chaves. As escolhas de projeto determinam a segurança e eficiência do algoritmo.

### (g) Explique o efeito avalanche.
O efeito avalanche refere-se ao fenômeno onde uma pequena alteração no texto claro ou na chave de encriptação resulta em uma mudança significativa no texto cifrado. Isso é desejável em algoritmos de cifragem, pois aumenta a segurança contra ataques.

## 2. Qual(is) dos recursos abaixo estão presentes no projeto da rede de Feistel? Explique.

### (a) Tamanho do bloco e da chave;
### (b) Função da rodada;
### (c) Gerador de sub-chaves;
### (d) Todas as alternativas.

**Resposta:** (d) Todas as alternativas.
Todos esses recursos são fundamentais no projeto de uma rede de Feistel. O tamanho do bloco e da chave, a função de rodada, e o gerador de sub-chaves são elementos essenciais que determinam a segurança e funcionamento do algoritmo.

## 3. Qual é o tamanho do texto claro no Data Encryption Standard (DES)? Explique.

### (a) 57;
### (b) 48;
### (c) 32;
### (d) 64.

**Resposta:** (d) 64.
O DES trabalha com blocos de 64 bits, ou seja, o tamanho do texto claro que ele processa por vez é de 64 bits.

## 4. A cifra de Feistel do algoritmo de encriptação utilizada no Data Encryption Standard (DES) utiliza quantos S-boxes? Explique.

### (a) 8;
### (b) 7;
### (c) 6;
### (d) 5.

**Resposta:** (a) 8.
O DES utiliza 8 S-boxes (Substitution boxes) durante o processo de encriptação em cada rodada para realizar substituições complexas que aumentam a segurança do algoritmo.

## 5. O Data Encryption Standard possui uma chave de 56 bits, o que torna possível um espaço de 2^56 chaves possíveis. Essa sentença trata de ataque de. . . Explique.

### (a) Tempo;
### (b) Matemático;
### (c) Força-Bruta;
### (d) DoS.

**Resposta:** (c) Força-Bruta.
O ataque de força-bruta envolve tentar todas as combinações possíveis de chaves até encontrar a correta. Com uma chave de 56 bits, isso significa tentar até 2^56 chaves possíveis.

## 6. Demonstre, através de um exemplo, como realizar a cifragem de 16 bits (dois caracteres), em 2 rounds, em seguida, decifre o texto cifrado. Explique o processo passo a passo. Forneça um código Python/Sagemath com sua solução.

Aqui está um exemplo de como cifrar e decifrar um texto usando uma cifra de Feistel em Python.

```python
def cifrar(texto_claro, chave):
    # Função para cifrar o texto claro em 2 rounds
    bloco = int.from_bytes(texto_claro.encode(), byteorder='big')
    chave_int = int.from_bytes(chave.encode(), byteorder='big')
    
    # Round 1
    bloco_cifrado = bloco ^ chave_int
    
    # Round 2
    bloco_cifrado = bloco_cifrado ^ chave_int
    
    # Retornar o texto cifrado como um número inteiro
    return bloco_cifrado

def decifrar(texto_cifrado, chave):
    # Função para decifrar o texto cifrado
    chave_int = int.from_bytes(chave.encode(), byteorder='big')
    
    # Round 2 (decifragem reversa)
    bloco_decifrado = texto_cifrado ^ chave_int
    
    # Round 1 (decifragem reversa)
    bloco_decifrado = bloco_decifrado ^ chave_int
    
    # Retornar o texto decifrado como um número inteiro convertido para bytes
    return bloco_decifrado.to_bytes((bloco_decifrado.bit_length() + 7) // 8, byteorder='big').decode()

# Exemplo de uso
texto_claro = "AB"
chave = "XY"

# Cifragem
texto_cifrado = cifrar(texto_claro, chave)
print(f'Texto cifrado: {texto_cifrado}')

# Decifragem
texto_decifrado = decifrar(texto_cifrado, chave)
print(f'Texto decifrado: {texto_decifrado}')

```
## 7. Considere uma cifra de Feistel composta de 16 rodadas com tamanho de bloco de 128 bits e tamanho de chave de 128 bits. Suponha que, para determinado k, o algoritmo de escalonamento de chave defina valores as oito primeiras chaves de rodada, k1, k2, . . . , k8, e depois estabeleça k9 = k8, k10 = k7, k11 = k6, . . . , k16 = k1. Admita que você tenha um texto cifrado S. Explique como, com acesso a um oráculo de encriptação, você pode decriptar c e determinar m usando apenas uma única consulta a ele. Isso mostra que tal cifra é vulnerável a um ataque de texto claro escolhido.

Neste cenário, podemos usar um ataque conhecido como "ataque de texto claro escolhido". O processo é o seguinte:

1. Crie um texto claro `P` com o primeiro bloco preenchido com zeros e o segundo bloco contendo o texto cifrado `S` (ou seja, `P = 0 || S`).
2. Envie `P` para o oráculo de encriptação para obter o texto cifrado correspondente `C = E(P)`.
3. O resultado `C` terá a forma `C1 || C2` onde `C1` é o bloco cifrado do bloco de zeros e `C2` é o texto cifrado correspondente a `S`.

Devido à estrutura da cifra de Feistel e a maneira como as chaves são repetidas, você pode usar `C1` e `S` para deduzir o texto claro original.

Este exemplo mostra que a cifra é vulnerável porque permite a dedução do texto claro com uma única consulta ao oráculo de encriptação, destacando a importância de evitar padrões repetitivos na geração de sub-chaves.

