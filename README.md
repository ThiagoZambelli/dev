# Scribo

![Scribo Logo Placeholder](https://via.placeholder.com/150/0000FF/FFFFFF?text=Scribo)

Bem-vindo ao **Scribo**, uma plataforma inspirada no conceito do Pinterest, mas totalmente focada em textos! Aqui, autores e leitores podem compartilhar, descobrir e organizar poemas, contos e histórias — sejam eles completos ou ainda em andamento. Nosso objetivo é criar uma comunidade vibrante onde a escrita floresce e é facilmente acessível.

---

## 📚 **Sobre o Projeto**

O Scribo nasceu da ideia de dar um espaço dedicado à palavra escrita. Imagine um mural infinito de criatividade, onde cada "pin" é um texto, esperando para ser lido, apreciado e salvo. Nossa plataforma permite que os usuários:

* **Publiquem** suas próprias obras.
* **Descubram** novos talentos e histórias.
* **Organizem** seus textos favoritos em "pastas" pessoais.
* **Interajam** com outros amantes da escrita.
* **Explorem** comunidades temáticas e tags específicas.

---

## ✨ **Tecnologias Utilizadas**

Este projeto é construído com um foco em performance, escalabilidade e facilidade de desenvolvimento.

* **Frontend:**
    * **React:** Biblioteca JavaScript para a construção de interfaces de usuário dinâmicas e reativas.
* **Backend & Banco de Dados (MVP Inicial):**
    * **Firebase Authentication:** Para um sistema robusto e seguro de cadastro e login de usuários.
    * **Firestore (Firebase Database):** Banco de dados NoSQL flexível e escalável para armazenar todos os dados da plataforma (textos, usuários, comunidades, etc.).
    * **Firebase Storage:** Para armazenamento de arquivos de mídia, como fotos de perfil e capas.
* **Backend (Futura Migração):**
    * **Node.js:** Para um backend customizável, permitindo maior controle sobre a lógica de negócios e APIs no futuro.

---

## 🚀 **Como Começar**

Siga estas instruções para configurar e rodar o projeto Scribo em sua máquina local.

### **Pré-requisitos**

Certifique-se de ter as seguintes ferramentas instaladas:

* **Node.js** (versão LTS recomendada)
* **npm** (gerenciador de pacotes do Node.js, geralmente vem com o Node.js) ou **Yarn**

### **Configuração do Ambiente**

1.  **Clone o Repositório:**
    ```bash
    git clone [https://github.com/seu-usuario/scribo.git](https://github.com/seu-usuario/scribo.git)
    cd scribo
    ```
    *(Substitua `https://github.com/seu-usuario/scribo.git` pelo link real do seu repositório quando ele existir.)*

2.  **Instale as Dependências:**
    ```bash
    npm install
    # ou se preferir yarn
    # yarn install
    ```

3.  **Configuração do Firebase:**
    * Crie um novo projeto no [Console do Firebase](https://console.firebase.google.com/).
    * Adicione um aplicativo web ao seu projeto Firebase e copie o objeto de configuração.
    * No diretório `src/` do seu projeto React, crie um arquivo chamado `firebaseConfig.js`.
    * Cole o objeto de configuração copiado neste arquivo, garantindo que ele tenha o seguinte formato (substitua os `YOUR_...` pelos seus dados):

    ```javascript
    // src/firebaseConfig.js
    import { initializeApp } from 'firebase/app';
    import { getAuth } from 'firebase/auth';
    import { getFirestore } from 'firebase/firestore';
    import { getStorage } from 'firebase/storage'; // Para o Firebase Storage

    const firebaseConfig = {
      apiKey: "YOUR_API_KEY",
      authDomain: "YOUR_AUTH_DOMAIN",
      projectId: "YOUR_PROJECT_ID",
      storageBucket: "YOUR_STORAGE_BUCKET",
      messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
      appId: "YOUR_APP_ID"
    };

    const app = initializeApp(firebaseConfig);

    export const auth = getAuth(app);
    export const db = getFirestore(app);
    export const storage = getStorage(app); // Exporta o Storage para uso futuro com imagens
    ```

    * **Habilite o Firestore:** No console do Firebase, vá em `Firestore Database` e clique em `Criar banco de dados`. Escolha o modo `start in production mode` (ou test mode se preferir, mas ajuste as regras de segurança depois) e selecione a localização do servidor.
    * **Habilite o Authentication:** No console do Firebase, vá em `Authentication` e clique em `Get started`. Habilite o método de login `Email/Password` para começar.
    * **Habilite o Storage:** No console do Firebase, vá em `Storage` e clique em `Get started`.

4.  **Rodar o Aplicativo:**
    ```bash
    npm start
    # ou
    # yarn start
    ```
    O aplicativo será aberto no seu navegador padrão em `http://localhost:3000`.

---

## 📂 **Estrutura do Banco de Dados (Firestore)**

Nossa base de dados é organizada nas seguintes coleções principais:

* **`users`**: Armazena os perfis dos usuários.
    * Campos: `username`, `nome`, `email`, `idade`, `capaUrl`, `fotoPerfilUrl`, `seguidores` (array de UIDs), `seguindo` (array de UIDs), `tagsFavoritas` (array), `foldersFavoritos` (array de IDs).
* **`posts`**: Contém os textos publicados.
    * Campos: `userId` (ID do autor), `titulo`, `conteudo`, `tags` (array), `dataCriacao`, `status` (ex: 'publicado', 'rascunho').
    * *Subcoleção (futura):* `comments` (para comentários de um post específico).
* **`communities`**: Informações sobre as comunidades.
    * Campos: `nome`, `descricao`, `membros` (array de UIDs), `postagens` (array de IDs de posts), `dataCriacao`, `criadorId`.
* **`tags`**: Gerencia as tags disponíveis.
    * Campos: `nome`, `classe`, `stickerUrl`, `popularidade`.
* **`folders`**: Pastas criadas pelos usuários para organizar textos.
    * Campos: `userId` (dono da pasta), `nome`, `descricao`, `textosContidos` (array de IDs de posts), `dataCriacao`, `publica` (boolean).

---

## 🤝 **Contribuição**

Estamos abertos a contribuições! Se você quiser melhorar o Scribo, siga os passos abaixo:

1.  Faça um `fork` do projeto.
2.  Crie uma nova `branch` para sua funcionalidade (`git checkout -b feature/minha-nova-feature`).
3.  Faça suas mudanças e teste-as.
4.  Comite suas mudanças (`git commit -m 'feat: Minha nova funcionalidade incrível'`).
5.  Envie para o `origin` (`git push origin feature/minha-nova-feature`).
6.  Abra um `Pull Request`.

---

## 📄 **Licença**

Este projeto está sob a licença [MIT](https://opensource.org/licenses/MIT).

---

## ✉️ **Contato**

Para dúvidas ou sugestões, entre em contato através do meu perfil do GitHub.

---# Scribo
