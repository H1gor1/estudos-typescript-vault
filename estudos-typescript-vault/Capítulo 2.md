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

teste