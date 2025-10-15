# Respostas
1. Resposta 1:
- const para o nome de usuário para ser fixo, se não sempre seria criado pelo usuário a cada login(Conceito de imutabilidade) .

- let para idade pois ninguem tem idade fixa sempre muda a cada ano conforme a data de nascismento do usuário, teria que ter uma função para fazer a soma de +1 sempre que chegar na data (let me pareceu ser mais adequado pois ela só conseguer ser lida no contexto do bloco em que está evitando bugs ja o var consegue ser redeclarado então me parece mais dificil de se ter o controle em código extensos, conceito de escopo).

- let para checar a permissão (let só consegue ser lido dentro do contexto do bloco em que está então acho que seria ideal para essa função para evitar bugs, conceito de escopo).

2. Resposta 2:

```js
let statusGlobal = 'Online';// variavel com escopo global pois está no topo do codigo

function verificarStatus() {
    console.log('1. Status dentro da função:', statusGlobal);//mostra o online

    let statusFuncao = 'Ocupado';
    if (true) {
        let statusBloco = 'Ausente';
        const idBloco = 123;
        console.log('2. Status dentro do bloco:', statusBloco);// mostra o ausente
        console.log('3. Status da função dentro do bloco:', statusFuncao);//mostra o ocupado
    }

    console.log('4. Status do bloco fora do bloco:', statusBloco); // erro de referencia pois o let esta no bloco do if fora do escopo do resto
    console.log('5. ID do bloco fora do bloco:', idBloco); // erro de referencia pois esta no bloco do if
}

verificarStatus();
```
3. Resposta 3:
- quando se utiliza o == para comparar valores o js tenta tranformar as variaveis no mesmo tipo para depois fazer a comparação dos valores

- EXEMPLO:
```js
let a = 10;
let b = '10'
if (a == b) {
  console.log('São iguais!');
} else {
  console.log('São diferentes!');
}
```
- quando se utiliza o === ele compara e não tenta transformar no mesmo tipo mas para se ter a comparação com resultado de true as variaveis tem que ser do mesmo tipo e os valores iguais.

- EXEMPLO:
```js
let a = 10;
let b = '10';

if (a === b) {
  console.log('São iguais!');
} else {
  console.log('São diferentes!');
}

 let c = 5;
 let d = 5;

 if (c === d) {
  console.log('São iguais!');
} else {
  console.log('São diferentes!');
}
```

4. Resposta 4:
```js
let idadeInput = prompt("Qual é a sua idade?");
let idadeDaqui5Anos = idadeInput + 5;
alert("Daqui a 5 anos, você terá: " + idadeDaqui5Anos);
```
- o alert vai mostrar o numero 205 pois o prompt recebe uma string e quando se tem uma string em alguma das variaveis o operador + vai concatenar em vez de somar para corrigir este erro a variavel idadeInput deveria ter sido convertida para o tipo number.

- Código com a correção
```js
let idadeInput = prompt("Qual é a sua idade?");
let idadeDaqui5Anos = Number(idadeInput) + 5;
alert("Daqui a 5 anos, você terá: " + idadeDaqui5Anos);
```

5. Resposta 5:
- o primeiro resultado é um bug um erro que veio desde da implementação do JS não foi corrijido até hoje pois isso iria quebrar muitos sistemas.
- o segundo é porque internamente um array é um objeto o jeito correto de se verificar um array é com o comando Array.isArray(valor).

6. Resposta 6:
- Código criado
```js
const divPrincipal = document.getElementById('principal');
const primeiroParagrafo = document.querySelector('.paragrafo');
const todosParagrafos = document.querySelectorAll('.paragrafo');`
```
- no método 2 o querySelector vai retornar o primeiro quer for compátivel 
- no método 3 o querySelectorAll retorna todos que forem da mesma class

7. Resposta 7:
- a- vai aparecer "<strong>Texto em negrito</strong>" o textContent pega o conteúdo inteiro ele não interpreta o html apenas exibe como texto puro
- b- vai mostrar "**Texto em negrito**" pois o inneHTML consegue interpretar as tags inseridas assim alterando o texto 
- c- o mais seguro é o textContent pois caso um usuário malicioso queira inserir algum script ele não sera interpretado

8. Resposta 8:
-o ClassList é melhor pois é facil de ter o controle já que vai estar em um arquivo CSS e não no JS caso o código fique muito extenso é dificil de se dar manuntenção e reaproveitar estilos com o comando Style, e o classList consegue aplicar uma formatação de estilo especifico para os elementos da mesmas classe

9. Resposta 9:
- Fiz o código pensando que a parte do HTML já está pronta.
Primeiro eu crio as variáveis que vão atuar como botões e uma para registrar o contador. Depois, a função para salvar e outra para carregar.
Para salvar eu uso o comando localStorage para armazenar no navegador a informação. No carregar, primeiro eu verifico se há algum valor armazenado, se houver ele entra em um if onde vai carregar o valor e atualizar o display. Caso não tenha nada salvo, ele exibirá uma mensagem informando que nenhum valor salvo foi encontrado. E para saber qual botão foi clicado, eu uso o addEventListener em cada um dos botões, com suas respectivas funções.
```js
const botaoSalvar = document.getElementById("botaoSalvar");
const botaoCarregar = document.getElementById("botaoCarregar");

let contador = 0;

function salvarContador(){
  localStorage,setItem('contador', contador);
  alert("Valor salvo!!");
}

function carregarContador(){
const valorSalvo = localStorage.getItem("contador");
    if (valorSalvo !== null) {
      contador = parseInt(valorSalvo);
      atualizarDisplay();
    } else {
      alert("Nenhum valor salvo foi encontrado.");
    }
  
}
 botaoSalvar.addEventListener("click", salvarContador);
  botaoCarregar.addEventListener("click", carregarContador);

```
10. Resposta 10:
- Antes do AJAX, toda vez que o usuário fazia uma ação que dependia do servidor o navegador precisava recarregar a página inteira para mostrar  o novo conteúdo. Esperas mais longas (tela piscando ou recarregando), Perda de informações já digitadas, Uma experiência menos fluida e mais  lenta. O AJAX resolve exatamente esse problema, ele permite enviar e receber dados do servidor sem recarregar a página inteira, tornando o site mais rápido, dinâmico e responsivo.

- EXEMPLO DE COMO SERIA UM SITE SEM AJAX:
1- O usuário preenche nome, e-mail e mensagem.
2- Clica em “Enviar”.
3- O navegador envia os dados para o servidor.
4- A página recarrega completamente.
5- O usuário vê uma nova página com a mensagem “Formulário enviado com sucesso”.

- O resultado disso e uma pagina lenta caso de algo errado e recarregue a pagina o usuario tem que preencher tudo de novo.

- EXEMPLO DE COMO SERIA UM SITE COM AJAX:
1- O usuário preenche o formulário.
2- Ao clicar em “Enviar”, o JavaScript (via jQuery) envia os dados em segundo plano, usando $.ajax() ou $.post().
3- servidor responde (ex: “Mensagem enviada com sucesso!”).
4- O JavaScript atualiza apenas uma parte da página, mostrando a mensagem — sem recarregar nada.

- O resultado disso é a página continua a mesma caso de algum problema, a resposta aparece quase instantaneamente e a experiência do usuário é mais fluida.

11. Resposta 11:
```js
const produto = {
    nome: "Fone de Ouvido Bluetooth",
    preco: 249.90,
    imagem: "https://exemplo.com/fone.jpg",
    disponivel: true
};
function renderizarProduto(produto) {
   const imagem = document.getElementById("card-imagem");
  const nome = document.getElementById("card-nome");
  const preco = document.getElementById("card-preco");
  const status = document.getElementById("card-status");

  imagem.src = produto.imagem;
  imagem.alt = produto.nome;
  nome.textContent = produto.nome;
  preco.textContent = produto.preco.toFixed(2);
  status.textContent = produto.disponivel ? "Disponível" : "Indisponível";
}

renderizarProduto(produto);

  const botao = document.getElementById("card-botao");
botao.addEventListener("click", function() {
  alert(`Produto ${produto.nome} adicionado ao carrinho!`);
});
```