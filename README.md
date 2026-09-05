# bot-follow-instagram-js

Um script simples em JavaScript para automatizar o processo de seguir perfis no Instagram diretamente pelo console do navegador, com intervalo configurado para evitar bloqueios imediatos da plataforma.

## 📌 Funcionalidades

- **Seleção Dinâmica:** Localiza os botões de ação de seguir presentes no DOM da página.
- **Verificação de Status:** Ignora perfis que você já segue antes de disparar o clique.
- **Temporizador com Delay:** Executa as ações com intervalo progressivo (10 segundos entre cada clique) para desacelerar o fluxo de automação.
- **Contador em Tempo Real:** Registra no console a quantidade de perfis seguidos com sucesso.

## 🛠️ Tecnologias Utilizadas

- **JavaScript (ES6+)**
- **Google Chrome DevTools** (ou qualquer navegador baseado em Chromium)

## 🚀 Como Usar

Não é necessário instalar bibliotecas ou configurar dependências externas. O script roda diretamente no navegador:

1. Acesse o [Instagram](https://www.instagram.com) pelo navegador e faça login na sua conta.
2. Navegue até a lista de seguidores/seguindo de um perfil ou abra uma lista de sugestões.
3. Abra as Ferramentas do Desenvolvedor:
   - Pressione `F12` ou `Ctrl + Shift + I` (Windows/Linux) / `Cmd + Option + I` (macOS).
4. Clique na aba **Console**.
5. Copie e cole o código abaixo no console e pressione **Enter**:

```javascript
let counter = 0;
let arr = document.querySelectorAll("._8A5w5, .L3NKy"); // Seleciona os seletores da interface

arr.forEach((v, i) => {
  setTimeout(() => {
    if (!v.classList.contains("_8A5w5")) {
      v.click();
      counter++;
      console.log(`Perfis seguidos até o momento: ${counter}`);
    } else {
      console.log("Você já segue este usuário.");
    }
  }, i * 10000);
});
```

## ⚠️ Avisos Importantes

* **Limitações de API e Ação:** O Instagram monitora ações repetitivas e em massa. O uso excessivo pode resultar em bloqueios temporários de ação (*Action Block*) ou restrições na conta.
* **Classes CSS Dinâmicas:** As classes do Instagram (como `.L3NKy` e `._8A5w5`) são ofuscadas e alteradas periodicamente pelo Meta. Caso o script pare de encontrar os botões, inspecione o elemento do botão "Seguir" atual e atualize as classes no `querySelector`.
* **Finalidade Educacional:** Este projeto foi criado estritamente para fins educacionais e experimentação com manipulação de DOM via DevTools.

## 📄 Licença

Este projeto está sob a licença [MIT](ICENSE). Consulte o arquivo `LICENSE` para mais detalhes.
