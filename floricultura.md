# Tutorial: Lojinha de Flores 
### Construindo um site com HTML5 e CSS

Neste tutorial você vai construir, passo a passo, o site de uma floricultura fictícia chamada **Lojinha de Flores**. Ao final você terá uma página com cabeçalho, menu de navegação, vitrine de produtos, formulário de contato e rodapé, e ela vai se adaptar a telas de computador e de celular.

Vamos usar **apenas HTML5 e CSS**, sem JavaScript.

---

## Sumário

1. [Objetivos de aprendizagem](#1-objetivos-de-aprendizagem)
2. [O que você vai precisar](#2-o-que-você-vai-precisar)
3. [O que vamos construir](#3-o-que-vamos-construir)
4. [Parte 1: A estrutura com HTML](#4-parte-1-a-estrutura-com-html)
5. [Parte 2: A aparência com CSS](#5-parte-2-a-aparência-com-css)
6. [Parte 3: Testando e validando](#6-parte-3-testando-e-validando)
7. [Resumo: tags e propriedades usadas](#7-resumo-tags-e-propriedades-usadas)
8. [Desafio: Vitrine de Promoções](#8-desafio-vitrine-de-promoções)
9. [Referências](#9-referências)

---

## 1. Objetivos de aprendizagem

Ao terminar este tutorial, você será capaz de:

- explicar a diferença entre **estrutura** (HTML) e **apresentação** (CSS);
- montar a estrutura básica de um documento HTML5;
- usar **tags semânticas** (`header`, `nav`, `main`, `section`, `article`, `footer`);
- criar links internos (âncoras), listas, imagens e formulários;
- escrever regras CSS usando seletores de **tipo**, **classe**, **descendente**, **agrupamento** e **pseudo-classes**;
- entender o **Box Model** (margin, border, padding, content);
- organizar elementos com **Flexbox** e **CSS Grid**;
- adaptar a página para celulares com **media queries**.



## 2. O que você vai precisar

| Ferramenta | Para quê |
|---|---|
| Um editor de código (ex.: [VS Code](https://code.visualstudio.com/)) | Escrever os arquivos `.html` e `.css` |
| Um navegador (Chrome, Firefox, Edge...) | Abrir e testar a página |
| *(Opcional)* Extensão **Live Server** do VS Code | Recarregar a página automaticamente a cada alteração |

> 💡 Também é possível fazer tudo em editores online, como o [CodePen](https://codepen.io/) ou o [Replit](https://replit.com/).

O código completo e pronto deste tutorial está na pasta [`template/`](template/). Use-o para conferir o seu trabalho, mas **tente digitar o código você mesmo**, porque é assim que se aprende.



## 3. O que vamos construir

A página terá o seguinte esqueleto:

```
┌──────────────────────────────────────────────────────────┐
│ HEADER  Lojinha de Flores   Início Sobre Produtos Contato│  ← <header> + <nav>
├──────────────────────────────────────────────────────────┤
│ MAIN                                                     │
│   ┌── SECTION "Sobre Nós" ─────────────────────────────┐ │
│   │ texto de apresentação                              │ │
│   └────────────────────────────────────────────────────┘ │
│   ┌── SECTION "Nossos Produtos" ───────────────────────┐ │
│   │ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐        │ │
│   │ │ imagem │ │ imagem │ │ imagem │ │ imagem │        │ │  ← cartões <article>
│   │ │ nome   │ │ nome   │ │ nome   │ │ nome   │        │ │     organizados com
│   │ │ preço  │ │ preço  │ │ preço  │ │ preço  │        │ │     CSS Grid
│   │ └────────┘ └────────┘ └────────┘ └────────┘        │ │
│   └────────────────────────────────────────────────────┘ │
│   ┌── SECTION "Entre em Contato" ──────────────────────┐ │
│   │            [ formulário de contato ]               │ │
│   └────────────────────────────────────────────────────┘ │
├──────────────────────────────────────────────────────────┤
│ FOOTER            © 2026 Lojinha de Flores               │
└──────────────────────────────────────────────────────────┘
```

### Estrutura de pastas

Crie uma pasta para o projeto com esta organização:

```
lojinha-de-flores/
├── index.html      ← estrutura e conteúdo da página
├── style.css       ← aparência da página
└── img/            ← imagens dos produtos
    ├── violeta.svg
    ├── rosa.svg
    ├── girassol.svg
    └── tulipa.svg
```

Copie as imagens da pasta [`template/img/`](template/img/) para a sua pasta `img/`. Se quiser, troque-as por fotos reais. Bancos como [Unsplash](https://unsplash.com/) e [Pexels](https://www.pexels.com/) oferecem imagens gratuitas, e você deve sempre respeitar a licença de uso delas.

> 💡 **Por que `index.html`?** Por convenção, servidores web procuram um arquivo chamado `index.html` para exibir como página inicial de uma pasta.


## 4. Parte 1: A estrutura com HTML

O **HTML** (*HyperText Markup Language*) é uma linguagem de **marcação**: ela não "programa" nada, apenas **descreve o significado** de cada parte do conteúdo ("isto é um título", "isto é um parágrafo", "isto é um menu"). O navegador lê essas marcações e monta a página.

Uma marcação é feita com **tags**:

```html
<p class="preco">R$ 24,90</p>
│ │ └────┬────┘ └───┬───┘ └┬┘
│ │   atributo   conteúdo  tag de fechamento
│ └─ nome da tag
└─ tag de abertura: <p ...>
```

Algumas tags não têm conteúdo nem fechamento, como `<img>`, `<input>`, `<meta>` e `<link>`. Elas são chamadas de **elementos vazios**.

📚 **Leia mais:** [MDN: Introdução ao HTML](https://developer.mozilla.org/pt-BR/docs/Learn/HTML/Introduction_to_HTML/Getting_started) · [W3Schools: HTML Introduction](https://www.w3schools.com/html/html_intro.asp)

### Passo 1: Estrutura básica do documento

Crie o arquivo `index.html` e digite:

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Lojinha de Flores: flores frescas, buquês e arranjos para todas as ocasiões.">
    <title>Lojinha de Flores</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

</body>
</html>
```

**O que cada linha faz:**

| Código | Para que serve |
|---|---|
| `<!DOCTYPE html>` | Avisa ao navegador que o documento é **HTML5**. Deve ser sempre a primeira linha. |
| `<html lang="pt-br">` | Elemento **raiz**: tudo fica dentro dele. O atributo `lang` informa o idioma, o que ajuda leitores de tela, tradutores e buscadores. |
| `<head>` | Guarda **informações sobre a página** (metadados). Nada aqui aparece no corpo da página. |
| `<meta charset="UTF-8">` | Define a codificação de caracteres. O **UTF-8** exibe corretamente acentos (ç, ã, é) e até emojis 🌷. |
| `<meta name="viewport" ...>` | Faz o celular usar a **largura real da tela** em vez de "encolher" a página. Essencial para sites responsivos. |
| `<meta name="description" ...>` | Resumo da página, usado por buscadores como o Google. |
| `<title>` | Texto que aparece na **aba do navegador** e nos favoritos. |
| `<link rel="stylesheet" href="style.css">` | **Liga o arquivo CSS** ao HTML. O `href` indica o caminho do arquivo. |
| `<body>` | Guarda **todo o conteúdo visível** da página. |

> ⚠️ **Atenção ao nome do arquivo!** O `href="style.css"` precisa ter exatamente o mesmo nome do arquivo que você vai criar, inclusive letras maiúsculas e minúsculas. Um erro comum é criar `styles.css` e escrever `style.css` no link. Nesse caso o CSS simplesmente não é aplicado.

📚 **Leia mais:**
- `<!DOCTYPE>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Glossary/Doctype) · [W3Schools](https://www.w3schools.com/tags/tag_doctype.asp)
- `<head>` e metadados: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML) · [W3Schools](https://www.w3schools.com/html/html_head.asp)
- Charset UTF-8: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/meta#attr-charset) · [W3Schools](https://www.w3schools.com/html/html_charset.asp)
- Viewport: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Viewport_meta_tag) · [W3Schools](https://www.w3schools.com/css/css_rwd_viewport.asp)
- `<link>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/link) · [W3Schools](https://www.w3schools.com/tags/tag_link.asp)


### Passo 2: HTML semântico, pensando na estrutura

Antes do HTML5, os sites eram feitos quase só com `<div>`, uma "caixa genérica" sem significado. O HTML5 trouxe **tags semânticas**, cujo nome já diz o que o conteúdo **é**:

| Tag | Significado |
|---|---|
| `<header>` | Cabeçalho (logo, título, menu) |
| `<nav>` | Bloco de links de navegação |
| `<main>` | Conteúdo principal (só pode haver **um** por página) |
| `<section>` | Seção temática, normalmente com um título |
| `<article>` | Conteúdo independente, que faria sentido sozinho (um post, um cartão de produto) |
| `<footer>` | Rodapé |

**Por que isso importa?**
1. **Acessibilidade:** leitores de tela usados por pessoas cegas conseguem "pular" direto para o menu ou para o conteúdo principal.
2. **SEO:** buscadores entendem melhor a página.
3. **Legibilidade:** o código fica mais fácil de ler e manter.

📚 **Leia mais:** [MDN: Semântica em HTML](https://developer.mozilla.org/pt-BR/docs/Glossary/Semantics#sem%C3%A2ntica_em_html) · [W3Schools: HTML Semantic Elements](https://www.w3schools.com/html/html5_semantic_elements.asp)


### Passo 3: Cabeçalho e menu de navegação

Dentro do `<body>`, adicione:

```html
<!-- Cabeçalho: nome da loja e menu de navegação -->
<header id="inicio">
    <h1>🌷 Lojinha de Flores</h1>
    <nav>
        <ul>
            <li><a href="#inicio">Início</a></li>
            <li><a href="#sobre">Sobre</a></li>
            <li><a href="#produtos">Produtos</a></li>
            <li><a href="#contato">Contato</a></li>
        </ul>
    </nav>
</header>
```

**O que está acontecendo:**

- `<!-- ... -->` é um **comentário**. O navegador o ignora, e ele serve para deixar anotações no código.
- `<h1>` é o **título principal** da página. Existem títulos de `<h1>` (mais importante) até `<h6>`. Use apenas **um `<h1>`** por página e não pule níveis (depois de `h1` vem `h2`, depois `h3`...).
- `<nav>` indica que ali há um **menu de navegação**.
- `<ul>` (*unordered list*) cria uma **lista não ordenada**, e cada `<li>` (*list item*) é um item. Menus são, semanticamente, listas de links.
- `<a>` (*anchor*) cria um **link**. O atributo `href` indica o destino.

#### Links internos (âncoras)

Repare que os links usam `href="#sobre"`, `href="#produtos"`, e assim por diante. O `#` seguido de um nome faz o navegador **rolar até o elemento que tem aquele `id`**. Por isso colocamos `id="inicio"` no `<header>`, e mais adiante vamos colocar `id="sobre"`, `id="produtos"` e `id="contato"` nas seções.

> 📝 O valor de um `id` deve ser **único** na página: dois elementos nunca podem ter o mesmo `id`.

📚 **Leia mais:**
- `<header>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/header) · [W3Schools](https://www.w3schools.com/tags/tag_header.asp)
- Títulos `<h1>`–`<h6>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/Heading_Elements) · [W3Schools](https://www.w3schools.com/html/html_headings.asp)
- `<nav>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/nav) · [W3Schools](https://www.w3schools.com/tags/tag_nav.asp)
- Listas `<ul>` / `<li>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/ul) · [W3Schools](https://www.w3schools.com/html/html_lists.asp)
- Links `<a>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/a) · [W3Schools](https://www.w3schools.com/html/html_links.asp)
- Atributo `id`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Global_attributes/id) · [W3Schools](https://www.w3schools.com/html/html_id.asp)
- Comentários: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/HTML/Introduction_to_HTML/Getting_started#coment%C3%A1rios_html) · [W3Schools](https://www.w3schools.com/html/html_comments.asp)


### Passo 4: Conteúdo principal e seção "Sobre Nós"

Logo após o `</header>`, adicione:

```html
<!-- Conteúdo principal da página -->
<main>

    <!-- Seção 1: apresentação da loja -->
    <section id="sobre">
        <h2>Sobre Nós</h2>
        <p>
            A <strong>Lojinha de Flores</strong> nasceu do amor de uma família pelas plantas.
            Cultivamos e selecionamos flores frescas todos os dias para transformar
            momentos especiais em lembranças inesquecíveis.
        </p>
        <p>
            Trabalhamos com buquês, arranjos e vasos para presentes, aniversários,
            casamentos e decoração de ambientes.
        </p>
    </section>

    <!-- As próximas seções entram aqui -->

</main>
```

- `<main>` envolve o **conteúdo principal**, ou seja, tudo o que não é cabeçalho nem rodapé.
- `<section>` agrupa um **assunto**. Cada seção tem seu próprio título `<h2>`.
- `<p>` é um **parágrafo**.
- `<strong>` marca um texto de **forte importância**, e o navegador o exibe em negrito.

> 💡 No HTML, quebras de linha e espaços extras dentro do texto são ignorados. O parágrafo acima aparece como um texto corrido, mesmo que no código ele esteja em várias linhas.

📚 **Leia mais:**
- `<main>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/main) · [W3Schools](https://www.w3schools.com/tags/tag_main.asp)
- `<section>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/section) · [W3Schools](https://www.w3schools.com/tags/tag_section.asp)
- `<p>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/p) · [W3Schools](https://www.w3schools.com/html/html_paragraphs.asp)
- `<strong>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/strong) · [W3Schools](https://www.w3schools.com/tags/tag_strong.asp)

---

### Passo 5: Vitrine de produtos

Substitua o comentário `<!-- As próximas seções entram aqui -->` por:

```html
<!-- Seção 2: vitrine de produtos -->
<section id="produtos">
    <h2>Nossos Produtos</h2>

    <div class="lista-produtos">

        <article class="produto">
            <img src="img/violeta.svg" alt="Ilustração de um vaso de violetas roxas">
            <h3>Violeta</h3>
            <p>Delicada e fácil de cuidar, a violeta traz harmonia para qualquer ambiente.</p>
            <p class="preco">R$ 24,90</p>
        </article>

        <article class="produto">
            <img src="img/rosa.svg" alt="Ilustração de uma rosa vermelha">
            <h3>Rosa</h3>
            <p>O clássico símbolo do amor. Perfeita para declarações e datas especiais.</p>
            <p class="preco">R$ 12,90</p>
        </article>

        <article class="produto">
            <img src="img/girassol.svg" alt="Ilustração de um girassol amarelo">
            <h3>Girassol</h3>
            <p>Alegria em forma de flor: ilumina o dia de quem recebe.</p>
            <p class="preco">R$ 18,50</p>
        </article>

        <article class="produto">
            <img src="img/tulipa.svg" alt="Ilustração de uma tulipa cor-de-rosa">
            <h3>Tulipa</h3>
            <p>Elegante e colorida, ideal para arranjos modernos.</p>
            <p class="preco">R$ 21,00</p>
        </article>

    </div>
</section>
```

**O que está acontecendo:**

- `<div class="lista-produtos">` é uma **caixa genérica**, sem significado próprio. Nós a usamos aqui só para **agrupar** os cartões e depois organizá-los em grade com CSS. Regra prática: use uma tag semântica quando existir uma adequada, e `<div>` quando precisar apenas de um "recipiente" para estilizar.
- `<article class="produto">` representa cada **cartão de produto**. É um `article` porque cada produto faz sentido sozinho.
- O atributo **`class`** dá um "apelido" ao elemento, que usaremos no CSS. Diferente do `id`, **a mesma classe pode ser usada em vários elementos**, e é exatamente isso que queremos: todos os cartões terão a mesma aparência.
- `<img>` insere uma **imagem**:
  - `src` indica o **caminho** do arquivo. `img/violeta.svg` significa "entre na pasta `img` e pegue o arquivo `violeta.svg`". Esse é um **caminho relativo**.
  - `alt` é o **texto alternativo**: ele é lido por leitores de tela e aparece se a imagem não carregar. **É obrigatório.** Descreva o que a imagem mostra.
- `<h3>` é o título de cada produto, um nível abaixo do `<h2>` da seção.

📚 **Leia mais:**
- `<div>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/div) · [W3Schools](https://www.w3schools.com/tags/tag_div.asp)
- `<article>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/article) · [W3Schools](https://www.w3schools.com/tags/tag_article.asp)
- Atributo `class`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Global_attributes/class) · [W3Schools](https://www.w3schools.com/html/html_classes.asp)
- `<img>` e `alt`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/img) · [W3Schools](https://www.w3schools.com/html/html_images.asp)
- Caminhos de arquivos: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/Getting_started_with_the_web/Dealing_with_files) · [W3Schools](https://www.w3schools.com/html/html_filepaths.asp)


### Passo 6: Formulário de contato

Logo após o `</section>` dos produtos (ainda dentro do `<main>`), adicione:

```html
<!-- Seção 3: formulário de contato -->
<section id="contato">
    <h2>Entre em Contato</h2>
    <p>Quer encomendar um arranjo especial? Envie sua mensagem!</p>

    <form action="#" method="get">
        <label for="nome">Nome:</label>
        <input type="text" id="nome" name="nome" placeholder="Seu nome completo" required>

        <label for="email">E-mail:</label>
        <input type="email" id="email" name="email" placeholder="voce@exemplo.com" required>

        <label for="ocasiao">Ocasião:</label>
        <select id="ocasiao" name="ocasiao">
            <option value="presente">Presente</option>
            <option value="aniversario">Aniversário</option>
            <option value="casamento">Casamento</option>
            <option value="decoracao">Decoração</option>
        </select>

        <label for="mensagem">Mensagem:</label>
        <textarea id="mensagem" name="mensagem" placeholder="Conte o que você precisa..." required></textarea>

        <button type="submit">Enviar</button>
    </form>
</section>
```

**Os elementos do formulário:**

| Elemento / atributo | Para que serve |
|---|---|
| `<form>` | Agrupa os campos. `action` diz **para onde** os dados vão, e `method` diz **como** vão (`get` ou `post`). |
| `<label for="nome">` | **Rótulo** do campo. O `for` deve ter o mesmo valor do `id` do campo. Assim, clicar no rótulo seleciona o campo, e leitores de tela anunciam o rótulo corretamente. |
| `<input type="text">` | Campo de texto de uma linha. |
| `<input type="email">` | Campo de e-mail. O navegador **verifica sozinho** se o texto tem formato de e-mail (tem `@`, por exemplo), e no celular mostra um teclado com `@`. |
| `<select>` e `<option>` | Lista de opções (*drop-down*). O `value` é o que será enviado. |
| `<textarea>` | Área de texto com **várias linhas**. Diferente do `input`, ela tem tag de fechamento. |
| `<button type="submit">` | Botão que **envia** o formulário. |
| `name` | Nome com que o dado é enviado ao servidor (ex.: `nome=Maria`). |
| `placeholder` | Texto de exemplo exibido dentro do campo vazio. **Não substitui o `<label>`.** |
| `required` | Torna o campo **obrigatório**. |

> 🎯 **Validação sem JavaScript!** Experimente clicar em **Enviar** com os campos vazios, ou com um e-mail inválido como `maria.com`. O próprio navegador impede o envio e mostra um aviso, graças aos atributos `required` e `type="email"`. Tudo isso só com HTML5.

> 📝 **E para onde vão os dados?** Para processar os dados de verdade (enviar um e-mail, salvar em um banco de dados) é necessário um **programa no servidor** (*back-end*), assunto de outras disciplinas. Aqui usamos `action="#"`: ao enviar, a página é recarregada e você pode ver os dados na barra de endereços (ex.: `index.html?nome=Maria&email=...`). Isso mostra como o `method="get"` funciona.

📚 **Leia mais:**
- Formulários (visão geral): [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/Forms/Your_first_form) · [W3Schools](https://www.w3schools.com/html/html_forms.asp)
- `<form>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/form) · [W3Schools](https://www.w3schools.com/tags/tag_form.asp)
- `<label>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/label) · [W3Schools](https://www.w3schools.com/tags/tag_label.asp)
- `<input>` e seus tipos: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/input) · [W3Schools](https://www.w3schools.com/html/html_form_input_types.asp)
- `<select>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/select) · [W3Schools](https://www.w3schools.com/tags/tag_select.asp)
- `<textarea>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/textarea) · [W3Schools](https://www.w3schools.com/tags/tag_textarea.asp)
- `<button>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/button) · [W3Schools](https://www.w3schools.com/tags/tag_button.asp)
- Validação de formulários: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/Forms/Form_validation) · [W3Schools (`required`)](https://www.w3schools.com/tags/att_input_required.asp)


### Passo 7: Rodapé

Depois do `</main>` e antes do `</body>`, adicione:

```html
<!-- Rodapé -->
<footer>
    <p>&copy; 2026 Lojinha de Flores. Todos os direitos reservados.</p>
</footer>
```

- `<footer>` é o **rodapé** da página.
- `&copy;` é uma **entidade HTML**: um código que o navegador troca pelo símbolo **©**. Entidades também são usadas para exibir caracteres que têm significado especial no HTML, como `&lt;` (<) e `&gt;` (>).

📚 **Leia mais:**
- `<footer>`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/footer) · [W3Schools](https://www.w3schools.com/tags/tag_footer.asp)
- Entidades HTML: [MDN](https://developer.mozilla.org/pt-BR/docs/Glossary/Entity) · [W3Schools](https://www.w3schools.com/html/html_entities.asp)


> ### ✅ Ponto de verificação 1
>
> Salve o arquivo e abra o `index.html` no navegador. Você deve ver todo o conteúdo **sem estilo**: fonte padrão, links azuis sublinhados, lista com bolinhas e imagens grandes. **Isso é esperado!** O HTML cuida apenas da **estrutura**. Teste também os links do menu: eles devem levar às seções.
> 
> Compare seu código com [`template/index.html`](template/index.html).


## 5. Parte 2: A aparência com CSS

O **CSS** (*Cascading Style Sheets*, ou folhas de estilo em cascata) define a **aparência** da página: cores, fontes, espaçamentos, posicionamento. Com o CSS em um arquivo separado, podemos mudar todo o visual do site **sem tocar no HTML**.

### Anatomia de uma regra CSS

```css
seletor {
    propriedade: valor;
    propriedade: valor;
}
```

Exemplo real:

```css
nav a {                     /* seletor: QUAIS elementos serão estilizados */
    color: white;           /* declaração: propriedade + valor */
    text-decoration: none;  /* cada declaração termina com ; */
}
```

- O **seletor** escolhe *quais* elementos recebem o estilo.
- Cada **declaração** diz *o que* muda (`propriedade`) e *como* (`valor`).
- `/* ... */` é um **comentário** em CSS.

### Tipos de seletores usados neste tutorial

| Seletor | Exemplo | Seleciona... |
|---|---|---|
| **Universal** | `*` | todos os elementos |
| **Tipo** (tag) | `footer` | todos os `<footer>` |
| **Classe** | `.produto` | todos os elementos com `class="produto"` (note o **ponto**) |
| **Id** | `#contato` | o elemento com `id="contato"` (note o **#**) |
| **Descendente** | `nav a` | todo `<a>` que está **dentro** de um `<nav>` |
| **Agrupamento** | `form input, form textarea` | vários seletores com a **mesma** regra (separados por vírgula) |
| **Pseudo-classe** | `a:hover` | elementos em um **estado** especial (mouse em cima, campo em foco...) |

### A "cascata" e a especificidade

Quando duas regras mexem na mesma propriedade de um elemento, o navegador decide qual vence:

1. A regra **mais específica** vence (id > classe > tag).
2. Se tiverem a mesma especificidade, vence a que aparece **por último** no arquivo.
3. Algumas propriedades (como `color` e `font-family`) são **herdadas**: se você as define no `body`, todos os elementos dentro dele as recebem.

📚 **Leia mais:**
- Introdução ao CSS: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/First_steps/What_is_CSS) · [W3Schools](https://www.w3schools.com/css/css_intro.asp)
- Sintaxe: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Syntax) · [W3Schools](https://www.w3schools.com/css/css_syntax.asp)
- Seletores: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_selectors) · [W3Schools](https://www.w3schools.com/css/css_selectors.asp)
- Cascata e herança: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance) · [W3Schools (especificidade)](https://www.w3schools.com/css/css_specificity.asp)
- Formas de inserir CSS: [W3Schools](https://www.w3schools.com/css/css_howto.asp)


### O Box Model (modelo de caixa)

Antes de escrever o CSS, é fundamental entender que **todo elemento HTML é uma caixa retangular** composta de quatro camadas:

```
┌──────────────────────────────────────────┐
│                 MARGIN                   │  ← espaço EXTERNO (transparente),
│   ┌──────────────────────────────────┐   │    afasta a caixa das vizinhas
│   │            BORDER                │   │  ← a borda
│   │   ┌──────────────────────────┐   │   │
│   │   │         PADDING          │   │   │  ← espaço INTERNO,
│   │   │   ┌──────────────────┐   │   │   │    entre a borda e o conteúdo
│   │   │   │     CONTENT      │   │   │   │  ← o conteúdo (texto, imagem)
│   │   │   └──────────────────┘   │   │   │
│   │   └──────────────────────────┘   │   │
│   └──────────────────────────────────┘   │
└──────────────────────────────────────────┘
```

As propriedades `margin` e `padding` aceitam atalhos:

```css
padding: 20px;            /* 20px nos 4 lados */
padding: 10px 20px;       /* 10px em cima e embaixo | 20px nas laterais */
margin: 10px 0 5px;       /* 10px em cima | 0 nas laterais | 5px embaixo */
margin: 0 auto;           /* 0 em cima/embaixo | laterais automáticas = CENTRALIZA */
```

> 🔍 **Dica:** no navegador, aperte **F12** (Ferramentas do Desenvolvedor), clique em um elemento e veja o desenho do box model dele na aba "Computado" / "Computed".

📚 **Leia mais:** [MDN: O modelo de caixa](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/Building_blocks/The_box_model) · [W3Schools: Box Model](https://www.w3schools.com/css/css_boxmodel.asp) · [W3Schools: Margin](https://www.w3schools.com/css/css_margin.asp) · [W3Schools: Padding](https://www.w3schools.com/css/css_padding.asp)


### Passo 8: Criando o arquivo CSS e os estilos gerais

Crie o arquivo `style.css` **na mesma pasta** do `index.html` e comece com:

```css
/* ---------- 1. Estilos gerais ---------- */

/* Faz width/height incluírem padding e borda (ver "Box Model") */
* {
    box-sizing: border-box;
}

/* Rolagem suave ao clicar nos links do menu (#sobre, #produtos...) */
html {
    scroll-behavior: smooth;
}

body {
    font-family: Arial, Helvetica, sans-serif; /* Fonte padrão da página */
    margin: 0;                   /* Remove a margem padrão do navegador */
    padding: 0;                  /* Remove o espaçamento interno padrão */
    line-height: 1.6;            /* Altura da linha: melhora a leitura */
    color: #333333;              /* Cor do texto (cinza escuro) */
    background-color: #f7f9f4;   /* Fundo levemente esverdeado */
}
```

**Para que servem essas regras:**

- **`box-sizing: border-box`**: por padrão, se você define `width: 100%` e depois adiciona `padding` e `border`, o elemento fica **maior** que 100% e "vaza" para fora do contêiner. Com `border-box`, a largura informada **já inclui** padding e borda. É uma regra tão útil que quase todo projeto profissional a usa. O seletor `*` aplica isso a **todos** os elementos.
- **`scroll-behavior: smooth`**: faz a página **rolar suavemente** quando clicamos nos links internos do menu, em vez de "pular".
- **`font-family`**: define a fonte. Informamos uma **lista de alternativas**: se o computador não tiver Arial, usa Helvetica, e se não tiver nenhuma das duas, usa qualquer fonte `sans-serif` (sem serifa).
- **`margin: 0` e `padding: 0`**: os navegadores colocam uma margem padrão no `body` (em geral 8px). Zeramos para que o cabeçalho encoste nas bordas da janela.
- **`line-height`**: a distância entre as linhas do texto. O valor `1.6` significa 1,6 vez o tamanho da fonte.
- **`color`** e **`background-color`**: cor do texto e cor do fundo. Como `color` é **herdada**, todo o texto da página fica cinza escuro, exceto onde definirmos outra cor.

#### Sobre as cores

Cores podem ser escritas de várias formas:

| Formato | Exemplo | Observação |
|---|---|---|
| Nome | `white` | Existem cerca de 140 nomes prontos |
| Hexadecimal | `#2e7d32` | `#RRGGBB`: quantidade de vermelho, verde e azul (de `00` a `ff`) |
| RGB | `rgb(46, 125, 50)` | Mesma ideia, em decimal (0 a 255) |
| RGBA | `rgba(0, 0, 0, 0.1)` | O 4º valor é a **transparência** (0 = invisível, 1 = opaco) |

> ♿ **Acessibilidade:** o texto precisa ter **contraste** suficiente com o fundo para ser lido por todos, inclusive pessoas com baixa visão. Por isso usamos um verde escuro (`#2e7d32`) com texto branco. Teste o contraste de suas cores em [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/).

📚 **Leia mais:**
- `box-sizing`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/box-sizing) · [W3Schools](https://www.w3schools.com/css/css3_box-sizing.asp)
- `scroll-behavior`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/scroll-behavior) · [W3Schools](https://www.w3schools.com/cssref/pr_scroll-behavior.php)
- `font-family`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/font-family) · [W3Schools](https://www.w3schools.com/css/css_font.asp)
- `line-height`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/line-height) · [W3Schools](https://www.w3schools.com/cssref/pr_dim_line-height.php)
- Cores: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/color_value) · [W3Schools](https://www.w3schools.com/css/css_colors.asp)

### Passo 9: Cabeçalho com Flexbox

```css
/* ---------- 2. Cabeçalho ---------- */

header {
    background-color: #2e7d32;   /* Verde escuro */
    color: white;                /* Texto branco */
    padding: 20px;               /* Espaçamento interno */
    display: flex;               /* Ativa o Flexbox */
    justify-content: space-between; /* Título à esquerda, menu à direita */
    align-items: center;         /* Centraliza verticalmente */
    flex-wrap: wrap;             /* Permite quebrar linha em telas estreitas */
    gap: 10px;                   /* Espaço entre os itens flexíveis */
}

header h1 {
    margin: 0;                   /* Remove a margem padrão do título */
    font-size: 1.8rem;           /* 1.8 x o tamanho de fonte base */
}
```

#### Entendendo o Flexbox

Normalmente, elementos como `<h1>` e `<nav>` são **elementos de bloco**: cada um ocupa uma linha inteira, um embaixo do outro. Queremos o título **à esquerda** e o menu **à direita, na mesma linha**. Para isso usamos o **Flexbox**.

Ao escrever `display: flex` no `header`, ele vira um **contêiner flexível**, e seus **filhos diretos** (`<h1>` e `<nav>`) viram **itens flexíveis**, que ficam lado a lado.

```
justify-content: space-between     (eixo principal = horizontal)
┌───────────────────────────────────────────────────────┐
│ [🌷 Lojinha de Flores]        [Início Sobre Produtos] │  ← align-items: center
└───────────────────────────────────────────────────────┘    (eixo transversal = vertical)
```

| Propriedade | Efeito |
|---|---|
| `display: flex` | Transforma o elemento em contêiner flexível |
| `justify-content` | Distribui os itens no **eixo principal** (horizontal). `space-between` = o primeiro no início, o último no fim e o espaço que sobra entre eles |
| `align-items` | Alinha os itens no **eixo transversal** (vertical). `center` = centralizados |
| `flex-wrap: wrap` | Se não couber, os itens **quebram** para a linha de baixo |
| `gap` | Espaço entre os itens |

Na regra `header h1` usamos a unidade **`rem`**: ela é relativa ao tamanho de fonte base do navegador (normalmente 16px). Assim, `1.8rem` ≈ 29px. Unidades relativas respeitam quem aumenta o tamanho da fonte no navegador por necessidade visual.

> 🎮 **Pratique:** o jogo [Flexbox Froggy](https://flexboxfroggy.com/#pt-br) ensina Flexbox de forma divertida (em português!).

📚 **Leia mais:**
- Flexbox: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/CSS_layout/Flexbox) · [W3Schools](https://www.w3schools.com/css/css3_flexbox.asp)
- `justify-content`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/justify-content) · [W3Schools](https://www.w3schools.com/cssref/css3_pr_justify-content.php)
- `align-items`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/align-items) · [W3Schools](https://www.w3schools.com/cssref/css3_pr_align-items.php)
- `gap`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/gap) · [W3Schools](https://www.w3schools.com/cssref/css3_pr_gap.php)
- Unidades (`px`, `rem`, `%`): [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/Building_blocks/Values_and_units) · [W3Schools](https://www.w3schools.com/css/css_units.asp)


### Passo 10: Menu de navegação

```css
/* ---------- 3. Menu de navegação ---------- */

nav ul {
    list-style-type: none;       /* Remove os marcadores (bolinhas) */
    margin: 0;
    padding: 0;
    display: flex;               /* Itens da lista lado a lado */
    gap: 20px;                   /* Espaço entre os links */
}

nav a {
    color: white;                /* Links brancos */
    text-decoration: none;       /* Remove o sublinhado */
    font-weight: bold;           /* Negrito */
    padding-bottom: 4px;         /* Afasta a linha inferior do texto */
    border-bottom: 2px solid transparent; /* Linha invisível (reserva espaço) */
}

nav a:hover {
    border-bottom-color: white;  /* Mostra a linha ao passar o mouse */
}
```

**Para que servem essas regras:**

- **`nav ul`** é um **seletor descendente**: estiliza apenas a `<ul>` que está dentro do `<nav>`. Outras listas da página não são afetadas.
- **`list-style-type: none`** remove as bolinhas da lista. **`margin: 0`** e **`padding: 0`** removem o recuo padrão que o navegador dá às listas.
- Usamos **Flexbox novamente**, agora na `<ul>`, para deixar os `<li>` **lado a lado**. Um contêiner flexível pode estar dentro de outro sem problema.
- **`text-decoration: none`** remove o sublinhado padrão dos links.
- **`border-bottom: 2px solid transparent`** é uma borda inferior **invisível**. Ela "reserva" o espaço da linha para que, quando a borda ficar visível, o texto não "pule".
- **`:hover`** é uma **pseudo-classe**: a regra `nav a:hover` só vale **enquanto o mouse está sobre o link**. Nesse momento a borda fica branca, criando um sublinhado elegante.

> 💡 O documento original usava `display: inline` nos `<li>` para colocá-los lado a lado. Funciona, mas o Flexbox com `gap` dá mais controle sobre o espaçamento.

📚 **Leia mais:**
- Estilizando listas: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/Styling_text/Styling_lists) · [W3Schools](https://www.w3schools.com/css/css_list.asp)
- Estilizando links: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/Styling_text/Styling_links) · [W3Schools](https://www.w3schools.com/css/css_link.asp)
- `text-decoration`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/text-decoration) · [W3Schools](https://www.w3schools.com/css/css_text_decoration.asp)
- `border`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/border) · [W3Schools](https://www.w3schools.com/css/css_border.asp)
- Pseudo-classes (`:hover`, `:focus`): [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Pseudo-classes) · [W3Schools](https://www.w3schools.com/css/css_pseudo_classes.asp)

### Passo 11: Conteúdo principal e seções

```css
/* ---------- 4. Conteúdo principal ---------- */

main {
    max-width: 1000px;           /* Largura máxima do conteúdo */
    margin: 0 auto;              /* Centraliza horizontalmente */
    padding: 20px;
}

section {
    margin-bottom: 40px;         /* Espaço entre as seções */
}

h2 {
    color: #2e7d32;
    border-bottom: 2px solid #a5d6a7; /* Linha decorativa abaixo do título */
    padding-bottom: 5px;
}
```

**Para que servem essas regras:**

- **`max-width: 1000px`**: em monitores muito largos, linhas de texto enormes cansam a leitura. Limitamos o conteúdo a no máximo 1000px. Em telas menores, ele ocupa só o espaço disponível. Diferente de `width`, o `max-width` **não força** a largura, apenas **limita**.
- **`margin: 0 auto`**: com as margens laterais em `auto`, o navegador divide o espaço que sobra igualmente dos dois lados e **centraliza** o bloco. É a forma clássica de centralizar um elemento de bloco que tem largura definida.
- **`margin-bottom: 40px`** separa visualmente as seções.
- No **`h2`**, a borda inferior cria uma linha decorativa sob cada título de seção.

📚 **Leia mais:**
- `max-width`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/max-width) · [W3Schools](https://www.w3schools.com/css/css_max-width.asp)
- Centralizando elementos: [W3Schools](https://www.w3schools.com/css/css_align.asp)
- `margin`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/margin) · [W3Schools](https://www.w3schools.com/css/css_margin.asp)

### Passo 12: Vitrine de produtos com CSS Grid

```css
/* ---------- 5. Produtos ---------- */

.lista-produtos {
    display: grid;               /* Ativa o CSS Grid */
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); /* Colunas automáticas */
    gap: 20px;                   /* Espaço entre os cartões */
}

.produto {
    background-color: white;
    border: 1px solid #dddddd;   /* Borda fina cinza */
    border-radius: 8px;          /* Cantos arredondados */
    padding: 15px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Sombra suave */
}

.produto img {
    display: block;              /* Remove o espaço extra abaixo da imagem */
    width: 100%;                 /* Ocupa toda a largura do cartão */
    height: 180px;               /* Todas as imagens com a mesma altura */
    object-fit: cover;           /* Recorta a imagem sem distorcer */
    border-radius: 4px;
}

.produto h3 {
    margin: 10px 0 5px;          /* cima | laterais | baixo */
    color: #2e7d32;
}

.preco {
    margin: 0;
    font-size: 1.2rem;
    font-weight: bold;
    color: #c2185b;              /* Rosa escuro para destacar o preço */
}
```

#### Entendendo o CSS Grid

O Flexbox organiza itens em **uma dimensão** (uma linha **ou** uma coluna). O **CSS Grid** organiza em **duas dimensões**: linhas **e** colunas ao mesmo tempo, como uma tabela. É ideal para vitrines de produtos.

A linha mais importante é:

```css
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
```

Lendo em português: *"crie **quantas colunas couberem** (`auto-fit`), cada uma com **no mínimo 200px** e **no máximo uma fração igual do espaço livre** (`1fr`)"*.

```
Tela larga (≈1000px)         Tela média (≈500px)      Celular (≈350px)
┌────┐┌────┐┌────┐┌────┐     ┌──────┐┌──────┐         ┌────────────┐
│ 🌸 ││ 🌹 ││ 🌻 ││ 🌷 │     │  🌸  ││  🌹  │         │     🌸     │
└────┘└────┘└────┘└────┘     └──────┘└──────┘         └────────────┘
                             ┌──────┐┌──────┐         ┌────────────┐
                             │  🌻  ││  🌷  │         │     🌹     │
                             └──────┘└──────┘         └────────────┘ ...
```

O resultado é uma vitrine **responsiva sem nenhuma media query**: as colunas se reorganizam sozinhas conforme a largura da tela.

**As demais regras:**

- **`.produto`** (seletor de **classe**) transforma cada `<article>` em um **cartão**: fundo branco, borda, **cantos arredondados** (`border-radius`) e uma **sombra** (`box-shadow`).
  - `box-shadow: 0 2px 4px rgba(0,0,0,0.1)` significa deslocamento horizontal 0, deslocamento vertical 2px, desfoque de 4px e cor preta com 10% de opacidade.
- **`.produto img`**: as imagens do cartão.
  - `width: 100%` faz a imagem ocupar a largura do cartão.
  - `height: 180px` + **`object-fit: cover`** faz todas as imagens terem a mesma altura. O `cover` **recorta** o excesso em vez de esticar a imagem. Isso é muito útil quando as fotos têm tamanhos diferentes.
  - `display: block` remove um pequeno espaço que o navegador deixa abaixo de imagens (porque, por padrão, `<img>` se comporta como texto).
- **`.preco`** destaca o preço com fonte maior, negrito e uma cor diferente.

> 🎮 **Pratique:** o jogo [Grid Garden](https://cssgridgarden.com/#pt-br) ensina CSS Grid regando uma horta (em português!).

📚 **Leia mais:**
- CSS Grid: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout) · [W3Schools](https://www.w3schools.com/css/css_grid.asp)
- `grid-template-columns`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/grid-template-columns) · [W3Schools](https://www.w3schools.com/cssref/pr_grid-template-columns.php)
- `repeat()` / `minmax()`: [MDN (repeat)](https://developer.mozilla.org/pt-BR/docs/Web/CSS/repeat) · [MDN (minmax)](https://developer.mozilla.org/pt-BR/docs/Web/CSS/minmax)
- `border-radius`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/border-radius) · [W3Schools](https://www.w3schools.com/css/css3_borders.asp)
- `box-shadow`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/box-shadow) · [W3Schools](https://www.w3schools.com/css/css3_shadows_box.asp)
- `object-fit`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/object-fit) · [W3Schools](https://www.w3schools.com/css/css3_object-fit.asp)
- Seletor de classe: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Class_selectors) · [W3Schools](https://www.w3schools.com/cssref/sel_class.php)

### Passo 13: Formulário de contato

```css
/* ---------- 6. Formulário de contato ---------- */

form {
    max-width: 400px;            /* O formulário não passa de 400px */
    margin: 0 auto;              /* Centraliza o formulário */
    padding: 20px;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Agrupamento de seletores: a mesma regra vale para todos */
form label,
form input,
form select,
form textarea {
    display: block;              /* Cada elemento em sua própria linha */
    width: 100%;                 /* Ocupa toda a largura do formulário */
}

form label {
    font-weight: bold;
    margin-bottom: 5px;
}

form input,
form select,
form textarea {
    margin-bottom: 15px;
    padding: 8px;
    border: 1px solid #bbbbbb;
    border-radius: 4px;
    font-family: inherit;        /* Usa a mesma fonte do body */
    font-size: 1rem;
}

/* :focus = campo selecionado (clicado ou alcançado com Tab) */
form input:focus,
form select:focus,
form textarea:focus {
    border-color: #2e7d32;
    outline: 2px solid #a5d6a7;
}

form textarea {
    height: 100px;               /* Altura da área de texto */
    resize: vertical;            /* Usuário só redimensiona na vertical */
}

form button {
    background-color: #2e7d32;
    color: white;
    border: none;                /* Remove a borda padrão do botão */
    border-radius: 4px;
    padding: 10px 20px;          /* vertical | horizontal */
    font-size: 1rem;
    cursor: pointer;             /* Cursor de "mãozinha" */
    transition: background-color 0.3s; /* Troca de cor suave */
}

form button:hover {
    background-color: #1b5e20;   /* Verde mais escuro ao passar o mouse */
}
```

**Para que servem essas regras:**

- **`form`**: o formulário vira um "cartão" branco centralizado (`max-width` + `margin: 0 auto`, a mesma técnica do `main`).
- **Agrupamento de seletores** (separados por vírgula): em vez de repetir `display: block` e `width: 100%` quatro vezes, escrevemos uma única regra para `label`, `input`, `select` e `textarea`.
- **`display: block`**: por padrão, `<label>` e `<input>` são elementos **em linha** (*inline*) e ficariam lado a lado. Como bloco, cada um ocupa sua própria linha, com o rótulo **acima** do campo.
- **`width: 100%`**: os campos ocupam toda a largura do formulário. Graças ao `box-sizing: border-box` do Passo 8, o `padding` não faz os campos vazarem para fora.
- **`font-family: inherit`**: campos de formulário **não herdam** a fonte do `body` automaticamente. O valor `inherit` força essa herança.
- **`:focus`**: pseudo-classe ativada quando o campo está **selecionado**. O destaque visual ajuda quem navega pelo teclado (tecla **Tab**) a saber onde está. Nunca remova o indicador de foco sem colocar outro no lugar!
- **`resize: vertical`**: por padrão o usuário pode redimensionar a `<textarea>` em qualquer direção e "quebrar" o layout. Assim, só na vertical.
- **`cursor: pointer`**: mostra a "mãozinha" sobre o botão, indicando que é clicável.
- **`transition`**: faz a troca de cor do `:hover` acontecer **gradualmente** em 0,3 segundo, em vez de instantaneamente. É uma animação simples, feita só com CSS.

📚 **Leia mais:**
- Estilizando formulários: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/Forms/Styling_web_forms) · [W3Schools](https://www.w3schools.com/css/css_form.asp)
- `display` (block, inline, flex, grid): [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/display) · [W3Schools](https://www.w3schools.com/css/css_display_visibility.asp)
- `inherit`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/inherit) · [W3Schools](https://www.w3schools.com/cssref/css_inherit.php)
- `:focus`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/:focus) · [W3Schools](https://www.w3schools.com/cssref/sel_focus.php)
- `outline`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/outline) · [W3Schools](https://www.w3schools.com/css/css_outline.asp)
- `resize`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/resize) · [W3Schools](https://www.w3schools.com/cssref/css3_pr_resize.php)
- `cursor`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/cursor) · [W3Schools](https://www.w3schools.com/cssref/pr_class_cursor.php)
- `transition`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_transitions/Using_CSS_transitions) · [W3Schools](https://www.w3schools.com/css/css3_transitions.asp)

### Passo 14: Rodapé

```css
/* ---------- 7. Rodapé ---------- */

footer {
    background-color: #2e7d32;
    color: white;
    text-align: center;          /* Centraliza o texto */
    padding: 10px 0;             /* 10px em cima/embaixo, 0 nas laterais */
}
```

- **`text-align: center`** centraliza o **texto** (conteúdo em linha) dentro do rodapé. Não confunda com `margin: 0 auto`, que centraliza a **caixa** inteira.
- Repetimos o verde do cabeçalho para criar **identidade visual**.

📚 **Leia mais:** `text-align`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/text-align) · [W3Schools](https://www.w3schools.com/css/css_text_align.asp)


### Passo 15: Responsividade com Media Queries

```css
/* ---------- 8. Responsividade (telas pequenas) ---------- */

/* As regras abaixo só valem quando a tela tem até 600px de largura */
@media (max-width: 600px) {
    header {
        flex-direction: column;  /* Título em cima, menu embaixo */
        text-align: center;
    }

    nav ul {
        gap: 12px;
    }
}
```

Uma **media query** é uma "condição" no CSS: as regras dentro de `@media (max-width: 600px) { ... }` **só são aplicadas quando a largura da tela for de até 600px**, como em celulares.

- **`flex-direction: column`** muda a direção do Flexbox: em vez de lado a lado (`row`, o padrão), o título e o menu ficam **um embaixo do outro**.
- Reduzimos o `gap` do menu para os quatro links caberem em telas estreitas.

> ⚠️ A media query deve ficar **no final** do arquivo. Lembre-se da cascata: com a mesma especificidade, vence a regra que aparece **por último**.

> 🔍 **Teste:** aperte **F12** e ative o **modo de dispositivo** (ícone de celular/tablet, ou `Ctrl+Shift+M`). Escolha um celular e veja o layout mudar.

📚 **Leia mais:**
- Media queries: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_media_queries/Using_media_queries) · [W3Schools](https://www.w3schools.com/css/css_rwd_mediaqueries.asp)
- `flex-direction`: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/flex-direction) · [W3Schools](https://www.w3schools.com/cssref/css3_pr_flex-direction.php)
- Design responsivo: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/CSS_layout/Responsive_Design) · [W3Schools](https://www.w3schools.com/css/css_rwd_intro.asp)



> ### ✅ Ponto de verificação 2
> 
> Salve o `style.css` e recarregue a página (**F5**). Agora ela deve estar com cores, cartões de produtos em grade, formulário centralizado e menu funcionando. Redimensione a janela do navegador e observe:
> 
> - os cartões mudando de 4 para 3, 2 e 1 coluna;
> - o cabeçalho "empilhando" título e menu em telas estreitas.
> 
> Compare seu código com [`template/style.css`](template/style.css).



## 6. Parte 3: Testando e validando

### Validação do código

Os navegadores são "tolerantes" e tentam exibir a página mesmo com erros. Isso esconde problemas! Use os validadores oficiais do W3C:

- **HTML:** [validator.w3.org](https://validator.w3.org/#validate_by_input). Cole o conteúdo do `index.html` na aba *"Validate by Direct Input"*.
- **CSS:** [jigsaw.w3.org/css-validator](https://jigsaw.w3.org/css-validator/#validate_by_input). Cole o conteúdo do `style.css`.

O objetivo é chegar a **zero erros**.

### Ferramentas do Desenvolvedor (DevTools)

Aperte **F12** (ou clique com o botão direito em um elemento e escolha **Inspecionar**). Nas DevTools você pode:

- ver quais regras CSS estão sendo aplicadas a cada elemento (e quais foram "vencidas" pela cascata, que aparecem riscadas);
- **editar o CSS ao vivo** para testar valores antes de alterar o arquivo;
- visualizar o **box model**, as grades do Grid e os contêineres Flex;
- simular telas de celular.

📚 **Leia mais:** [MDN: O que são ferramentas do desenvolvedor?](https://developer.mozilla.org/pt-BR/docs/Learn/Common_questions/Tools_and_setup/What_are_browser_developer_tools)

### Problemas comuns

| Sintoma | Causa provável |
|---|---|
| O CSS não é aplicado | Nome ou caminho do arquivo diferente no `<link href="...">` |
| Imagem não aparece (mostra só o texto do `alt`) | Caminho do `src` errado ou imagem fora da pasta `img/` |
| Link do menu não rola até a seção | `href="#produtos"` não corresponde a nenhum `id="produtos"` |
| Uma regra CSS "não funciona" | Falta `;` na linha anterior, `{ }` não fechado ou `.` esquecido no seletor de classe |
| Campos do formulário vazam para fora | Faltou o `box-sizing: border-box` |
| Acentos aparecem como `Ã§` ou `�` | Falta `<meta charset="UTF-8">` ou o arquivo não foi salvo em UTF-8 |

## 7. Resumo: tags e propriedades usadas

### Tags HTML

| Tag | Função | Referências |
|---|---|---|
| `<!DOCTYPE html>` | Declara HTML5 | [MDN](https://developer.mozilla.org/pt-BR/docs/Glossary/Doctype) · [W3S](https://www.w3schools.com/tags/tag_doctype.asp) |
| `<html>` | Elemento raiz | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/html) · [W3S](https://www.w3schools.com/tags/tag_html.asp) |
| `<head>` | Metadados | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/head) · [W3S](https://www.w3schools.com/tags/tag_head.asp) |
| `<meta>` | Charset, viewport, descrição | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/meta) · [W3S](https://www.w3schools.com/tags/tag_meta.asp) |
| `<title>` | Título da aba | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/title) · [W3S](https://www.w3schools.com/tags/tag_title.asp) |
| `<link>` | Liga o CSS | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/link) · [W3S](https://www.w3schools.com/tags/tag_link.asp) |
| `<body>` | Conteúdo visível | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/body) · [W3S](https://www.w3schools.com/tags/tag_body.asp) |
| `<header>` | Cabeçalho | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/header) · [W3S](https://www.w3schools.com/tags/tag_header.asp) |
| `<nav>` | Navegação | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/nav) · [W3S](https://www.w3schools.com/tags/tag_nav.asp) |
| `<main>` | Conteúdo principal | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/main) · [W3S](https://www.w3schools.com/tags/tag_main.asp) |
| `<section>` | Seção temática | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/section) · [W3S](https://www.w3schools.com/tags/tag_section.asp) |
| `<article>` | Conteúdo independente | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/article) · [W3S](https://www.w3schools.com/tags/tag_article.asp) |
| `<div>` | Contêiner genérico | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/div) · [W3S](https://www.w3schools.com/tags/tag_div.asp) |
| `<footer>` | Rodapé | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/footer) · [W3S](https://www.w3schools.com/tags/tag_footer.asp) |
| `<h1>`–`<h6>` | Títulos | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/Heading_Elements) · [W3S](https://www.w3schools.com/tags/tag_hn.asp) |
| `<p>` | Parágrafo | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/p) · [W3S](https://www.w3schools.com/tags/tag_p.asp) |
| `<strong>` | Texto importante | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/strong) · [W3S](https://www.w3schools.com/tags/tag_strong.asp) |
| `<ul>` / `<li>` | Lista e itens | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/ul) · [W3S](https://www.w3schools.com/tags/tag_ul.asp) |
| `<a>` | Link | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/a) · [W3S](https://www.w3schools.com/tags/tag_a.asp) |
| `<img>` | Imagem | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/img) · [W3S](https://www.w3schools.com/tags/tag_img.asp) |
| `<form>` | Formulário | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/form) · [W3S](https://www.w3schools.com/tags/tag_form.asp) |
| `<label>` | Rótulo de campo | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/label) · [W3S](https://www.w3schools.com/tags/tag_label.asp) |
| `<input>` | Campo de entrada | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/input) · [W3S](https://www.w3schools.com/tags/tag_input.asp) |
| `<select>` / `<option>` | Lista de opções | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/select) · [W3S](https://www.w3schools.com/tags/tag_select.asp) |
| `<textarea>` | Texto multilinha | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/textarea) · [W3S](https://www.w3schools.com/tags/tag_textarea.asp) |
| `<button>` | Botão | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/button) · [W3S](https://www.w3schools.com/tags/tag_button.asp) |

### Propriedades CSS

| Propriedade | O que faz | Referências |
|---|---|---|
| `box-sizing` | Define se width inclui padding e borda | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/box-sizing) · [W3S](https://www.w3schools.com/cssref/css3_pr_box-sizing.php) |
| `scroll-behavior` | Rolagem suave | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/scroll-behavior) · [W3S](https://www.w3schools.com/cssref/pr_scroll-behavior.php) |
| `font-family` | Fonte | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/font-family) · [W3S](https://www.w3schools.com/cssref/pr_font_font-family.php) |
| `font-size` | Tamanho da fonte | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/font-size) · [W3S](https://www.w3schools.com/cssref/pr_font_font-size.php) |
| `font-weight` | Espessura (negrito) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/font-weight) · [W3S](https://www.w3schools.com/cssref/pr_font_weight.php) |
| `line-height` | Altura da linha | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/line-height) · [W3S](https://www.w3schools.com/cssref/pr_dim_line-height.php) |
| `color` | Cor do texto | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/color) · [W3S](https://www.w3schools.com/cssref/pr_text_color.php) |
| `background-color` | Cor de fundo | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-color) · [W3S](https://www.w3schools.com/cssref/pr_background-color.php) |
| `margin` | Espaço externo | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/margin) · [W3S](https://www.w3schools.com/cssref/pr_margin.php) |
| `padding` | Espaço interno | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/padding) · [W3S](https://www.w3schools.com/cssref/pr_padding.php) |
| `border` | Borda | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/border) · [W3S](https://www.w3schools.com/cssref/pr_border.php) |
| `border-radius` | Cantos arredondados | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/border-radius) · [W3S](https://www.w3schools.com/cssref/css3_pr_border-radius.php) |
| `box-shadow` | Sombra | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/box-shadow) · [W3S](https://www.w3schools.com/cssref/css3_pr_box-shadow.php) |
| `width` / `height` | Largura / altura | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/width) · [W3S](https://www.w3schools.com/css/css_dimension.asp) |
| `max-width` | Largura máxima | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/max-width) · [W3S](https://www.w3schools.com/cssref/pr_dim_max-width.php) |
| `display` | Tipo de caixa (block, flex, grid...) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/display) · [W3S](https://www.w3schools.com/cssref/pr_class_display.php) |
| `justify-content` | Alinhamento no eixo principal (flex) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/justify-content) · [W3S](https://www.w3schools.com/cssref/css3_pr_justify-content.php) |
| `align-items` | Alinhamento no eixo transversal (flex) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/align-items) · [W3S](https://www.w3schools.com/cssref/css3_pr_align-items.php) |
| `flex-wrap` | Quebra de linha no flex | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/flex-wrap) · [W3S](https://www.w3schools.com/cssref/css3_pr_flex-wrap.php) |
| `flex-direction` | Direção do flex (linha/coluna) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/flex-direction) · [W3S](https://www.w3schools.com/cssref/css3_pr_flex-direction.php) |
| `gap` | Espaço entre itens (flex/grid) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/gap) · [W3S](https://www.w3schools.com/cssref/css3_pr_gap.php) |
| `grid-template-columns` | Colunas do grid | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/grid-template-columns) · [W3S](https://www.w3schools.com/cssref/pr_grid-template-columns.php) |
| `object-fit` | Encaixe da imagem | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/object-fit) · [W3S](https://www.w3schools.com/css/css3_object-fit.asp) |
| `list-style-type` | Marcador de lista | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/list-style-type) · [W3S](https://www.w3schools.com/cssref/pr_list-style-type.php) |
| `text-decoration` | Sublinhado etc. | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/text-decoration) · [W3S](https://www.w3schools.com/cssref/pr_text_text-decoration.php) |
| `text-align` | Alinhamento do texto | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/text-align) · [W3S](https://www.w3schools.com/cssref/pr_text_text-align.php) |
| `outline` | Contorno (foco) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/outline) · [W3S](https://www.w3schools.com/cssref/pr_outline.php) |
| `resize` | Redimensionamento | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/resize) · [W3S](https://www.w3schools.com/cssref/css3_pr_resize.php) |
| `cursor` | Tipo de cursor | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/cursor) · [W3S](https://www.w3schools.com/cssref/pr_class_cursor.php) |
| `transition` | Animação de mudança | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/transition) · [W3S](https://www.w3schools.com/cssref/css3_pr_transition.php) |
| `@media` | Regras condicionais (responsivo) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/@media) · [W3S](https://www.w3schools.com/cssref/css3_pr_mediaquery.php) |


## 8. Desafio: Vitrine de Promoções

A Lojinha de Flores quer divulgar as **promoções da semana**! Sua tarefa é **partir do código produzido neste tutorial** (pasta [`template/`](template/)) e implementar uma nova seção **"Promoções da Semana"**, usando **somente HTML e CSS** (sem JavaScript).

### Resultado esperado (esboço)

```
Promoções da Semana
─────────────────────────────────────────────────────────
┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
│ [-20%]           │ │ [-15%]           │ │ [-30%]           │  ← selo no canto
│     imagem       │ │     imagem       │ │     imagem       │
│ Buquê de Rosas   │ │ Orquídea         │ │ Kit Suculentas   │
│ descrição...     │ │ descrição...     │ │ descrição...     │
│ de R$ 99,90      │ │ de R$ 80,00      │ │ de R$ 50,00      │  ← preço antigo (<del>, riscado)
│ por R$ 79,90     │ │ por R$ 68,00     │ │ por R$ 35,00     │  ← preço novo (.preco)
└──────────────────┘ └──────────────────┘ └──────────────────┘
```

### Requisitos obrigatórios

**HTML (`index.html`)**

1. Crie uma nova `<section>` com `id="promocoes"` e o título `<h2>Promoções da Semana</h2>`, posicionada **entre** a seção de Produtos e a de Contato.
2. Adicione um link **"Promoções"** no menu de navegação (`<nav>`) que leve até essa seção.
3. Dentro da seção, crie **pelo menos 3 produtos em promoção**. Reaproveite a estrutura do tutorial: um `<div class="lista-produtos">` contendo cartões `<article>`.
4. Cada cartão de promoção deve ter **duas classes**: `class="produto promocao"`. (Sim, um elemento pode ter várias classes, separadas por espaço!)
5. Cada cartão deve conter:
   - um **selo de desconto**: `<span class="selo">-20%</span>`;
   - uma **imagem** com `alt` descritivo (use imagens próprias, de bancos gratuitos, ou reutilize as da pasta `img/`);
   - o **nome** do produto (`<h3>`) e uma **descrição** (`<p>`);
   - o **preço antigo** marcado com a tag `<del>` e o **preço novo** com a classe `preco`.

**CSS (`style.css`)**

6. Os cartões com a classe `.promocao` devem ter uma aparência **diferente** dos cartões comuns (por exemplo, borda colorida e/ou fundo de outra cor), **sem alterar** a aparência dos produtos normais.
7. O `.selo` deve aparecer **no canto superior do cartão, sobreposto à imagem**, com fundo colorido, texto branco e cantos arredondados.
8. O preço antigo (`<del>`) deve aparecer **menor e em cinza**.
9. Ao passar o mouse sobre um cartão de promoção, ele deve "**subir**" levemente e a sombra deve aumentar, com uma **transição suave**.
10. A seção deve continuar **responsiva**: teste em uma largura de celular (F12 → modo dispositivo).

### Dicas (conceitos novos que você vai pesquisar)

| Para fazer... | Pesquise sobre | Referências |
|---|---|---|
| Duas classes no mesmo elemento e selecionar só os cartões de promoção | Seletor de múltiplas classes (`.produto.promocao`) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Class_selectors) · [W3Schools](https://www.w3schools.com/cssref/sel_class.php) |
| Colocar o selo sobre a imagem | `position: relative` no cartão + `position: absolute` no selo, com `top` e `left` | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/position) · [W3Schools](https://www.w3schools.com/css/css_positioning.asp) |
| Preço antigo riscado | Tag `<del>` | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/del) · [W3Schools](https://www.w3schools.com/tags/tag_del.asp) |
| Selo em linha com o texto | Tag `<span>` | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/span) · [W3Schools](https://www.w3schools.com/tags/tag_span.asp) |
| Fazer o cartão "subir" | `transform: translateY(-5px)` dentro de `:hover` | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/transform) · [W3Schools](https://www.w3schools.com/css/css3_2dtransforms.asp) |
| Animar a subida | `transition` (já usado no botão do formulário!) | [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/transition) · [W3Schools](https://www.w3schools.com/css/css3_transitions.asp) |

> 💡 **Dica sobre `position`:** um elemento com `position: absolute` é posicionado em relação ao **ancestral mais próximo que tenha `position` diferente de `static`**. Por isso o cartão precisa de `position: relative`. Sem isso, o selo vai parar no canto da **página**!

### Desafios extras

- ⭐ **Tabela de entrega:** dentro da seção de promoções, crie uma tabela (`<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>`) com os bairros atendidos e o valor do frete, e estilize-a com bordas e linhas zebradas (`tr:nth-child(even)`). Referências: [MDN](https://developer.mozilla.org/pt-BR/docs/Learn/HTML/Tables/Basics) · [W3Schools](https://www.w3schools.com/html/html_tables.asp) · [W3Schools: CSS Tables](https://www.w3schools.com/css/css_table.asp)
- ⭐⭐ **Mapa da loja:** adicione ao rodapé um endereço usando a tag `<address>` e um mapa incorporado com `<iframe>` (por exemplo, do OpenStreetMap: menu "Compartilhar" → "HTML"). Referências: [MDN (address)](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/address) · [W3Schools (iframe)](https://www.w3schools.com/html/html_iframe.asp)
- ⭐⭐⭐ **Variáveis CSS:** o verde `#2e7d32` aparece várias vezes no CSS. Crie uma variável `--cor-principal` em `:root` e use `var(--cor-principal)` no lugar das repetições. Depois mude a cor em **um só lugar** e veja o site todo mudar! Referências: [MDN](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Using_CSS_custom_properties) · [W3Schools](https://www.w3schools.com/css/css3_variables.asp)

### Regras

- ❌ **Não** use JavaScript.
- ❌ **Não** use frameworks CSS (Bootstrap, Tailwind etc.).
- ✅ Escreva comentários no CSS explicando as regras novas que você criou.
- ✅ O HTML e o CSS devem passar nos validadores do W3C (veja a [Parte 3](#6-parte-3-testando-e-validando)) **sem erros**.

### O que entregar

Uma pasta compactada (`.zip`) contendo `index.html`, `style.css` e a pasta `img/` com todas as imagens usadas.

### Critérios de avaliação

| Critério | Pontos |
|---|---|
| Seção `#promocoes` criada, com link funcionando no menu | 1,5 |
| 3 ou mais cartões com estrutura correta (`article`, `span.selo`, `img` com `alt`, `h3`, `p`, `del`, `.preco`) | 2,0 |
| Cartões de promoção com visual diferente, **sem afetar** os produtos comuns | 1,5 |
| Selo posicionado corretamente sobre a imagem (`position`) | 2,0 |
| Efeito de `:hover` com `transform` e `transition` | 1,5 |
| Layout responsivo funcionando no celular | 0,5 |
| Código validado no W3C, indentado e comentado | 1,0 |
| **Total** | **10,0** |


## 9. Referências

**Documentação**
- MDN Web Docs (Mozilla): [HTML](https://developer.mozilla.org/pt-BR/docs/Web/HTML) · [CSS](https://developer.mozilla.org/pt-BR/docs/Web/CSS) · [Aprendendo desenvolvimento web](https://developer.mozilla.org/pt-BR/docs/Learn)
- W3Schools: [HTML Tutorial](https://www.w3schools.com/html/) · [CSS Tutorial](https://www.w3schools.com/css/) · [Referência de tags](https://www.w3schools.com/tags/) · [Referência CSS](https://www.w3schools.com/cssref/)

**Ferramentas**
- [Validador HTML do W3C](https://validator.w3.org/)
- [Validador CSS do W3C](https://jigsaw.w3.org/css-validator/)
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/): verificador de contraste de cores
- [Can I use](https://caniuse.com/): quais navegadores suportam cada recurso

**Para praticar**
- [Flexbox Froggy](https://flexboxfroggy.com/#pt-br): jogo para aprender Flexbox
- [Grid Garden](https://cssgridgarden.com/#pt-br): jogo para aprender CSS Grid
- [CSS Diner](https://flukeout.github.io/): jogo para aprender seletores CSS

---
_Tutorial baseado em códigos gerados pelo Prof. Wellington Sarmento e organizado usando a IA Claude Opus 5.5_
