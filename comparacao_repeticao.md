````md
# 📘 Guia Básico de JavaScript (Para Iniciantes)

Este documento foi criado para fins de estudo, simplificando o entendimento de lógica e estruturas básicas em JavaScript.
Todas as funções podem ser refatoradas para melhor performance e leitura por outros devs ao utilizar no dia a dia

---

## 📚 Operadores

```javascript
===  // igual
!==  // diferente
!    // negação (not)
&&   // e (and)
||   // ou (or)
>    // maior
<    // menor
>=   // maior ou igual
<=   // menor ou igual
````

---

## 🔀 IF / ELSE

Estrutura de decisão usada para comparar valores.
SE "tal condição" for verdadeira ENTÃO faça "tal coisa" SENÃO faça "tal"
Utilizar no máximo 3 condições por bloco, para que o código seja mais limpo
Ex: IF (1 E 1) E (1 OU 1) OU (1 OU 0) {}

*estrutura padrão:
```javascript
//if simples: Se condição então faça isso
if (condition) {
  
}

//if else: Se condição então faça isso Senão faça tal
if (condition) {
  
} else {
  
} 

```

### 🧠 Exemplo básico

```javascript
const idade = 18;
const cor = "verde";
const altura = 150;

if (idade >= 18) {//SE idade maior ou igual a 18, ENTÃO é maior de idade
  console.log("Maior de idade");
}
```

---

### 🔗 Múltiplas condições (AND / OR)

```javascript
//quando utilizado mais de uma condição no mesmo if, é feita comparação em pares. Se houver mais de um par, compara o resultado do primeiro par com o segundo, e assim por diante
//if ((idade >= 18) && (cor === "verde")) 
if (idade >= 18 && cor === "verde") {//SE idade maior ou igual a 18 E cor igual a verde ENTÃO é maior de idade - APENAS se AS DUAS forem verdadeiras
  console.log("Maior de idade");
}
```

```javascript
if (idade >= 18 || cor === "amarelo") {//SE idade maior ou igual a 18 OU cor igual a amarelo ENTÃO é maior de idade - PODE ser UMA OU OUTRA verdadeira. A cor informada foi verde
  console.log("Maior de idade");
}
```

```javascript
//if ((idade >= 18) || (cor === "amarelo") && (altura > 160)) { //SE idade maior ou igual a 18 OU cor igual a amarelo E altura maior que 160 ENTÃO é maior de idade - PODE a primeira ou a segunda verdadeira, logo o primeiro par é verdadeiro, mas a terceira condição precisa ser verdadeira para que entre nesse IF.
if ((idade >= 18 || cor === "amarelo") && altura > 160) {
  console.log("Maior de idade");
}
```


---

### 🔁 IF / ELSE

```javascript
if (idade >= 18) { //SE idade maior ou igual a 18, ENTÃO é maior de idade
  console.log("Maior de idade");
} else { //SENÃO é menor de idade
  console.log("Menor de idade");
}
```
### 🛑 Atenção com parêntestes
Dependedo a posição ou ausência do parêntese, o resultado altera, entrando ou não no `IF`
* `(idade >= 18 || cor === "amarelo" && altura > 160)`   → vai validar todas as condições - SE primeira for verdadeira `OU` segunda for verdadeira `E` terceira for verdadeira
* `((idade >= 18 || cor === "amarelo") && altura > 160)` → vai validar o primeiro par `E` comparar com a terceira condição
* `(idade >= 18 || (cor === "amarelo" && altura > 160)`  → vai validar a primeira condição `OU` segundo par verdadeiro

---

## 🔄 SWITCH CASE

Usado quando há várias comparações possíveis para um único valor.
Funciona como o IF comparando com valores distintos

Switch verifica o resultado CASO "tal" variável repassada, retorna "tal" valor. 
BREAK instrui que pare de validar e retorne "tal" valor. 
DEFAULT é sempre o valor padrão que irá retornar caso nenhuma das condições anteriores sejam satisfeitas.
Utilizar switch somente se houver mais uma condição a ser verificada, senão utilizar IF

### 🧠 Estrutura básica

```javascript
switch (value) {
  case 1:
    break;
  case 2:
    break;
  default:
    break;
}
```

---

### 📅 Exemplo prático

```javascript
function nomeDiaExtenso(dia) {
  let nome = ""; //cria uma variável para receber o nome do dia por extenso

  switch (dia) {
    case 1:
      nome = "Domingo";
      break;
    case 2:
      nome = "Segunda";
      break;
    case 3:
      nome = "Terça";
      break;
    case 4:
      nome = "Quarta";
      break;
    case 5:
      nome = "Quinta";
      break;
    case 6:
      nome = "Sexta";
      break;
    case 7:
      nome = "Sábado";
      break;
    default:
      nome = "Inválido";
  }

  return nome;
}
```

### ▶️ Testando a função

```javascript
console.log(nomeDiaExtenso(1)); // Domingo
console.log(nomeDiaExtenso(5)); // Quinta
console.log(nomeDiaExtenso(9)); // Inválido
```

---

## 🔄 FOR
Estrutura de repetição composta por 3 partes: inicialização; condição; incremento
for (let index = 0; `(inicialização)` index < array.length; `(condição)` index++ `(incremento)`) 
* `index = 0` → qual o valor que irá iniciar 
* `index < array.length` → qual será a condição para que pare de executar a repetição
* `index++` → incrementando o índice atual +1 

*estrutura padrão:
```javascript
for (let index = 0; index < array.length; index++) {
  const element = array[index];  
}
```

### 🧠 Exemplo básico

```javascript
for (let index = 0; index < 5 ; index++) { //Inicie com 0, repita enquanto o índice (atual) for menor que 5, some índice +1
  console.log("Registro atual = ", index);//Cada vez que incrementar, vai mostrar o índice do registro atual
} 
```

### 🛑 Cuidado com o `FOR` infinito 
Nunca vai parar de executar porque `não tem a definição da condição`, que é o segundo parametro, foi setado como `true`
Pode ocasionar travas no programa ou navegador e consome memória desnecessária

```javascript
for (let index = 0; true; index++) {
    console.log("for", index);
   } 
```
Caso necessite utilização intencional, verificar casos específicos de aplicação.

---
### 🔄 FOR EACH
Utilizado para percorrer listas (array) e executar algo `PARA CADA` item.
Para executar ações e não retorna valor.

*estrutura padrão:
```javascript
array.forEach(element => {
  
});
```
### 🧠 Exemplo básico

```javascript
const numeros = [1, 2, 3, 4]; //dados valores para a variável complexa

numeros.forEach((numero) => {//seleciona a variável. PARA CADA parametro 'numero' recebe um valor ordenado da variável 'numeros'. Poderia ser qualquer nome.
  console.log(numero * 2); //exibe o resultado sendo 'numero' atual * 2. Por exemplo 1*2, 2*2, 3*2, 4*2
});
```
---

## 🔄 WHILE
Estrutura de repetição que somente para a execução enquanto a condição for verdadeira.
`ENQUANTO` for falso continua executando.
Dependendo a condição imposta, pode não ser executado.

*estrutura padrão:
```javascript
while (condição) {
  // código que será repetido
}
```

### 🧠 Exemplo básico

```javascript
let numero = 1;//valor inicial = 1

while (numero < 5) { //ENQUANTO variável número for menor que 5, sendo 1 a 4
  console.log(numero); //exiba o número. Aqui pode alterar o valor caso seja incremental, como no exemplo
  numero = numero + 1; //incrementa a variável número. Uma forma de finalizar o laço
}
```

### 🛑🛑🛑 Cuidado com o `WHILE` infinito 🛑🛑🛑
Nunca vai parar de executar porque `não tem a definição` de quando vai parar de executar.
Pode ocasionar travas no programa ou navegador e consome memória desnecessária

```javascript
let numero = 1;
while (numero < 5) {
  console.log(numero); 
  //?? CADÊ a definição de PARE? 
}
```
---
## 🔄 DO...WHILE
Semelhante ao WHILE, `FAÇA ENQUANTO` se refere a execução antes mesmo de um teste.
Logo, neste laço de repetição, irá executar pelo menos uma vez antes de sair de uma condição.
A estrutura é invertida do primeiro while.

```javascript
let numero = 1;//valor inicial = 1

do { // FAÇA
  console.log(numero); //exiba o número. Aqui pode alterar o valor caso seja incremental, como no exemplo
  numero = numero + 1; //incrementa a variável número. Uma forma de finalizar o laço
} while (numero < 5) //ENQUANTO variável número for menor que 5, sendo 1 a 4
```

---

## ⚠️ Dicas importantes

- Quando utilizar `if` → lembre de colocar a condição entre parênteses.
- `Utilizar no máximo 3 condições por bloco IF` para manter o código limpo.
- Evitar utilizar `else` → preferir retornos diretos.
- Utilizar igualdade absoluta `===` → (três sinais de igual) para que a comparação tenha resultado verdadeiro
- `Índices` iniciam sempre em 0.
- Utilizar `for` → quando você sabe quantas vezes vai repetir
- Utilizar `while` → quando repete até uma condição mudar
- `while` → testa antes de executar.
- `do while` → executa antes de testar. Executa pelo menos uma vez mesmo que a condição seja falsa.

### 💡 Boas práticas em funções:
- Faça primeiro as validações de erro ou saída antecipada e depois execute a lógica principal da função.
As condições que impedem a continuação, retornos de erros, tipos de variáveis repassada, devem ser as primeiras coisas da função, e depois realizar o propósito dela somente se todas as condições forem satisfeitas
- Um `return` encerra a função imediatamente.




