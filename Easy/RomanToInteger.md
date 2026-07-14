# Exercício: Roman to Integer

## Regras

- Se o valor menor estiver à esquerda de um valor maior, deve-se **diminuir**.
- Se o valor menor estiver à direita de um valor maior, deve-se **somar**.

Exemplo:

- `IV = 4` → `5 - 1`
- `VI = 6` → `5 + 1`

## Solução em Java

```java
class Solution {
    public int romanToInt(String s) {

        // Transformo minha String em um array de caracteres
        char[] caracteres = s.toCharArray();

        // Agora eu tenho uma lista com cada caractere em cada índice
        List<Character> listaCaracteres = new ArrayList<>();

        for (char c : caracteres) {
            listaCaracteres.add(c);
        }

        // Faço o mapeamento dos caracteres para depois só puxar com um get
        Map<Character, Integer> valores = new HashMap<>();

        valores.put('I', 1);
        valores.put('V', 5);
        valores.put('X', 10);
        valores.put('L', 50);
        valores.put('C', 100);
        valores.put('D', 500);
        valores.put('M', 1000);

        int soma = 0;

        // Agora eu percorro essa lista de caracteres
        for (int i = 0; i < listaCaracteres.size(); i++) {

            // Pego o valor do char no índice atual
            char atual = listaCaracteres.get(i);

            // Validação para saber se o próximo valor existe ou não
            if (i + 1 < listaCaracteres.size()) {

                // Pego o valor do char no próximo índice
                char proximo = listaCaracteres.get(i + 1);

                // Transformo em número através do map
                int valorAtual = valores.get(atual);
                int valorProximo = valores.get(proximo);

                // Comparo para verificar se o próximo valor é maior
                if (valorAtual < valorProximo) {

                    // Caso seja maior, subtraio o valor atual do próximo
                    soma = soma + (valorProximo - valorAtual);

                    // Pulo o próximo caractere pois ele já foi utilizado
                    i++;

                } else {

                    // Caso contrário, apenas adiciono o valor atual
                    soma += valorAtual;
                }

            } else {

                // Caso seja o último índice, adiciono seu valor e retorno
                return soma += valores.get(atual);
            }
        }

        return soma;
    }
}
```

## Complexidade

- **Tempo:** O(n)  
  - Percorremos a string apenas uma vez.

- **Espaço:** O(1)  
  - O mapa possui apenas os 7 símbolos romanos fixos.
