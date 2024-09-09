### Types
#### 2.1 Var, Let, Const

O capítulo começa com o livro explicando a diferença entre os tipos de declarações de variáveis do javascript: "var, let e const"

Basicamente: 
- Var: Variável de escopo, ela é "puxada" (Hoisting) para o topo do seu contexto de execuçao, que no caso do "var", é global.
```
mensagem = 'MSG';
console.log(mensagem);
var mensagem; //MSG
```
- Let: Variável com escopo de bloco, quando é "içada, puxada" pelo processo de Hoisting, o topo de seu contexto de execução é do bloco onde ela está declarada, seja um if, um loop ou uma function.
```
let mensagemForaDoIf = 'mensagem fora do if';
if (true) {
	let mensagemDentroDoIf = 'mensagem dentro do if';
	console.log(mensagemDentroDoIf);
}
console.log(mensagemForaDoIf);
console.log(mensagemDentroDoIf);
Resultado:
//mensagem dentro do if
//mensagem fora do if
//ReferenceError: mensagemDentroDoIf is not defined
```
- Const: Mesma coisa do let, porém é um valor constante que não pode ser modificado
```
const mensagem = 'MSG 1';
console.log(mensagem); // MSG 1
mensagem = 'MSG 2'; // TypeError: Assignment to constant variable.
Resultado:
// MSG 1
// TypeError: Assignment to constant variable.
```
---
Após isso foi falado sobre os tipos de dados que são aceitos:

#### 2.2 Number
No TypeScript, todos os valores numéricos, como floating, decimal, hex, octal devem ser tipados como number.
```
let octal : number = 0o745;
let binary : number = 0b1111;
let decimal : number = 34;
let hex : number = 0xf34d;

```

#### 2.3 Boolean 

```
let ativo : boolean;
ativo = false;
ativo = true;
```

Nós também podemos declarar uma variável sem o seu type, basta passar o seu valor inicial:
let ativo : boolean = true;

#### 2.4 String

Podem ser declaradas tanto com ' ' ou com " ".

```
let cor: string = "verde";
cor = 'azul';
```

Usando template strings:

```
let nome: string = 'Anders Hejlsberg';
let idade: number = 58;
let sentence: string = `Olá, meu nome é ${ nome }, eu tenho ${idade} anos.
```

#### 2.5 Trabalhando com Strings

Métodos e propriedades mais utilizadas para trabalhar com strings

##### Length

```
//outras variáveis 
let sentence: string = `Olá, meu nome é ${ nome }, eu tenho ${idade} anos.`; 
console.log(sentence.length); //Resultado 51
```

##### IndexOf

```
//outras variáveis 
let sentence: string = `Olá, meu nome é ${ nome }, eu tenho ${idade} anos.`; 
console.log(sentence.indexOf('nome')); //posição 9
```

Caso procure uma palavra ou caractere que não existe, retorna -1:

```
//outras variáveis let sentence: string = `Olá, meu nome é ${ nome }, eu tenho ${idade} anos.`; 
console.log(sentence.indexOf('idade')); //retorno -1 console.log(sentence.indexOf('!')); //retorno -1
```

#### 2.6 Array

Podemos declarar usando colchetes:
```
let numeros: number[] = [1, 2, 3]; 
let textos : string[] = ["exemplo 1", "exemplo 2", "exemplo 3"];
```

Ou usando "Array<>":

```
let numeros: Array<number> = [1, 2, 3]; 
let textos: Array<string> = ["exemplo 1", "exemplo 2", "exemplo 3"];
```

Para adicionar um item ao array, podemos usar a função "push"

```
let numeros: Array<number> = [1, 2, 3]; 
let textos: Array<string> = ["exemplo 1", "exemplo 2", "exemplo 3"]; 
numeros.push(4); 
textos.push("exemplo 3"); 
console.log(numeros); 
console.log(textos); 
//Resultado 
[ 1, 2, 3, 4 ] 
[ 'exemplo 1', 'exemplo 2', 'exemplo 3', 'exemplo 3' ]
```

#### 2.7 ReadonlyArray

O `ReandolyArray<T>` é um array que nos permite somente leitura, ele remove métodos como push, pop e etc.

```
let numerosDaMega: ReadonlyArray<number> = [8, 5, 5, 11, 4, 28]; numerosDaMega[0] = 12; // error! 
numerosDaMega.push(23); // error! 
numerosDaMega.pop(); // error! 
numerosDaMega.length = 100; // error!
```

À versão 3.4 do TypeScript, foi adicionada uma nova sintaxe para o `ReadonlyArray<T>` . Nessa versão, o time que cuida do TypeScript simplificou a declaração dos ``ReadonlyArray<T>`` para ``Readonly<T>`` . A seguir você tem o exemplo com o array numerosDaMega atualizado com essa nova sintaxe 

```
Readonly<T> : let numerosDaMega: Readonly<number[]> = [8, 5, 5, 11, 4, 28];
```

