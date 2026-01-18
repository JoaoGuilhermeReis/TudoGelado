#  Tudo Gelado - Landing Page

<div align="center">

![Status do Projeto](https://img.shields.io/badge/Status-Concluído-brightgreen)
![Licença](https://img.shields.io/badge/License-MIT-blue)
![Versão](https://img.shields.io/badge/Versão-5.0-orange)

**Uma experiência imersiva para venda de sobremesas artesanais com integração direta ao WhatsApp.**

[Ver Demo Online](#) · [Reportar Bug](#) · [Solicitar Feature](#)

</div>

---

##  Sobre o Projeto

O **Tudo Gelado** é uma Landing Page desenvolvida para uma confeitaria artesanal em Aracaju/SE. O objetivo do projeto foi criar uma interface moderna, responsiva e focada em conversão, eliminando barreiras entre a escolha do produto e o pedido final.

O design utiliza o conceito de **Glassmorphism** (efeito de vidro fosco) e conta com um **Carrinho de Compras em JavaScript** que gera o pedido automaticamente formatado para envio no WhatsApp.

###  Destaques Visuais
> "O design não é apenas o que parece e o que se sente. O design é como funciona." — Steve Jobs

*  **UI Moderna:** Tema escuro com gradientes e transparências.
*  **Scroll Reveal:** Animações suaves ao rolar a página (Intersection Observer).
*  **100% Responsivo:** Adapta-se perfeitamente a celulares e desktops.

---

##  Tecnologias Utilizadas

O projeto foi construído utilizando tecnologias nativas da web, garantindo leveza e alta performance.

| Tecnologia | Descrição | Uso Principal |
| :--- | :--- | :--- |
| ![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white) | Estrutura Semântica | Estrutura da página e SEO |
| ![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white) | Estilização Avançada | Glassmorphism, Flexbox, Grid e Animações |
| ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black) | Lógica de Programação | Lógica do carrinho, manipulação do DOM e Scroll Reveal |

---

##  Funcionalidades

- [x] **Catálogo de Produtos:** Exibição de cards com imagem, descrição, preço e status (Pronta entrega/Encomenda).
- [x] **Carrinho Lateral (Sidebar):**
    - Adicionar itens.
    - Contabilizar quantidade.
    - Remover itens.
    - Calcular total dinamicamente.
- [x] **Checkout via WhatsApp:** Transforma a lista do carrinho em uma mensagem de texto formatada e abre a API do WhatsApp.
- [x] **Animações de Entrada:** Elementos surgem na tela conforme o usuário desce a página.
- [x] **Redes Sociais:** Botões estilizados para Instagram e TikTok.

---

##  Exemplo de Código

Abaixo, um trecho da lógica que integra o carrinho ao WhatsApp, codificando a mensagem URL para garantir quebras de linha e caracteres especiais:

```javascript
function checkoutWhatsApp() {
    if (cart.length === 0) return showToast("Carrinho vazio!");

    let message = "Olá! Gostaria de fazer o pedido:\n\n";
    let total = 0;

    // Itera sobre o carrinho para montar a lista
    cart.forEach(item => {
        const itemTotal = item.price * item.quantity;
        message += `▪️ *${item.quantity}x ${item.name}* (R$ ${itemTotal.toFixed(2)})\n`;
        total += itemTotal;
    });

    message += `\n*Total: R$ ${total.toFixed(2)}*\n\nInforme a taxa de entrega.`;
    
    // Abre a API do WhatsApp
    const phone = "557981169223"; 
    window.open(`https://wa.me/${phone}?text=${encodeURIComponent(message)}`, '_blank');
}
