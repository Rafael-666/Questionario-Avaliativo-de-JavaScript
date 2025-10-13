### **Questionário Avaliativo de JavaScript – Fundamentos e DOM**

**Instruções:** Responda às seguintes perguntas de forma clara e descritiva. O objetivo é avaliar seu raciocínio e a profundidade do seu entendimento sobre os conceitos de JavaScript. Forneça exemplos de código sempre que solicitado.

---

#### **Seção 1: Fundamentos, Variáveis e Escopo**


**Pergunta 1:**
Imagine que você está desenvolvendo uma página de perfil de usuário. Você precisa armazenar três informações:
1.  O nome de usuário, que não mudará após o login.
2.  A idade do usuário, que pode ser atualizada por ele.
3.  Uma variável para verificar se o usuário é um administrador, mas que só precisa ser conhecida dentro de um bloco de código específico que checa permissões.

Qual palavra-chave (`const`, `let` ou `var`) você usaria para declarar cada uma dessas variáveis? Justifique sua escolha para cada uma, explicando os conceitos de escopo e imutabilidade que motivaram sua decisão.


**Pergunta 2:**
Analise o código abaixo. Sem executá-lo, explique linha por linha o que será impresso no console e por quê. Se alguma linha resultar em erro, explique qual é o erro e a razão pela qual ele ocorre, relacionando com o conceito de escopo de bloco.

```javascript
let statusGlobal = 'Online';

function verificarStatus() {
    console.log('1. Status dentro da função:', statusGlobal);

    let statusFuncao = 'Ocupado';
    if (true) {
        let statusBloco = 'Ausente';
        const idBloco = 123;
        console.log('2. Status dentro do bloco:', statusBloco);
        console.log('3. Status da função dentro do bloco:', statusFuncao);
    }

    console.log('4. Status do bloco fora do bloco:', statusBloco); // O que acontece aqui?
    console.log('5. ID do bloco fora do bloco:', idBloco); // E aqui?
}

verificarStatus();
```

---

#### **Seção 2: Tipos de Dados e Coerção**

**Pergunta 3:**
JavaScript possui dois operadores de igualdade: `==` (igualdade fraca) e `===` (igualdade estrita). Explique a diferença fundamental entre eles. Crie dois exemplos de código distintos:
1.  Um em que `==` retorna `true`, mas `===` retorna `false`.
2.  Um em que ambos retornam `true`.

Justifique o resultado de cada exemplo, explicando o papel da **coerção de tipo** na comparação.


**Pergunta 4:**
Você utiliza a função `prompt()` para pedir ao usuário que digite sua idade. Em seguida, você tenta adicionar 5 anos a essa idade para calcular qual será a idade dele no futuro.

```javascript
let idadeInput = prompt("Qual é a sua idade?");
let idadeDaqui5Anos = idadeInput + 5;
alert("Daqui a 5 anos, você terá: " + idadeDaqui5Anos);
```

Se um usuário digitar "25", qual será o resultado exibido no `alert`? Explique detalhadamente por que esse resultado acontece, considerando o tipo de dado retornado pela função `prompt()`. Em seguida, corrija o código para que o cálculo matemático seja feito corretamente.


**Pergunta 5:**
O operador `typeof` é usado para verificar o tipo de uma variável. No entanto, ele tem alguns comportamentos peculiares. Explique o que será retornado nos dois `console.log` abaixo e justifique o porquê de cada resultado, especialmente o primeiro, que é considerado uma "pegadinha" histórica do JavaScript.

```javascript
console.log(typeof null);
console.log(typeof ['maçã', 'banana', 'laranja']);
```
Considerando o resultado do segundo `console.log`, qual é a maneira correta e mais segura de verificar se uma variável é de fato um Array?

---

#### **Seção 3: Manipulação do DOM**

**Pergunta 6:**
Dado o HTML abaixo:
```html
<div id="principal">
    <p class="paragrafo">Primeiro parágrafo.</p>
    <p class="paragrafo">Segundo parágrafo.</p>
</div>
```
Escreva três linhas de código JavaScript para:
1. Selecionar o `div` usando seu ID.
2. Selecionar apenas o **primeiro** parágrafo usando sua classe.
3. Selecionar **todos** os parágrafos usando sua classe.

Após escrever o código, explique qual a principal diferença entre o que é retornado pelo método que você usou no passo 2 e o método que você usou no passo 3.


**Pergunta 7:**
Imagine que você tem um `div` vazio no seu HTML (`<div id="meu-div"></div>`) e a seguinte variável no seu JavaScript: `let meuHtml = "<strong>Texto em negrito</strong>";`.
a. O que aparecerá na tela se você executar `document.getElementById('meu-div').textContent = meuHtml;`?
b. E o que aparecerá se você executar `document.getElementById('meu-div').innerHTML = meuHtml;`?
c. Baseado na sua resposta, qual dos dois (`.textContent` ou `.innerHTML`) é mais seguro para exibir um texto simples que foi digitado por um usuário? Por quê?


**Pergunta 8:**
Existem duas maneiras principais de alterar a aparência de um elemento via JavaScript:
1.  Modificando diretamente a propriedade `style` (ex: `elemento.style.color = 'red';`).
2.  Adicionando ou removendo classes CSS (ex: `elemento.classList.add('classe-de-erro');`).

Qual dessas abordagens é considerada uma melhor prática para gerenciar estilos de forma organizada e por quê? Descreva pelo menos duas vantagens de usar o método `classList`.

---

#### **Seção 4: Lógica de Aplicação e Eventos**

**Pergunta 9:**
Baseado no exemplo do "Contador Interativo" visto em aula, imagine que você precisa adicionar uma nova funcionalidade: um botão "Salvar" que armazena o valor atual do contador no `localStorage` do navegador, e um botão "Carregar" que recupera esse valor e atualiza o display. Descreva os passos e o código JavaScript que você usaria para implementar essas duas funções, `salvarContador()` e `carregarContador()`.


**Pergunta 10:**
Os slides da Aula 6 introduziram o conceito de AJAX para fazer requisições a uma API, usando jQuery como ferramenta. Em suas próprias palavras, explique qual problema fundamental o AJAX resolve no desenvolvimento web. Descreva a experiência de um usuário em um site que **não usa** AJAX versus um que **usa** AJAX ao, por exemplo, submeter um formulário de contato.

---

#### **Desafio Prático**

**Pergunta 11:**
Seu desafio é preencher um "Card de Produto" com dados de um objeto JavaScript.

**1. Dados Fornecidos:**
Você recebe o objeto JavaScript com os dados do produto:
```javascript
const produto = {
    nome: "Fone de Ouvido Bluetooth",
    preco: 249.90,
    imagem: "https://exemplo.com/fone.jpg",
    disponivel: true
};
```
E a estrutura HTML do card, já pronta no seu `index.html`:
```html
<div id="card-produto">
    <img id="card-imagem" src="" alt="Imagem do Produto">
    <h3 id="card-nome"></h3>
    <p>Preço: R$ <span id="card-preco"></span></p>
    <p>Status: <span id="card-status"></span></p>
    <button id="card-botao">Adicionar ao Carrinho</button>
</div>
```

**2. Sua Tarefa:**
a. Escreva uma função JavaScript chamada `renderizarProduto(produto)` que receba o objeto acima e use manipulação do DOM (`getElementById`, `.textContent`, `.src`, etc.) para preencher corretamente a imagem, o nome, o preço e o status no card HTML. O status deve ser "Disponível" se `produto.disponivel` for `true`, e "Indisponível" se for `false`.

b. Usando `addEventListener`, faça com que o botão "Adicionar ao Carrinho" (`card-botao`), ao ser clicado, exiba um `alert` com a mensagem: "Produto [nome do produto] adicionado ao carrinho!".

(Você só precisa escrever o código JavaScript para as partes a e b).