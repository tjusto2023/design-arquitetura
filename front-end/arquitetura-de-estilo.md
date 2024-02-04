# Design Pattern para estilo

Ao trabalhar com estilos em CSS, não há padrões de design no mesmo sentido que existem para programação. No entanto, há boas práticas e metodologias que ajudam a organizar e estruturar seus estilos de forma mais eficiente e sustentável. Alguns desses padrões e metodologias são:

1. **BEM (Block, Element, Modifier):**
   - O BEM é uma metodologia que visa tornar o código CSS mais modular e reutilizável, dividindo-o em blocos, elementos e modificadores.
   - Exemplo:

    ```css
    .block {
      /* Estilos do bloco */
    }

    .block__element {
      /* Estilos do elemento dentro do bloco */
    }

    .block--modifier {
      /* Estilos modificados para o bloco */
    }
    ```

2. **SMACSS (Scalable and Modular Architecture for CSS):**
   - O SMACSS é uma metodologia que divide os estilos em categorias específicas, promovendo a escalabilidade e manutenção do código.
   - Categorias incluem base, layout, módulo, estado e tema.
   - Exemplo:

    ```css
    /* Base Styles */
    body {
      font-size: 16px;
    }

    /* Layout Styles */
    .container {
      width: 100%;
      max-width: 1200px;
      margin: 0 auto;
    }

    /* Module Styles */
    .button {
      /* Estilos do botão */
    }

    /* State Styles */
    .is-active {
      /* Estilos para o estado ativo */
    }
    ```

3. **OOCSS (Object-Oriented CSS):**
   - O OOCSS incentiva a separação da estrutura e do design visual, promovendo a reutilização de estilos em diferentes partes do site.
   - Exemplo:

    ```css
    /* Estrutura */
    .box {
      padding: 10px;
      margin: 10px;
    }

    /* Design Visual */
    .box--blue {
      background-color: blue;
      color: white;
    }
    ```

4. **ITCSS (Inverted Triangle CSS):**
   - O ITCSS organiza os estilos em uma pirâmide invertida, com estilos mais genéricos e de baixo nível na base, e estilos mais específicos e de alto nível no topo.
   - Exemplo:

    ```css
    /* Configurações globais e resets */
    html {
      font-size: 16px;
    }

    /* Estilos base */
    body {
      font-family: 'Arial', sans-serif;
    }

    /* Componentes e módulos */
    .button {
      /* Estilos do botão */
    }

    /* Estilos de layout e templates */
    .container {
      /* Estilos do layout */
    }

    /* Estilos de temas e variações específicas do projeto */
    .theme-dark {
      /* Estilos para o tema escuro */
    }
    ```

Essas metodologias não são mutuamente exclusivas, e você pode combiná-las ou adaptá-las conforme necessário para atender às necessidades específicas do seu projeto. O importante é manter a consistência, modularidade e reusabilidade em seus estilos.

## Estrutura de Cascading Style Sheets

Montar uma boa estrutura de Cascading Style Sheets (CSS) é fundamental para garantir a manutenibilidade e a escalabilidade do seu código. Abaixo estão algumas diretrizes e boas práticas que podem ajudar a criar uma estrutura organizada e eficiente para o seu CSS:

### 1. **Organização Geral:**

- **Divisão Modular:**
  - Separe o CSS em módulos ou componentes, cada um responsável por uma parte específica da interface.

- **Arquivos Separados:**
  - Mantenha arquivos CSS separados para diferentes partes do seu projeto (ex: base, layout, componentes, páginas).

```plaintext
styles/
|-- base/
|   |-- reset.css
|   |-- typography.css
|-- layout/
|   |-- grid.css
|   |-- header.css
|   |-- footer.css
|-- components/
|   |-- button.css
|   |-- card.css
|-- pages/
|   |-- home.css
|   |-- about.css
|-- main.css
```

### 2. **Metodologias e Padrões:**

- **BEM, SMACSS, ou OOCSS:**
  - Considere a adoção de uma metodologia de nomenclatura como BEM, SMACSS ou OOCSS para padronizar a nomenclatura e a estrutura.

- **Nomeação Semântica:**
  - Use nomes semânticos para classes, evitando estilos baseados em apresentação.

### 3. **Resets e Normalizações:**

- **Reset CSS ou Normalize:**
  - Inclua um arquivo de reset ou normalização para garantir uma base consistente entre diferentes navegadores.

### 4. **Responsividade:**

- **Media Queries:**
  - Utilize media queries para estilos responsivos e adaptação a diferentes dispositivos.

```css
/* Exemplo de media query */
@media screen and (max-width: 768px) {
  /* Estilos para telas menores */
}
```

### 5. **Variáveis e Configurações:**

- **Variáveis CSS:**
  - Use variáveis CSS para armazenar valores reutilizáveis, como cores e tamanhos.

```css
:root {
  --primary-color: #3498db;
  --font-size: 16px;
}

body {
  color: var(--primary-color);
  font-size: var(--font-size);
}
```

### 6. **Arquitetura de Diretórios:**

- **Organização de Arquivos:**
  - Estruture seus diretórios de forma lógica, agrupando arquivos semelhantes.

- **Arquivos Importados:**
  - Importe arquivos CSS necessários em um arquivo principal (entry point) para manter a ordem correta.

### 7. **Comentários:**

- **Comentários Descritivos:**
  - Adicione comentários descritivos para explicar blocos de código complexos ou para documentar o propósito de um componente.

```css
/* Estilos para a barra de navegação */
.navbar {
  /* ... */
}
```

### 8. **Nomenclatura Consistente:**

- **Consistência de Nomes:**
  - Mantenha uma nomenclatura consistente para facilitar a leitura e a manutenção do código.

### 9. **Desempenho:**

- **Concatenação e Minificação:**
  - Ao implantar, considere concatenar e minificar arquivos CSS para otimizar o desempenho.

### 10. **Ferramentas e Pré-processadores:**

- **Sass ou Less:**
  - Considere o uso de pré-processadores como Sass ou Less para adicionar funcionalidades como variáveis, mixins e aninhamento.

### 11. **Versionamento:**

- **Controle de Versão:**
  - Considere o uso de controle de versão para rastrear alterações em seus arquivos CSS.

### Exemplo de `main.css` (Entry Point):

```css
/* Importação dos estilos globais */
@import 'base/reset.css';
@import 'base/typography.css';

/* Importação dos estilos de layout */
@import 'layout/grid.css';
@import 'layout/header.css';
@import 'layout/footer.css';

/* Importação dos estilos dos componentes */
@import 'components/button.css';
@import 'components/card.css';

/* Importação dos estilos das páginas */
@import 'pages/home.css';
@import 'pages/about.css';
```

Lembre-se de que essas diretrizes podem ser adaptadas conforme a necessidade do seu projeto. O objetivo principal é manter uma estrutura organizada, modular e fácil de manter.

## Usando o Sass 

Ao usar Sass (Syntactically Awesome Stylesheets) para criar uma estrutura de Cascading Style Sheets (CSS), você pode aproveitar recursos como variáveis, aninhamento, mixins e importações para tornar seu código mais modular e fácil de manter. Abaixo está um exemplo de como você poderia estruturar seus arquivos Sass:

### Estrutura de Diretórios:

```plaintext
styles/
|-- base/
|   |-- _reset.scss
|   |-- _typography.scss
|-- layout/
|   |-- _grid.scss
|   |-- _header.scss
|   |-- _footer.scss
|-- components/
|   |-- _button.scss
|   |-- _card.scss
|-- pages/
|   |-- _home.scss
|   |-- _about.scss
|-- main.scss
```

### `main.scss` (Entry Point):

```scss
/* Importação dos estilos globais */
@import 'base/reset';
@import 'base/typography';

/* Importação dos estilos de layout */
@import 'layout/grid';
@import 'layout/header';
@import 'layout/footer';

/* Importação dos estilos dos componentes */
@import 'components/button';
@import 'components/card';

/* Importação dos estilos das páginas */
@import 'pages/home';
@import 'pages/about';
```

### Exemplo de Uso de Variáveis:

```scss
/* _variables.scss */
$primary-color: #3498db;
$font-size: 16px;

/* _button.scss */
.button {
  background-color: $primary-color;
  font-size: $font-size;
  /* ... outros estilos ... */
}
```

### Exemplo de Aninhamento e Mixins:

```scss
/* _card.scss */
.card {
  padding: 10px;

  h2 {
    font-size: 1.5em;
  }

  @include box-shadow(0 0 10px rgba(0, 0, 0, 0.1));
}

/* Mixin para sombra */
@mixin box-shadow($shadow) {
  -webkit-box-shadow: $shadow;
  -moz-box-shadow: $shadow;
  box-shadow: $shadow;
}
```

### Vantagens do Sass:

1. **Variáveis:** Use variáveis para armazenar valores reutilizáveis.

2. **Aninhamento:** Aninhe seletores para refletir a estrutura HTML.

3. **Mixins:** Crie mixins para reutilizar padrões de estilos.

4. **Importações:** Importe arquivos Sass para manter uma estrutura modular.

5. **Partials e Importações Condicionais:** Use partials (arquivos começando com `_`) para dividir seu código em partes menores e importe apenas o que for necessário.

Ao compilar o arquivo `main.scss` com Sass, ele gerará um único arquivo CSS, aproveitando as importações e mantendo a organização da estrutura. Certifique-se de instalar o Sass e configurar um script de compilação em seu projeto para começar a trabalhar com essas práticas.

## Configurar variáveis globais de estilo 

Webpack, por si só, não lida diretamente com variáveis globais de estilo sem import. No entanto, você pode alcançar esse comportamento usando ferramentas como loaders e plugins no ecossistema do Webpack, juntamente com pré-processadores CSS como Sass.

Aqui estão os passos básicos para configurar variáveis globais de estilo sem a necessidade de importar em cada arquivo no Webpack usando Sass:

### 1. Instalar Dependências:

Certifique-se de ter os pacotes necessários instalados:

```bash
npm install sass sass-loader style-loader css-loader --save-dev
```

### 2. Configurar o Webpack:

Configure o seu arquivo `webpack.config.js` para incluir os loaders necessários:

```javascript
const path = require('path');

module.exports = {
  entry: './src/index.js', // Seu ponto de entrada principal
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
  module: {
    rules: [
      {
        test: /\.scss$/,
        use: [
          'style-loader', // Adiciona estilos ao DOM via tag <style>
          'css-loader',   // Converte CSS em módulos CommonJS
          'sass-loader'   // Compila Sass para CSS
        ],
      },
    ],
  },
};
```

### 3. Criar Variáveis Globais com Sass:

Crie um arquivo `_variables.scss` com suas variáveis globais:

```scss
// _variables.scss

$primary-color: #3498db;
$font-size: 16px;
```

### 4. Usar Variáveis no Estilo:

Agora, em seus estilos Sass, você pode usar essas variáveis diretamente sem importar:

```scss
// styles.scss

body {
  color: $primary-color;
  font-size: $font-size;
}

.button {
  background-color: $primary-color;
  /* outros estilos */
}
```

### 5. Importar Arquivos Sass no Seu Ponto de Entrada:

Certifique-se de importar seus arquivos Sass no ponto de entrada do seu aplicativo (geralmente um arquivo JavaScript):

```javascript
// index.js

import './styles.scss'; // Importa os estilos Sass
```

### 6. Compilar e Executar:

Execute o webpack para compilar e gerar seu bundle:

```bash
npx webpack
```

O resultado final será um único arquivo JavaScript (bundle) que inclui tanto seu código JavaScript quanto os estilos Sass. Isso elimina a necessidade de importar variáveis globalmente em cada arquivo Sass.

## Mixins em Sass para criar media queries com breakpoints

Ao utilizar mixins em Sass para criar media queries com breakpoints, você pode criar um sistema flexível e fácil de manter. Aqui está um exemplo básico:

```scss
// Defina seus breakpoints
$breakpoints: (
  small: 576px,
  medium: 768px,
  large: 992px,
  xlarge: 1200px
);

// Mixin para media queries
@mixin breakpoint($point) {
  $breakpoint: map-get($breakpoints, $point);
  @media only screen and (min-width: $breakpoint) {
    @content;
  }
}

// Exemplos de uso
.element {
  width: 100%;

  @include breakpoint(medium) {
    width: 50%;
  }

  @include breakpoint(large) {
    width: 33.33%;
  }

  @include breakpoint(xlarge) {
    width: 25%;
  }
}
```

Neste exemplo:

1. Definimos um mapa chamado `$breakpoints` que associa nomes de breakpoints a valores em pixels.
2. Criamos um mixin chamado `breakpoint` que aceita um ponto (nome do breakpoint) e aplica as regras dentro da media query correspondente.
3. Em seguida, usamos o mixin nos estilos do nosso elemento, especificando as regras específicas para cada breakpoint.

Isso torna fácil ajustar e manter os breakpoints em um único lugar (no mapa) e simplifica a aplicação de estilos condicionais com mixins.

Se você preferir usar nomes mais descritivos, renomear os `$breakpoints` para refletir tipos de dispositivos, como "mobile", "tablet", "notebook", etc., é uma escolha sensata. Aqui está o exemplo atualizado:

```scss
// Defina seus tipos de media
$mediaTypes: (
  mobile: 576px,
  tablet: 768px,
  notebook: 992px,
  desktop: 1200px
);

// Mixin para media queries
@mixin media-type($type) {
  $media: map-get($mediaTypes, $type);
  @media only screen and (min-width: $media) {
    @content;
  }
}

// Exemplos de uso
.element {
  width: 100%;

  @include media-type(tablet) {
    width: 50%;
  }

  @include media-type(notebook) {
    width: 33.33%;
  }

  @include media-type(desktop) {
    width: 25%;
  }
}
```

Agora, os nomes dos tipos de media estão mais alinhados com os dispositivos que representam, tornando o código mais semântico e fácil de entender. Essa é uma boa prática para manter a clareza e a consistência no seu código Sass.