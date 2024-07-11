# Resposta - Atividade Cap. 02 - Técnicas clássicas de encriptação

**Aluno:** Fábio dos Santos Batalha Freire

## 1. Responda (de forma objetiva) as questões a seguir:

   (a) Os elementos essenciais de uma cifra simétrica são:

  - Texto claro: a mensagem ou dados originais antes da encriptação.
  - Algoritmo de encriptação: realiza substituições e transformações no texto claro.
  - Chave secreta: valor independente do texto claro e do algoritmo, usado como entrada para o algoritmo de encriptação.
  - Texto cifrado: a mensagem embaralhada produzida como saída do algoritmo de encriptação, dependente do texto claro e da chave secreta.
  - Algoritmo de decriptação: executa o algoritmo de encriptação de forma inversa, produzindo o texto claro original a partir do texto cifrado e da chave secreta.

   (b) Substituição e transposição.
  - Substituição: Substitui cada elemento do texto claro por outro elemento de acordo com uma regra específica.
  - Transposição: Rearranja a ordem dos elementos do texto claro de acordo com uma regra específica, sem alterar os elementos em si.

   (c)  A diferença entre uma cifra de bloco e uma cifra de fluxo é que uma cifra de bloco opera em blocos fixos de dados, enquanto uma cifra de fluxo cifra os dados em tempo real, bit a bit ou byte a byte.

   (d)
  - Ataques de força bruta: Tentativas sistemáticas de todas as combinações possíveis de chaves para decifrar o texto cifrado.
  - Criptoanálise: Análise das características do texto cifrado, do algoritmo de encriptação ou de ambos para encontrar fraquezas que possam ser exploradas para decifrar o texto cifrado sem a necessidade de tentar todas as combinações possíveis de chaves.

   (e) Problemas do one-time pad:
  - Criar grandes quantidades de chaves aleatórias representa um problema prático. Qualquer sistema bastante utilizado poderia exigir milhões de caracteres aleatórios regularmente. O fornecimento de caracteres de fato aleatórios nesse volume é uma tarefa significativa.
  - Problema da distribuição e proteção da chave. A cada mensagem a ser enviada, uma chave de mesmo tamanho é necessária para uso do emissor e do receptor. Assim, existe um problema gigantesco de distribuição de chave.

   (f) Uma cifra de transposição é um tipo de cifra em que as posições dos caracteres na mensagem são alteradas de acordo com um sistema pré-determinado, sem alterar os próprios caracteres.

   (g) Esteganografia é a prática de ocultar mensagens dentro de outros arquivos, como imagens ou áudio, de modo que a presença da mensagem oculta não seja aparente para um observador casual.

## 2. Uma generalização da cifra de César, conhecida como cifra de César afim, tem a seguinte forma: a cada letra de texto claro p, substitua-a pela letra de texto cifrado C:
  
(a) Sim, há limitações sobre o valor de b na cifra de César afim. Para garantir que a função de encriptação seja bijetora (um-para-um), o valor de b deve ser escolhido de modo que gcd(a, 26) divida b.

(b) Os valores de a que não são permitidos são aqueles em que gcd(a, 26) ≠ 1. Isso ocorre porque, se a e 26 não são coprimos, a função de encriptação não será um-para-um, resultando em letras do texto claro que não são mapeadas de maneira única no texto cifrado.

(c) Uma afirmação geral é que valores de a são permitidos se e somente se gcd(a, 26) = 1. Isso garante que a função de encriptação seja uma permutação de todas as letras do alfabeto, cumprindo o requisito de ser um-para-um. Valores de a que não atendem a essa condição não são permitidos, pois resultam em uma função de encriptação não bijetora.

## 3. 

## Encriptação usando a cifra de Hill

### Mensagem Original:
"meet me at the usual place at ten rather than eight oclock"

### Chave da Cifra de Hill:
K = [9 4]
    [5 7]

### Conversão da Mensagem para Números:
- "me" -> [12, 4]
- "et" -> [4, 19]
- "me" -> [12, 4]
- "at" -> [0, 19]
- "th" -> [19, 7]
- "eu" -> [4, 20]
- "su" -> [18, 20]
- "al" -> [0, 11]
- "pl" -> [15, 11]
- "ac" -> [0, 2]
- "ea" -> [4, 0]
- "tt" -> [19, 19]
- "en" -> [4, 13]
- "ra" -> [17, 0]
- "th" -> [19, 7]
- "er" -> [4, 17]
- "th" -> [19, 7]
- "an" -> [0, 13]
- "ei" -> [4, 8]
- "gh" -> [6, 7]
- "to" -> [19, 14]
- "cl" -> [2, 11]
- "oc" -> [14, 2]
- "kx" -> [10, 23]

### Aplicação da Cifra de Hill:
Para cada par de números, multiplicamos pela matriz chave K e reduzimos módulo 26.

**Exemplo:**
```
[12  4] * [9  4] = [ (12 * 9 + 4 * 5)  (12 * 4 + 4 * 7) ] = [ 128  76 ]
         [5  7]   [ (19 * 9 + 7 * 5)  (19  *4 + 7 * 7) ]   [ 209  120 ]
```

Reduzindo módulo 26:
[ 128 mod 26  76 mod 26 ] = [ 24  24 ]

Portanto, "me" é encriptado como "yx" (onde 24 corresponde a 'y' e 'x').

### Mensagem Encriptada:
"yx pc yx ow mz xx xl tz nz wu il ai ti zi rn"

Cada par de letras na mensagem encriptada corresponde a um par encriptado da mensagem original, calculado utilizando a matriz chave K.




## 4. 

## Código

```python
def encrypt(text, shift):
    encrypted_text = ""
    for char in text:
        if char.isalpha():
            shifted = ord(char) + shift
            if char.islower():
                if shifted > ord('z'):
                    shifted -= 26
            elif char.isupper():
                if shifted > ord('Z'):
                    shifted -= 26
            encrypted_text += chr(shifted)
        else:
            encrypted_text += char
    return encrypted_text

def decrypt(text, shift):
    decrypted_text = ""
    for char in text:
        if char.isalpha():
            shifted = ord(char) - shift
            if char.islower():
                if shifted < ord('a'):
                    shifted += 26
            elif char.isupper():
                if shifted < ord('A'):
                    shifted += 26
            decrypted_text += chr(shifted)
        else:
            decrypted_text += char
    return decrypted_text

def main():
    text = input("Digite o texto: ")
    shift = int(input("Digite o valor do deslocamento (número inteiro): "))

    encrypted_text = encrypt(text, shift)
    print("Texto criptografado:", encrypted_text)

    decrypted_text = decrypt(encrypted_text, shift)
    print("Texto descriptografado:", decrypted_text)

if __name__ == "__main__":
    main()
```

## 5.

## Código

```python
def decrypt_caesar(ciphertext, shift):
    plaintext = ''
    for char in ciphertext:
        if char.isalpha():
            shifted_char = chr(((ord(char) - ord('A') - shift) % 26) + ord('A')) if char.isupper() else chr(((ord(char) - ord('a') - shift) % 26) + ord('a'))
            plaintext += shifted_char
        else:
            plaintext += char
    return plaintext

def get_word_frequencies(text):
    word_list = text.split()
    word_count = {}
    for word in word_list:
        word_count[word] = word_count.get(word, 0) + 1
    return word_count

def attack_caesar_cipher(ciphertext, num_attempts=10):
    possible_messages = []
    for shift in range(26):
        decrypted_text = decrypt_caesar(ciphertext, shift)
        possible_messages.append((decrypted_text, get_word_frequencies(decrypted_text)))
    sorted_messages = sorted(possible_messages, key=lambda x: sum(x[1].values()), reverse=True)
    return sorted_messages[:num_attempts]

if __name__ == "__main__":
    ciphertext = input("Digite o texto cifrado: ")
    num_attempts = int(input("Número de tentativas de decifração para mostrar (por exemplo, 10): "))
    possible_messages = attack_caesar_cipher(ciphertext, num_attempts)
    print("\nOs", num_attempts, "textos claros mais prováveis são:\n")
    for i, (plaintext, _) in enumerate(possible_messages, start=1):
        print(f"Texto Claro #{i}: {plaintext}")

```

## 6.

```python

import numpy as np
from sympy import Matrix

# Função para verificar se a matriz é inversível em módulo 26
def is_invertible(matrix):
    det = Matrix(matrix).det() % 26
    return det != 0 and np.gcd(det, 26) == 1

# Função para encontrar a matriz inversa em módulo 26
def inverse_matrix(matrix):
    matrix = Matrix(matrix)
    inv_matrix = matrix.inv_mod(26)
    return np.array(inv_matrix).astype(int)

# Função para converter texto em números (A=0, B=1, ..., Z=25)
def text_to_numbers(text):
    return [ord(char) - ord('A') for char in text]

# Função para converter números em texto
def numbers_to_text(numbers):
    return ''.join([chr(num + ord('A')) for num in numbers])

# Função para criptografar uma mensagem usando a cifra de Hill 2x2
def encrypt(message, key_matrix):
    message = message.upper().replace(" ", "")
    while len(message) % 2 != 0:
        message += 'X'

    message_numbers = text_to_numbers(message)
    n = len(message_numbers)
    encrypted_message = ""

    for i in range(0, n, 2):
        pair = np.array(message_numbers[i:i+2])
        result = np.dot(key_matrix, pair) % 26
        encrypted_message += numbers_to_text(result)

    return encrypted_message

# Função para descriptografar uma mensagem usando a cifra de Hill 2x2
def decrypt(encrypted_message, key_matrix):
    key_inverse = inverse_matrix(key_matrix)
    message_numbers = text_to_numbers(encrypted_message)
    n = len(message_numbers)
    decrypted_message = ""

    for i in range(0, n, 2):
        pair = np.array(message_numbers[i:i+2])
        result = np.dot(key_inverse, pair) % 26
        decrypted_message += numbers_to_text(result)

    return decrypted_message

# Exemplo de uso:
if __name__ == "__main__":
    # Definindo uma nova chave de criptografia (matriz 2x2) que é invertível
    key_matrix = np.array([[9, 4], [5, 7]])

    # Mensagem original
    original_message = "HELLO"

    # Criptografando a mensagem
    encrypted_message = encrypt(original_message, key_matrix)
    print("Mensagem Criptografada:", encrypted_message)

    # Descriptografando a mensagem
    decrypted_message = decrypt(encrypted_message, key_matrix)
    print("Mensagem Descriptografada:", decrypted_message)
```
  
