# Resolução de Exercícios

## 1. Definições

### Grupo
Um grupo ((G, ⋅)) é um conjunto (G) com uma operação binária (⋅) que satisfaz quatro propriedades:
- **Fechamento:** Para todos (a, b ∈ G), (a ⋅ b ∈ G).
- **Associatividade:** Para todos (a, b, c ∈ G), ((a ⋅ b) ⋅ c = a ⋅ (b ⋅ c)).
- **Elemento neutro:** Existe um elemento (e ∈ G) tal que para todo (a ∈ G), (a ⋅ e = e ⋅ a = a).
- **Inverso:** Para cada (a ∈ G), existe um (b ∈ G) tal que (a ⋅ b = b ⋅ a = e).

### Anel
Um anel ((R, +, ⋅)) é um conjunto (R) equipado com duas operações binárias (+) e (⋅) tal que:
- ((R, +)) é um grupo abeliano.
- ((R, ⋅)) é um semigrupo.
- A operação (⋅) é distributiva em relação a (+).

### Corpo
Um corpo ((K, +, ⋅)) é um anel comutativo com identidade (1 ≠ 0) tal que cada elemento diferente de zero possui um inverso multiplicativo.

## 2. Divisor

Dizer que (b) é um divisor de (a) significa que existe um inteiro (k) tal que (a = b ⋅ k). Em outras palavras, (b) divide (a) sem deixar resto.

## 3. Encontrar Inteiros (x)

Para encontrar (x) que satisfaça cada congruência, resolvemos as equações módulo.

### (a) 5x ≡ 4 (mod 3)

5 ≡ 2 (mod 3) ⟹ 2x ≡ 4 (mod 3) ⟹ 2x ≡ 1 (mod 3) ⟹ x ≡ 2 (mod 3)

### (b) 7x ≡ 6 (mod 5)

7 ≡ 2 (mod 5) ⟹ 2x ≡ 1 (mod 5) ⟹ x ≡ 3 (mod 5)

### (c) 9x ≡ 8 (mod 7)

9 ≡ 2 (mod 7) ⟹ 2x ≡ 1 (mod 7) ⟹ x ≡ 4 (mod 7)

## 4. Inverso Multiplicativo em ℤ₅

Em **Z5**, os elementos diferentes de zero são (1, 2, 3,) e (4). Vamos encontrar o inverso multiplicativo de cada um desses elementos:

- Para ( a = 1 ): ( 1 * 1 ≡ 1 (mod 5) ). Portanto, o inverso multiplicativo de ( 1 ) em Z5 é ( 1 ).

- Para ( a = 2 ): ( 2 * 3 = 6 ≡ 1 (mod 5) ). Assim, o inverso multiplicativo de ( 2 ) em Z5 é ( 3 ).

- Para ( a = 3 ): ( 3 * 2 = 6 ≡ 1 (mod 5) ). Portanto, o inverso multiplicativo de ( 3 ) em Z5 é ( 2 ).

- Para ( a = 4 ): ( 4 * 4 = 16 ≡ 1 (mod 5) ). Logo, o inverso multiplicativo de ( 4 ) em Z5 é ( 4 ).

Assim, os inversos multiplicativos de cada elemento não zero em Z5 são:

- Inverso de ( 1 ): ( 1 )
- Inverso de ( 2 ): ( 3 )
- Inverso de ( 3 ): ( 2 )
- Inverso de ( 4 ): ( 4 )

## 5. Determinação dos MDC

### (a) mdc(24140, 16762)

Utilizando o algoritmo de Euclides:

```
24140 = 16762 ⋅ 1 + 7378
16762 = 7378 ⋅ 2 + 2006
7378 = 2006 ⋅ 3 + 1360
2006 = 1360 ⋅ 1 + 646
1360 = 646 ⋅ 2 + 68
646 = 68 ⋅ 9 + 34
68 = 34 ⋅ 1 + 0
```
Portanto, mdc(24140, 16762) = 34.

### (b) mdc(4655, 12075)

Utilizando o algoritmo de Euclides:

```
12075 = 4655 ⋅ 2 + 2765
4655 = 2765 ⋅ 1 + 1890
2765 = 1890 ⋅ 1 + 875
1890 = 875 ⋅ 2 + 140
875 = 140 ⋅ 6 + 35
140 = 35 ⋅ 4 + 0
```
Portanto, mdc(4655, 12075) = 35.

## 6. Algoritmo de Euclides Estendido para Inverso Multiplicativo

### Encontrar o inverso multiplicativo usando o algoritmo de Euclides estendido:

#### (a) Encontrar o inverso de 1234 mod 4321

Para encontrar o inverso multiplicativo de 1234 modulo 4321 usando o algoritmo de Euclides estendido:

1. **Passo 1:** Aplicar o algoritmo de Euclides para encontrar gcd(1234, 4321):
   - 4321 = 3 * 1234 + 619
   - 1234 = 1 * 619 + 615
   - 619 = 1 * 615 + 4
   - 615 = 153 * 4 + 3
   - 4 = 1 * 3 + 1
   - 3 = 3 * 1 + 0
   Assim, gcd(1234, 4321) = 1.

2. **Passo 2:** Aplicar o algoritmo de Euclides estendido para expressar 1 como combinação linear de 1234 e 4321:
   - 1 = 29 * 1234 - 8 * 4321
   Portanto, o inverso de 1234 modulo 4321 é 29.

#### (b) Encontrar o inverso de 24140 mod 40902

Para encontrar o inverso multiplicativo de 24140 modulo 40902:

1. Aplicando o algoritmo de Euclides para encontrar gcd(24140, 40902):
   - O resultado mostra que gcd(24140, 40902) = 2.
   Como gcd(24140, 40902) ≠ 1, o inverso multiplicativo não existe porque 24140 não é coprimo com 40902.

#### (c) Encontrar o inverso de 550 mod 1769

Para encontrar o inverso multiplicativo de 550 modulo 1769 usando o algoritmo de Euclides estendido:

1. **Passo 1:** Aplicar o algoritmo de Euclides para encontrar gcd(550, 1769):
   - 1769 = 3 * 550 + 119
   - 550 = 4 * 119 + 74
   - 119 = 1 * 74 + 45
   - 74 = 1 * 45 + 29
   - 45 = 1 * 29 + 16
   - 29 = 1 * 16 + 13
   - 16 = 1 * 13 + 3
   - 13 = 4 * 3 + 1
   - 3 = 3 * 1 + 0
   Assim, gcd(550, 1769) = 1.

2. **Passo 2:** Aplicar o algoritmo de Euclides estendido para expressar 1 como combinação linear de 550 e 1769:
   - 1 = -289 * 550 + 89 * 1769
   Portanto, o inverso de 550 modulo 1769 é -289, que é equivalente a 1480 modulo 1769.

Resumindo os resultados:

- (a) O inverso de 1234 modulo 4321 é 29.
- (b) Não existe inverso de 24140 modulo 40902 porque gcd(24140, 40902) ≠ 1.
- (c) O inverso de 550 modulo 1769 é 1480.


## 7. Inverso Multiplicativo de x³ + x + 1 em GF(2⁴) com m(x) = x⁴ + x + 1

---

Para determinar o inverso multiplicativo de x^3 + x + 1 em GF(2^4) com m(x) = x^4 + x + 1, utilizamos o algoritmo estendido de Euclides sobre corpos finitos.

### Passos para encontrar o inverso multiplicativo:

1. **Identificar os polinômios:**
   - f(x) = x^3 + x + 1
   - m(x) = x^4 + x + 1

2. **Aplicar o algoritmo de Euclides estendido:**
   - Queremos encontrar g(x) tal que f(x) * g(x) ≡ 1 mod m(x).

3. **Passo 1: Aplicar o algoritmo de Euclides:**

   - Dividindo m(x) por f(x):
     - x^4 + x + 1 = (x^3 + x + 1)(x) + (x^2 + 1)

   - Portanto, x^2 + 1 = m(x) - (x^3 + x + 1)(x).

4. **Passo 2: Continuar o algoritmo:**

   - x^3 + x + 1 = (x^2 + 1)(x) + x + 1
   - x^2 + 1 = (x + 1)(x) + 1

   - Continuamos até que o resto seja 1.

5. **Encontrar o inverso:**

   - O algoritmo de Euclides estendido nos fornece uma expressão para 1 em termos de f(x) e m(x):
     - 1 = (x^2 + 1)(x^2 + x + 1) + (x^3 + x + 1)(x^3 + x^2 + 1)

   - Portanto, o inverso multiplicativo de x^3 + x + 1 em GF(2^4) é x^3 + x^2 + 1.

--- 


## 8. Aritmética de Polinômios em ℤ₁₀

### Parte (a)

Para resolver (7x + 2) - (x^2 + 5) em Z10:

1. Primeiro, subtraímos os polinômios termo a termo:

   7x + 2 - (x^2 + 5)

2. Distribuímos o sinal negativo no segundo polinômio:

   7x + 2 - x^2 - 5

3. Reorganizamos os termos em ordem decrescente de grau:

   -x^2 + 7x + (2 - 5)

4. Simplificamos o coeficiente constante:

   -x^2 + 7x - 3

5. Para garantir que os coeficientes estão em Z10, aplicamos o módulo 10:

   -x^2 + 7x - 3

Portanto, (7x + 2) - (x^2 + 5) = 9x - x^2 - 3 em Z10.

### Parte (b)

Agora, vamos multiplicar (6x^2 + x + 3) × (5x^2 + 2) em Z10:

1. Multiplicamos os polinômios termo a termo, considerando módulo 10:

   (6x^2 + x + 3) × (5x^2 + 2)

2. Distribuímos cada termo do primeiro polinômio pelo segundo:

   6x^2 × 5x^2 + 6x^2 × 2 + x × 5x^2 + x × 2 + 3 × 5x^2 + 3 × 2

3. Calculamos cada produto e aplicamos módulo 10:

   30x^4 + 12x^2 + 5x^3 + 2x + 15x^2 + 6

4. Reduzimos os coeficientes módulo 10:

   0x^4 + 2x^3 + 7x^2 + 2x + 6

Então, (6x^2 + x + 3) × (5x^2 + 2) = 2x^3 + 7x^2 + 2x + 6 em Z10.

## 9. Calculadora Simples em GF(2⁴)

Para criar uma calculadora simples de quatro funções (adição, subtração, multiplicação e divisão) em GF(2^4) (o corpo finito com 16 elementos), precisamos definir alguns elementos básicos:

**Representação dos Elementos:** Em GF(2^4), cada elemento pode ser representado como um polinômio de grau até 3 com coeficientes binários. Por exemplo, o elemento "5" pode ser representado pelo polinômio 𝑥^2 + 1.

**Adição:** A adição em GF(2^4) é simplesmente a operação XOR entre os coeficientes binários dos polinômios correspondentes.

**Multiplicação:** A multiplicação em GF(2^4) é um pouco mais complexa e envolve a multiplicação de polinômios seguida de uma redução módulo um polinômio irreduzível específico. Um polinômio irreduzível comumente usado em GF(2^4) é 𝑥^4 + 𝑥 + 1.

**Inversos Multiplicativos:** Para a divisão, precisamos dos inversos multiplicativos de cada elemento não nulo em GF(2^4). Esses inversos podem ser pré-calculados e armazenados em uma tabela.

```python
# Tabela de inversos multiplicativos em GF(2^4)
inverse_table = {
    0x1: 0x1, 0x2: 0x8, 0x3: 0x4, 0x4: 0x3,
    0x5: 0xC, 0x6: 0x6, 0x7: 0x2, 0x8: 0xB,
    0x9: 0xD, 0xA: 0x9, 0xB: 0x5, 0xC: 0x7,
    0xD: 0xA, 0xE: 0xE, 0xF: 0xF
}

# Funções auxiliares

def gf_add(a, b):
    """ Adição em GF(2^4) """
    return a ^ b

def gf_sub(a, b):
    """ Subtração em GF(2^4) (que é a mesma que adição) """
    return gf_add(a, b)

def gf_mult(a, b):
    """ Multiplicação em GF(2^4) usando o polinômio irredutível x^4 + x + 1 """
    result = 0
    while b > 0:
        if b & 1:
            result ^= a
        a <<= 1
        if a & 0x10:  # Se houver termo x^4, reduzir usando x^4 + x + 1
            a ^= 0x13
        b >>= 1
    return result

def gf_div(a, b):
    """ Divisão em GF(2^4) usando inversos multiplicativos """
    if b == 0:
        raise ZeroDivisionError("Divisão por zero em GF(2^4)")

    # A divisão é multiplicação por inverso de b
    inverse_b = inverse_table[b]
    return gf_mult(a, inverse_b)

# Teste da calculadora

def main():
    a = 0x5  # Exemplo de número em GF(2^4)
    b = 0x3  # Outro exemplo

    print(f"Adição de {a} e {b}:", gf_add(a, b))
    print(f"Subtração de {a} e {b}:", gf_sub(a, b))
    print(f"Multiplicação de {a} e {b}:", gf_mult(a, b))
    print(f"Divisão de {a} por {b}:", gf_div(a, b))

if __name__ == "__main__":
    main()


```


