# Dicas e Boas Práticas de CSS

Este arquivo reúne as dicas e explicações sobre CSS que aprendemos durante o projeto.

## 1. Unidades de Medida (`rem` vs `px` vs `%`)

- **`px` (Pixel):** Unidade absoluta e fixa. Não é ideal para acessibilidade, pois não respeita as configurações de fonte do usuário.
- **`%` (Porcentagem):** Relativa ao elemento pai. Pode causar complexidade e "efeito cascata" indesejado.
- **`rem` (Root EM):** **A mais recomendada.** Relativa à fonte do elemento raiz (`html`). Garante que todo o layout escale de forma previsível e acessível.

**Conclusão:** Prefira `rem` para fontes e espaçamentos para criar layouts flexíveis e acessíveis.

## 2. Boas Práticas de Tipografia

Para parágrafos (`<p>`) e textos longos, foque na legibilidade:

- **`font-size`**: `1.1rem` é um bom ponto de partida para o corpo do texto.
- **`line-height`**: Essencial para dar "ar" ao texto. Use um valor entre `1.5` e `1.7` (sem unidade).
- **`color`**: Evite o preto puro (`#000`). Um cinza escuro como `#333` é mais confortável para os olhos em fundos claros.
- **`max-width`**: Limite a largura das linhas de texto para evitar cansaço visual. Use a unidade `ch` (largura do caractere '0'). Um valor entre `60ch` e `75ch` é o ideal.
  ```css
  .seu-bloco-de-texto p {
    max-width: 65ch;
  }
  ```

## 3. Media Queries para Responsividade

São a base do design responsivo. Permitem aplicar estilos diferentes com base no tamanho da tela.

```css
/* Desktop (padrão, sem media query) */
.container {
  width: 90%;
}

/* Tablet */
@media only screen and (max-width: 1024px) {
  .container {
    width: 95%;
  }
}

/* Mobile */
@media only screen and (max-width: 767px) {
  .container {
    width: 100%;
  }
}
```

## 4. Seletores de Atributo

Uma forma poderosa de selecionar elementos sem precisar de classes ou IDs específicos.

- `[class*="valor"]`: Seleciona elementos cuja classe **contenha** a string "valor".
- `[class^="valor"]`: Seleciona elementos cuja classe **comece com** a string "valor".
- `[class$="valor"]`: Seleciona elementos cuja classe **termine com** a string "valor".

**Exemplo prático:**
```css
/* Seleciona .company-1, .company-2, etc., de uma só vez */
[class*="company-"] {
  /* seus estilos aqui */
}
```

## 5. Controlando o Layout com Grid e Flexbox

- **`grid-area`**: No CSS Grid, esta propriedade posiciona um item em um local específico da grade. Isso ignora o fluxo automático. Para fazer os itens voltarem ao fluxo (por exemplo, em uma media query), resete a propriedade:
  ```css
  .meu-item-grid {
    grid-area: auto; /* Valor padrão */
  }
  ```

- **`order`**: No Flexbox, esta propriedade permite reordenar os itens visualmente, sem alterar a estrutura do HTML. É muito útil para layouts responsivos.
  ```css
  .item-que-vai-para-o-topo-no-mobile {
    order: -1; /* Um valor menor aparece primeiro */
  }
  ```

## 6. CSS Nesting (Aninhamento)

Permite aninhar seletores dentro de outros, de forma similar ao SASS/SCSS, tornando o código mais organizado e legível.

```css
/* Sem Nesting */
.article-container .article-details {
  text-align: left;
}
.article-container .article-details button {
  font-size: 1rem;
}

/* Com Nesting */
.article-container {
  .article-details {
    text-align: left;

    & > button { /* O '&' refere-se ao seletor pai (.article-details) */
      font-size: 1rem;
    }
  }
}
```
