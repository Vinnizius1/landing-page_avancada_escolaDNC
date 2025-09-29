# Lições Aprendidas: CSS Responsivo

## Ruim 👎 (Valores fixos com `px`)

Usar `px` (pixels) para fontes e espaçamentos cria um layout rígido. Se um usuário aumentar o tamanho da fonte padrão no navegador, o layout quebra, pois os pixels não se ajustam.

```css
.card {
  font-size: 16px;
  padding: 20px;
  border-radius: 8px;
}
```

---

## Bom 👍 (Valores relativos com `rem`)

Usar `rem` torna o layout flexível. As medidas são relativas ao tamanho da fonte raiz (`html`). Se o usuário alterar a fonte padrão, toda a interface se ajusta proporcionalmente, garantindo acessibilidade e uma boa experiência.

```css
html {
  font-size: 16px; /* Define a base */
}

.card {
  font-size: 1rem;    /* 1 * 16px = 16px */
  padding: 1.25rem; /* 1.25 * 16px = 20px */
  border-radius: 0.5rem; /* 0.5 * 16px = 8px */
}
```

---

## Efeito Visual ✨ (Gradiente de Fundo)

Para criar um fundo com uma transição suave de cores, usamos `linear-gradient`. É uma forma simples de adicionar profundidade e um toque profissional ao design sem precisar de imagens.

Neste exemplo, um gradiente vertical (`180deg`) vai do branco (`#fff`) para um cinza claro (`#d9d9d9`), criando um efeito sutil.

```css
.background-gradient {
  background: linear-gradient(180deg, #fff, #d9d9d9);
}
```

---

## Imagens: Conteúdo (HTML) vs. Decoração (CSS)

Uma decisão importante no desenvolvimento web é onde colocar as imagens. A regra geral é:

- **HTML para conteúdo:** Imagens que são essenciais para a compreensão do conteúdo, como fotos de perfil, imagens de posts ou diagramas, devem estar no HTML usando a tag `<img>`. Isso ocorre porque elas têm **valor semântico**. Leitores de tela as descrevem para usuários com deficiência visual (usando o atributo `alt`), e os motores de busca as indexam.

- **CSS para decoração:** Imagens que são puramente estéticas, como texturas de fundo ou ícones decorativos, devem ser aplicadas no CSS com a propriedade `background-image`. Elas não adicionam informação, apenas enfeitam a página. Mantê-las no CSS separa a apresentação do conteúdo, tornando o código mais limpo e fácil de manter. Se a imagem não carregar, o conteúdo principal não é afetado.

Neste projeto, as fotos dos posts e do usuário estão no HTML, enquanto a imagem de fundo está no CSS, seguindo exatamente essa boa prática.