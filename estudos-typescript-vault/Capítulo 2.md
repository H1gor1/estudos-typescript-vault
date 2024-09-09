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

#### 2.8 Tuplas

Tuplas são arrays com diferentes tipos de dados por exemplo:

```
let list: [string, number, string] = ['string', 1, 'string 2'];
```

No TypeScript 4.0, podemos adicionar nomes nos parâmetros das tuplas:

```
let list: [nome: string, idade: number, email: string] = ['Bill Gates', 65, 'bill@teste.com'];

```

Para adicionar um novo registro a uma tupla também fazemos igual ao Array

```
let list: [string, number] = ['Bill Gates', 1]; 
list.push('Steve', 2);
```

Agora para testar um desses valores, podemos utilizar os seus índices. 

```
let list: [string, number] = ['Bill Gates', 1]; 
console.log(list[0]); //Bill 
console.log(list[1]); //1 
//Resultado: 
//Bill 
//1 
```

Assim como nos arrays, nós também podemos trabalhar com a palavra reservada readonly com as tuplas . 

```
let list: readonly [string, number] = ['Bill Gates', 1]; 
list.push('Steve', 2); 

//Resultado: index.ts:2:6 - error TS2339: Property 'push' does not exist on type 'readonly [string, number]'. 2 list.push('Steve', 2);
```

#### 2.9 Enum

O ``enum`` nos permite declarar um conjunto de valores/constantes predefinidos. Existem 3 formas de se trabalhar com ele no typescript:

##### Numérico

Nós podemos declará-los com um valor inicial. 

```
export enum DiaDaSemana { 
	Segunda = 1, 
	Terca = 2, 
	Quarta = 3,
	Quinta = 4, 
	Sexta = 5, 
	Sabado = 6, 
	Domingo = 7 
} 
```

Caso você não passe um valor inicial na declaração do seu enum , o compilador do TypeScript fará um autoincremento de +1 iniciando em 0 até o último elemento do enum. 

```
export enum DiaDaSemana { 
	Segunda, //0
	Terca, //1
	Quarta, //2
	Quinta, //...
	Sexta, 
	Sabado, 
	Domingo 
} 
```

Ou, no caso de passarmos um valor numérico inicial, ele fará como no passo anterior, incrementando +1 até o último elemento: 

```
export enum DiaDaSemana { 
	Segunda = 18, 
	Terca, //19
	Quarta, //20
	Quinta, //...
	Sexta, 
	Sabado, 
	Domingo 
}
```

Para acessar um valor dentro de um enum , nós podemos utilizar uma das formas a seguir: 

```
let dia = DiaDaSemana[19]; // Terca 
let diaNumero = DiaDaSemana[dia]; // 19 
let diaString= DiaDaSemana["Segunda"]; // 18 

//Resultado: 
// Terca 
// 19 
// 18
```

##### Strings

Strings Diferente dos enums numéricos, os enums do tipo string precisam iniciar com um valor.

```
export enum DiaDaSemana { 
	Segunda = "Segunda-feira", 
	Terca = "Terça-feira", 
	Quarta = "Quarta-feira", 
	Quinta = "Quinta-feira", 
	Sexta = "Sexta-feira", 
	Sabado = "Sábado", 
	Domingo = "Domingo", 
}
```

Para acessar os valores de um enum do tipo string, basta utilizar uma das formas a seguir: 

```
console.log(DiaDaSemana.Sexta); //Sexta-feira 
console.log(DiaDaSemana['Sabado']); //Sábado 

Resultado: 
//Sexta-feira 
//Sábado
```

##### Heterogeneous

Os enums heterogeneous aceitam tanto strings quanto números:

```
export enum Heterogeneous { 
	Segunda = 'Segunda-feira', 
	Terca = 1, 
	Quarta, 
	Quinta, 
	Sexta, 
	Sabado, 
	Domingo = 18, 
}
```

E como acessar esses valores? A seguir você tem um exemplo demonstrando esse passo: 

```
console.log(Heterogeneous.Segunda); 
console.log(Heterogeneous['Segunda']); 

console.log(Heterogeneous['Terca']); 
console.log(Heterogeneous[1]); 

console.log(Heterogeneous['Quarta']); 
console.log(Heterogeneous['Quinta']);
console.log(Heterogeneous['Sexta']); 
console.log(Heterogeneous['Sabado']); 
console.log(Heterogeneous['Domingo']); 

Resultado: 
//Segunda-feira 
//Segunda-feira
//1 
//Terca 
//2 
//3 
//4 
//5 
//18
```

#### 2.10 Union

O union permite "combinar" um ou mais tipos, ele usa uma "|" para passar os tipos que ele pode aceitar:

Sintaxe: (tipo1 | tipo2)

Exemplo:

```
let exemploVariavel: (string | number); 
exemploVariavel = 123; 
console.log(exemploVariavel); //123 
exemploVariavel = "ABC"; 
console.log(exemploVariavel); //ABC
```

Podemos utilizar com quantos tipos quisermos.

Podemos também utilizar arrays com o union:

```
var arr: (number[] | string[]);
var i: number;
arr = [1,2,4];

for (i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}

arr = ["a", "b", "c"];

for (i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

Como parâmetro de funções: 

```
function deleteTeste(usuario: string | string[]) { 
	if (typeof usuario == "string") { 
		console.log(usuario, "deletado"); 
	} else { 
		var i; 
		for (i = 0; i < usuario.length; i++) { 
			console.log(usuario[i], "deletado"); 
		} 
	} 
}
Resultado: 
//função para deletar um registro 
//função para deletar mais de um registro
```

Nesse exemplo, nós podemos passar um registro para o nosso método deleteTeste ou passar um array de registros para serem deletados.

Note que nós temos uma nova palavra reservada chamada typeof no exemplo anterior, onde criamos uma função que recebe um tipo union como parâmetro. O typeof é um tipo de guarda, ou, no inglês, Type Guard, do JavaScript, que nós podemos utilizar desde a versão 1.4 do TypeScript.

Ele é utilizado em cenários onde precisamos verificar o tipo de um objeto dentro de um bloco condicional, como if ou o switch/case.

```
let x: string | number | boolean = 13; 
console.log(typeof(x))  //number
```

Além do typeof, temos outro tipo de guarda chamado instanceof. Ele tem a mesma funcionalidade do typeof, com a diferença de que o typeof retorna o tipo do objeto e o instanceof retorna um boolean.

```
interface Z { x(): string }

class A implements Z {
    x(): string {
        throw new Error("Method not implemented.");
    }
}

class B implements Z {
    x(): string {
        throw new Error("Method not implemented.");
    }
}

function exemploComInstanceof(paramentro: Z) {
    if (paramentro instanceof A) {
         console.log("Sou a classe A"); }
    else if (paramentro instanceof B) {
        console.log("Sou a classe B");
    }
}

exemploComInstanceof(new A());
```

#### 2.11 Any

Imagine o seguinte cenário: você está fazendo integração a uma API de terceiros e, mesmo que você tenha uma documentação dessa API, você não conhece 100% a estrutura do outro projeto. Esse é um dos cenários em que o any é mais utilizado.

```
let variavelAny: any = "Variável";
variavelAny = 34; 
variavelAny = true;
```

#### 2.12 Tipando funções

O TypeScript também nos permite tipar as nossas funções informando para o compilador qual é o tipo que elas devem retornar.

```
function calc(x: number, y: number): string { 
	return `resultado: ${x + y}`; 
}
```

##### Funções com tipos

No TypeScript, podemos tipar uma variável com o valor de uma função. Pegando o nosso exemplo anterior, vamos atribuir o valor da function calc a uma variável.

```
function calc(x: number, y: number): string { 
	return `resultado: ${x + y}`; 
}

let resultado : string;
resultado = calc(10,15);
console.log(resultado);

Resultado:
//resultado: 25
```

Caso você tente atribuir esse valor a uma variável de um tipo diferente de string, o compilador retornará a mensagem de erro:

```
function calc(x: number, y: number): string { 
	return `resultado: ${x + y}`; 
}

let resultado : number;
resultado = calc(10,15);
console.log(resultado);

Resultado:
//Type 'string' is not assignable to type 'number'.ts(2322)
```

#### 2.13 Void

