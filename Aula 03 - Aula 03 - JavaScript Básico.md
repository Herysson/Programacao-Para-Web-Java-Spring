# Aula 03 - JavaScript (JS)

## Introdução ao JavaScript

O **JavaScript** (frequentemente abreviado como JS) é uma linguagem de programação interpretada de alto nível, caracterizada por ser dinâmica e fracamente tipada. Juntamente com HTML e CSS, o JavaScript é uma das três principais tecnologias da World Wide Web.

Enquanto o HTML estrutura a página e o CSS a estiliza, o JavaScript é o responsável por adicionar **interatividade**, **comportamento dinâmico** e **lógica** às páginas web.

Com JS, você pode:
* Alterar o conteúdo e os estilos de elementos HTML em tempo real.
* Reagir a eventos do usuário (como cliques, digitação, rolagem da página).
* Validar dados de formulários antes de enviá-los ao servidor.
* Buscar novos dados sem recarregar a página (AJAX/Fetch).


## Como Inserir o JavaScript no HTML

Assim como o CSS, existem três maneiras principais de adicionar JavaScript a um documento HTML.

### 1. JavaScript Externo

O código JavaScript é escrito em um arquivo separado com a extensão `.js`. Esse arquivo é então referenciado no HTML usando a tag `<script>` com o atributo `src`. Geralmente, essa tag é colocada no final do `<body>` (logo antes da tag de fechamento `</body>`) para não bloquear o carregamento do restante da página.

**HTML:**
```html
<body>
  <script src="script.js"></script>
</body>
```

**Arquivo `script.js`:**
```javascript
alert("Olá! Este é um script externo.");
```

**Vantagens:**
* Separa a lógica (JS) da estrutura (HTML).
* Permite a reutilização de código em várias páginas.
* Facilita a manutenção e colaboração em equipe.
* É a **prática mais recomendada** para projetos reais.

### 2. JavaScript Interno

O código é inserido diretamente no arquivo HTML, dentro das tags `<script>`, que podem ficar no `<head>` ou no `<body>`.

```html
<body>
  <script>
    console.log("Este é um script interno.");
  </script>
</body>
```

### 3. JavaScript Inline

O código JS é colocado diretamente nos atributos de eventos dos elementos HTML.

```html
<button onclick="alert('Botão clicado!')">Clique Aqui</button>
```

**Desvantagens:**
* Mistura estrutura com comportamento, dificultando a leitura.
* Não reutilizável e complexo para dar manutenção.
* Deve ser **evitado em projetos maiores**.

## Sintaxe e Variáveis

Variáveis são "caixas" (espaços de memória) onde armazenamos dados que serão manipulados pelo nosso programa.

No JavaScript moderno (ES6+), usamos `let` e `const` para declarar variáveis. O uso do antigo `var` tornou-se obsoleto na maioria dos casos devido a problemas com o escopo de bloco.

### Declarando Variáveis

* **`let`**: Usado para variáveis cujo valor pode mudar (ser reatribuído) ao longo do tempo.
* **`const`**: Usado para constantes; o valor atribuído na declaração não pode ser alterado posteriormente.

```javascript
let nome = "João da Silva"; // String (texto)
let idade = 25;           // Number (número)
let buscandoEmprego = true; // Boolean (verdadeiro/falso)

const cpf = "123.456.789-00"; // Constante, não pode mudar
```

### Tipos de Dados Básicos

| Tipo | Descrição | Exemplo |
| :--- | :--- | :--- |
| **String** | Sequência de caracteres (texto), sempre entre aspas simples, duplas ou crases. | `"Desenvolvedor Web"` |
| **Number** | Números inteiros ou decimais. | `2026` ou `3.14` |
| **Boolean** | Valor lógico: verdadeiro (`true`) ou falso (`false`). | `true` |
| **Array** | Lista ordenada de valores. | `["HTML", "CSS", "JS"]` |
| **Object** | Coleção de propriedades e valores (pares chave-valor). | `{ nome: "Ana", idade: 30 }` |

### Exercício Prático

**Objetivo:** Começar a interagir com o JavaScript e visualizar informações de dados que estarão no currículo.

**Instruções:**
1. Crie um arquivo chamado `script.js` na mesma pasta do seu arquivo de currículo.
2. No seu arquivo HTML, vincule o script externo no final do `<body>` com a tag `<script src="script.js"></script>`.
3. No arquivo `script.js`, declare variáveis (usando `let` e `const`) para armazenar:
   * Seu nome.
   * Sua idade.
   * Um array (lista) com três habilidades técnicas suas.
4. Utilize a função `console.log()` para imprimir essas variáveis.
5. Abra seu currículo no navegador, aperte `F12` (ou clique com o botão direito e vá em "Inspecionar") e acesse a aba **Console** para ver o resultado da execução do seu script.

---

## Estruturas de Controle (Condicionais)

As estruturas de controle permitem que o código tome decisões e execute blocos de código diferentes com base em certas condições lógicas.

### `if` e `else`

A estrutura mais comum para tomada de decisão é o `if/else` (se/senão).

```javascript
let anosExperiencia = 3;

if (anosExperiencia > 5) {
  console.log("Perfil Sênior");
} else if (anosExperiencia >= 2) {
  console.log("Perfil Pleno");
} else {
  console.log("Perfil Júnior");
}
```

---

## Funções

Funções são blocos de código projetados para realizar uma tarefa específica. Uma função é executada quando "chamada" (invocada).
Elas evitam a repetição de código e mantêm o projeto muito mais organizado e modular.

### Declarando e Chamando Funções

```javascript
// Declaração da função
function saudarUsuario(nomeUsuario) {
  alert("Bem-vindo ao currículo de " + nomeUsuario + "!");
}

// Chamando a função
saudarUsuario("Maria");
```

As funções também podem **retornar** um valor para quem as chamou usando a palavra-chave `return`.

```javascript
function calcularAnoNascimento(idadeAtual) {
  const anoAtual = 2026;
  return anoAtual - idadeAtual;
}

let ano = calcularAnoNascimento(25);
console.log("Você nasceu em " + ano);
```

---

## O DOM (Document Object Model)

Quando uma página web é carregada, o navegador cria o **Document Object Model** da página. É uma representação estruturada (em formato de árvore hierárquica) de todos os elementos HTML presentes no documento.


Através do DOM, o JavaScript consegue acessar, adicionar, alterar e remover elementos, atributos HTML e propriedades CSS.

### 1. Selecionando Elementos

Para manipular um elemento com JS, primeiro precisamos "encontrá-lo" no HTML.

| Método | Descrição | Exemplo |
| :--- | :--- | :--- |
| `getElementById()` | Busca um elemento pelo seu atributo `id`. | `document.getElementById("titulo")` |
| `querySelector()` | Busca o primeiro elemento que corresponde a um seletor CSS (tag, `.classe`, `#id`). | `document.querySelector(".minha-classe")` |
| `querySelectorAll()` | Retorna uma NodeList (lista) com todos os elementos que correspondem a um seletor CSS. | `document.querySelectorAll("p")` |

### 2. Alterando o Conteúdo e os Estilos

Uma vez que o elemento está selecionado e armazenado em uma variável, podemos modificar seu conteúdo ou aparência.

```javascript
// Seleciona um elemento com id="profissao" no HTML
let profissaoElemento = document.getElementById("profissao");

// Altera o texto visível desse elemento
profissaoElemento.textContent = "Desenvolvedor Front-end Especialista";

// Altera o estilo CSS diretamente via JavaScript
profissaoElemento.style.color = "blue";
profissaoElemento.style.fontSize = "24px";
```

---

## Eventos

Eventos são ações que ocorrem em elementos HTML (geralmente causadas pela interação do usuário ou pelo próprio ciclo de vida do navegador). O JavaScript pode "escutar" esses eventos e reagir a eles executando funções.

Exemplos de eventos muito comuns:
* `click`: O usuário clica em um elemento.
* `mouseover` / `mouseout`: O mouse passa por cima ou sai de um elemento.
* `submit`: Um formulário é enviado.
* `keydown`: Uma tecla do teclado é pressionada.

### Adicionando EventListeners (Ouvintes de Eventos)

A forma moderna e mais flexível de lidar com eventos é usar o método `addEventListener()`.

**HTML:**
```html
<button id="btnContato">Ver E-mail de Contato</button>
<p id="emailContato" style="display: none;">contato@meuemail.com</p>
```

**JavaScript:**
```javascript
// 1. Seleciona os elementos necessários
const botao = document.getElementById("btnContato");
const emailParagrafo = document.getElementById("emailContato");

// 2. Cria a função que será executada quando o evento ocorrer
function mostrarEmail() {
  emailParagrafo.style.display = "block"; // Torna o parágrafo visível
  botao.style.display = "none";           // Oculta o botão
}

// 3. Adiciona o ouvinte de evento (o tipo do evento e a função a ser executada)
botao.addEventListener("click", mostrarEmail);
```

### Exercício Prático

**Objetivo:** Adicionar interatividade básica ao currículo usando manipulação de DOM e escuta de Eventos.

**Instruções:**
1. No arquivo HTML do seu currículo, localize (ou crie) a seção de "Habilidades" (Skills).
2. Adicione um botão no final dessa seção com o texto "Mostrar Habilidade Oculta" e atribua a ele o atributo `id="btnHabilidade"`.
3. Adicione um item à sua lista de habilidades (`<li>`) com uma característica "secreta" ou bônus (ex: "Trabalho bem sob pressão", "Excelente fotógrafo de eventos da empresa"). Defina para esse item o `id="habilidadeOculta"` e aplique a ele o estilo CSS in-line `style="display: none;"` para que comece escondido.
4. No seu arquivo `script.js`, crie um código completo que selecione o botão e o item da lista, escute o `click` no botão e, ao clicar, mude a propriedade `display` da habilidade para `list-item` (ou `block`).

---

## Validação de Formulários com JavaScript

No material anterior, vimos como criar e estilizar um formulário de contato. Embora o HTML5 possua validações nativas (como o atributo `required`), o JavaScript permite validações muito mais complexas, customizadas e capazes de exibir feedbacks visuais sem a necessidade de recarregar a página.

### Exemplo de Validação Simples

Vamos interceptar o evento `submit` do formulário para impedir que ele seja efetivamente enviado caso a mensagem digitada seja muito curta.

**HTML:**
```html
<form id="formContato">
  <textarea id="mensagem" name="mensagem" placeholder="Digite sua mensagem"></textarea>
  <p id="erroMensagem" style="color: red; display: none;">A mensagem deve ter pelo menos 10 caracteres.</p>
  
  <input type="submit" value="Enviar">
</form>
```

**JavaScript:**
```javascript
const formulario = document.getElementById("formContato");
const campoMensagem = document.getElementById("mensagem");
const erroMensagem = document.getElementById("erroMensagem");

formulario.addEventListener("submit", function(evento) {
  // Pega o valor (o texto) digitado na textarea
  let texto = campoMensagem.value;

  // Verifica se o texto tem menos de 10 caracteres
  if (texto.length < 10) {
    // 1. Impede o envio real do formulário (que recarregaria a página)
    evento.preventDefault(); 
    
    // 2. Mostra a mensagem de erro que estava oculta
    erroMensagem.style.display = "block"; 
    
    // 3. Aplica uma borda vermelha ao campo para chamar a atenção
    campoMensagem.style.border = "2px solid red"; 
  } else {
    // Esconde o erro e restaura a borda caso o usuário tenha corrigido
    erroMensagem.style.display = "none";
    campoMensagem.style.border = "1px solid #ccc";
    alert("Formulário validado e pronto para envio real!");
  }
});
```

---

## Atividade Final

**Objetivo:** Consolidar os conceitos de JavaScript manipulando ativamente o formulário criado nas aulas anteriores do projeto do currículo.

**Instruções:**
1. Abra o arquivo HTML do seu currículo que contém o formulário de contato.
2. Certifique-se de que a tag `<form>` tenha um `id="meuFormulario"`.
3. Garanta que o campo "Nome" tenha um `id="nome"` e o campo "Email" tenha um `id="email"`.
4. No arquivo `script.js`, escreva um código para selecionar os campos e escutar o evento `submit` do formulário inteiro.
5. Use `evento.preventDefault()` logo no início da sua função para impedir o recarregamento da página durante os testes.
6. Crie uma lógica de validação com `if/else` que garanta:
   * Que o campo "Nome" não esteja totalmente vazio.
   * Que o campo "Email" contenha o caractere `@` (Dica de pesquisa: procure sobre o método `.includes('@')` em strings no JavaScript).
7. Se o usuário cometer um erro, exiba mensagens de aviso usando `alert()` (ou, como desafio extra, modificando o DOM para exibir textos em vermelho abaixo do campo que falhou).
8. Se tudo estiver correto (dados válidos), limpe os campos simulando o envio (ex: `document.getElementById('nome').value = "";`) e exiba um `alert()` amigável informando "Mensagem de [Nome do Usuário] enviada com sucesso!".

---

## Referências

* FLANAGAN, David. *JavaScript: O Guia Definitivo*. 6. ed. Porto Alegre: Bookman, 2013.
* SILVA, Maurício Samy. *JavaScript: guia do programador*. São Paulo: Novatec Editora, 2010.
* MDN Web Docs. *JavaScript*. Mozilla. Disponível em: [https://developer.mozilla.org/pt-BR/docs/Web/JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript).
* W3Schools. *JavaScript Tutorial*. Disponível em: [https://www.w3schools.com/js/](https://www.w3schools.com/js/).
