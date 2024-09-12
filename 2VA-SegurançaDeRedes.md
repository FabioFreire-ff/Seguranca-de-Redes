## Q3
```python
# Definindo a S-Box usada no processo de criptografia
S_BOX = {
    '0000': '1001', '0001': '0100', '0010': '1010', '0011': '1011',
    '0100': '1101', '0101': '0001', '0110': '1000', '0111': '0101',
    '1000': '0110', '1001': '0010', '1010': '0000', '1011': '0011',
    '1100': '1100', '1101': '1110', '1110': '1111', '1111': '0111'
}

# Definindo a S-Box inversa para o processo de descriptografia
INV_S_BOX = {v: k for k, v in S_BOX.items()}

# Função para dividir a string binária em blocos de 4 bits
def split_by_n(bits, n=4):
    return [bits[i:i+n] for i in range(0, len(bits), n)]

# Função SubBytes (substituição de bytes)
def sub_bytes(block, sbox):
    return ''.join([sbox[block[i:i+4]] for i in range(0, len(block), 4)])

# Função ShiftRows (transposição de linhas)
def shift_rows(block):
    return block[:4] + block[8:12] + block[4:8] + block[12:]

# Função MixColumns (mistura de colunas)
def mix_columns(block):
    # Para o S-AES, o MixColumns envolve operações específicas de campo finito
    mixed_block = [
        block[0], block[1], block[2], block[3],  # MixColumns não afeta no S-AES simplificado
        block[4], block[5], block[6], block[7],
        block[8], block[9], block[10], block[11],
        block[12], block[13], block[14], block[15]
    ]
    return ''.join(mixed_block)

# Função AddRoundKey (adição de chave de rodada)
def add_round_key(block, key):
    return ''.join(['1' if block[i] != key[i] else '0' for i in range(len(block))])

# Função para criptografar usando S-AES
def s_aes_encrypt(plaintext, key):
    # Rodada 1
    state = add_round_key(plaintext, key)
    state = sub_bytes(state, S_BOX)
    state = shift_rows(state)
    state = mix_columns(state)
    
    # Rodada Final
    state = add_round_key(state, key)
    return state

# Função para descriptografar usando S-AES
def s_aes_decrypt(ciphertext, key):
    # Rodada Final
    state = add_round_key(ciphertext, key)
    
    # Rodada Inversa
    state = mix_columns(state)
    state = shift_rows(state)
    state = sub_bytes(state, INV_S_BOX)
    state = add_round_key(state, key)
    
    return state

# Dados do problema
plaintext = '0110111101101011'
key = '1010011100111011'
expected_ciphertext = '0000011100111000'

# Criptografar
ciphertext = s_aes_encrypt(plaintext, key)
print(f"Texto cifrado: {ciphertext}")

# Verificar se a criptografia está correta
print(f"Criptografia correta? {ciphertext == expected_ciphertext}")

# Descriptografar
decrypted_text = s_aes_decrypt(ciphertext, key)
print(f"Texto decifrado: {decrypted_text}")

# Verificar se a descriptografia está correta
print(f"Descriptografia correta? {decrypted_text == plaintext}")
```

## Q4 


```python
def totient_euler(n):
    # Fatora n
    fatores = factor(n)
    
    # Inicializa φ(n) como o valor de n
    phi = n
    
    # Para cada fator primo p de n, aplica a fórmula
    for p, _ in fatores:
        phi *= (1 - 1/p)
    
    # Retorna o valor inteiro de φ(n)
    return int(phi)

totient_euler(10)
```


## Q5

```python
# Função para calcular as raízes quadradas modulares de um número
def raiz_quadrada_mod(x, p):
    # Fórmula: x^(p+1)/4 mod p
    return power_mod(x, (p + 1) // 4, p)

# Função para encontrar o estado anterior do Blum Blum Shub
def encontrar_estado_anterior(x_n, p, q):
    # Calcula as raízes quadradas mod p e q
    raiz_p = raiz_quadrada_mod(x_n, p)
    raiz_q = raiz_quadrada_mod(x_n, q)

    # Quatro possíveis raízes usando o teorema chinês dos restos
    possibilidades = []
    
    # Soluções possíveis com as combinações de +raiz_p, -raiz_p e +raiz_q, -raiz_q
    for s_p in [raiz_p, p - raiz_p]:
        for s_q in [raiz_q, q - raiz_q]:
            # Teorema Chinês dos Restos para combinar as raízes
            s = crt([s_p, s_q], [p, q])
            possibilidades.append(s)
    
    return possibilidades

# Exemplo prático

# Gerando dois números primos p e q tais que p ≡ 3 mod 4 e q ≡ 3 mod 4
p = 499  # Exemplo de primo p
q = 547  # Exemplo de primo q

# Módulo do Blum Blum Shub
n = p * q

# Gerando um estado atual (x_n) do Blum Blum Shub
# Escolhendo uma semente aleatória s
s = 12345  # Você pode escolher outra semente
x_n = power_mod(s, 2, n)  # x_n = s^2 mod n

# Encontrando o estado anterior (s^2 mod n)
estados_anteriores = encontrar_estado_anterior(x_n, p, q)

# Exibindo os resultados
print("Estado atual (x_n):", x_n)
print("Possíveis estados anteriores (s):", estados_anteriores)

```

## Q8

```python
# (a)
N_a = 13962799
e_a = 3
assinatura_a = 8674413
valor_assinado_a = power_mod(assinatura_a, e_a, N_a)
valor_esperado_a = 821
valor_esperado_a == valor_assinado_a

# (b)
N_b = 34300129
e_b = 61
assinatura_b = 27535246
valor_assinado_b = power_mod(assinatura_b, e_b, N_b)
valor_esperado_b = 2478
valor_esperado_b == valor_assinado_b

# (c)
N_c = 5898461
e_c = 23
assinatura_c = 2607727
valor_assinado_c = power_mod(assinatura_c, e_c, N_c)
valor_esperado_c = 419
valor_esperado_c == valor_assinado_c

# (d)
p = 3181
q = 2677
e = 163
N = p * q
valor_para_assinar = 521
assinatura = power_mod(valor_para_assinar, e, N)
valor_assinado = power_mod(assinatura, e, N)
N, assinatura, valor_assinado
```


## Q9

```python
# Função para gerar chaves RSA
def gerar_chaves_rsa(tamanho=512):
    p = random_prime(2^tamanho, lbound=2^(tamanho-1))
    q = random_prime(2^tamanho, lbound=2^(tamanho-1))
    n = p * q
    phi_n = (p - 1) * (q - 1)
    e = 65537
    d = inverse_mod(e, phi_n)
    return (e, n), (d, n)

# Função de criptografia RSA
def criptografar_rsa(mensagem, chave_publica):
    e, n = chave_publica
    return power_mod(mensagem, e, n)

# Função de descriptografia RSA
def descriptografar_rsa(mensagem_cifrada, chave_privada):
    d, n = chave_privada
    return power_mod(mensagem_cifrada, d, n)

# Simulação
chave_publica, chave_privada = gerar_chaves_rsa()
mensagem_original = 123456789
mensagem_cifrada = criptografar_rsa(mensagem_original, chave_publica)
mensagem_decifrada = descriptografar_rsa(mensagem_cifrada, chave_privada)

print(f"Mensagem cifrada: {mensagem_cifrada}")
print(f"Mensagem decifrada: {mensagem_decifrada}")

if mensagem_original == mensagem_decifrada:
    print("A criptografia e descriptografia RSA funcionaram corretamente!")
```









