# MarPDF — Central Gratuita de Ferramentas para PDF em HTML5

> Uma suíte completa, moderna, rápida e 100% gratuita de ferramentas para manipulação de arquivos PDF e imagens, executada diretamente no navegador sem necessidade de cadastro, login ou servidores externos.

---

## 📋 Sumário

1. [Visão Geral](#-visão-geral)
2. [Princípios Fundamentais](#-princípios-fundamentais)
3. [Stack Tecnológica](#-stack-tecnológica)
4. [Ferramentas Disponíveis](#-ferramentas-disponíveis)
5. [Sistema de Disponibilidade (Online/Offline)](#-sistema-de-disponibilidade-onlineoffline)
6. [Privacidade e Processamento Local](#-privacidade-e-processamento-local)
7. [Acessibilidade e Experiência do Usuário (UX)](#-acessibilidade-e-experiência-do-usuário-ux)
8. [Como Usar e Instalar no Celular](#-como-usar-e-instalar-no-celular)
9. [Central de Ajuda e FAQ](#-central-de-ajuda-e-faq)
10. [Autor](#-autor)
11. [Divulgação do Uso de IA (Transparência)](#-divulgação-do-uso-de-ia-transparência)
12. [Licença](#-licença)

---

## 🎯 1. Visão Geral

O **MarPDF** é uma aplicação web desenvolvida para simplificar o manuseio de documentos PDF por qualquer tipo de usuário — desde profissionais experientes até pessoas com pouca familiaridade com tecnologia (incluindo idosos). 

Com uma interface inspirada na organização visual de referências de mercado, o MarPDF possui identidade própria, design limpo, suporte a **tema claro e escuro**, responsividade avançada e uma experiência fluida em computadores, tablets e smartphones.

---

## 🔑 2. Princípios Fundamentais

* **100% Gratuito:** Sem paywalls, assinaturas, créditos limitados ou recursos bloqueados.
* **Sem Login ou Cadastro:** Acesso imediato a todas as ferramentas sem exigir e-mail, senhas ou criação de contas.
* **Transparência Total:** Cada ferramenta exibe claramente o seu status de funcionamento (offline, dependência de carregamento inicial ou conexão ativa).

---

## 🛠️ 3. Stack Tecnológica

O projeto foi construído com foco em alta performance e manutenibilidade, utilizando tecnologias web modernas:

* **HTML5 Semantic** & **CSS3 Moderno** (Variáveis CSS, Flexbox, Grid Layout, Design System próprio).
* **JavaScript (ES6+)** puro e modular para manipulação de eventos, DOM e lógica de processamento.
* **Bibliotecas Especializadas (via CDN):**
  * `PDF-lib`: Criação, junção, divisão e modificação estrutural de arquivos PDF.
  * `PDF.js`: Renderização de páginas de PDF em miniaturas e imagens no navegador.
  * `Cropper.js`: Recorte e ajuste de imagens e fotografias no scanner.
  * `JSZip`: Compactação e empacotamento de múltiplos arquivos para download em lote (ZIP).

---

## 🧰 4. Ferramentas Disponíveis

| Categoria | Ferramenta | Descrição Resumida |
| :--- | :--- | :--- |
| **Organizar** | **Juntar PDF** | Combina múltiplos arquivos PDF em um único documento, com reordenação interativa. |
| **Organizar** | **Dividir PDF** | Separa um documento por intervalos de páginas específicos (`1-3, 5, 8-10`). |
| **Organizar** | **Extrair Páginas** | Gera um novo arquivo contendo apenas as páginas selecionadas pelo usuário. |
| **Organizar** | **Organizar Páginas** | Visualiza miniaturas reais, permite girar em 90°, excluir e reordenar páginas. |
| **Otimizar** | **Comprimir PDF** | Reduz o tamanho do documento com diferentes níveis de intensidade e feedback percentual. |
| **Converter** | **Imagens para PDF** | Converte PNG, JPG, JPEG e WEBP em PDF com escolha de formato (A4/Carta) e margens. |
| **Converter** | **PDF para Imagens** | Converte páginas de PDF em arquivos PNG ou JPG individuais ou compactados em ZIP. |
| **Digitalizar** | **Scanner com Câmera** | Fotografa documentos usando a câmera do dispositivo, com recorte (`Cropper.js`), ajuste de brilho/contraste e filtro P&B. |
| **Impressão** | **Preparar para Impressão**| Otimiza margens, orientação e escala para envio à impressora do navegador. |
| **Utilidades** | **Informações do PDF** | Exibe metadados, contagem de páginas, dimensões e tamanho do arquivo. |

---

## 📡 5. Sistema de Disponibilidade (Online / Offline)

O MarPDF implementa um verificador dinâmico de dependências que exibe etiquetas visuais em cada cartão e dentro de cada ferramenta:

* **`✓ FUNCIONA OFFLINE`**: Pronta para uso imediato sem conexão.
* **`⚡ OFFLINE APÓS O CARREGAMENTO`**: Funciona sem internet após o carregamento inicial das bibliotecas via CDN.
* **`🌐 PRECISA DE INTERNET PARA CARREGAR`**: Requer conexão momentânea para baixar os recursos externos necessários.
* **`⚠ PRECISA DE INTERNET DURANTE O USO`**: Utilizada estritamente quando a operação exige requisições ativas.

Um **indicador de conectividade** no cabeçalho monitora em tempo real os eventos `online`/`offline` do navegador, informando o usuário caso a rede caia e preservando os arquivos em andamento.

---

## 🔒 6. Privacidade e Processamento Local

* **Privacidade Absoluta:** O processamento dos documentos ocorre inteiramente no cliente (*client-side*), utilizando a memória e o poder de processamento do seu próprio dispositivo.
* **Zero Upload Externo:** Seus arquivos, nomes de documentos ou dados pessoais **nunca** são enviados para servidores externos, garantindo total conformidade com boas práticas de privacidade.

---

## ♿ 7. Acessibilidade e Experiência do Usuário (UX)

* **Feedback Visual Detalhado:** Progresso em tempo real, estados de leitura de arquivos, avisos claros de sucesso e tratamento robusto de erros.
* **Acessibilidade (a11y):** Contraste adequado, tamanhos de fontes confortáveis, foco visível para navegação por teclado e atributos `aria-live` para leitores de tela.
* **Filtros e Busca Instantânea:** Caixa de pesquisa dinâmica na página inicial para encontrar ferramentas pelo nome ou palavra-chave.

---

## 📱 8. Como Usar e Instalar no Celular

O MarPDF pode ser aberto diretamente em qualquer navegador moderno. Para acesso rápido, você pode adicioná-lo à tela inicial do seu smartphone:

### 🤖 Android (Google Chrome)
1. Abra o MarPDF no Google Chrome.
2. Toque no ícone de três pontinhos (`⋮`) no canto superior direito.
3. Selecione **"Adicionar à tela inicial"** ou **"Instalar aplicativo"**.
4. Confirme o nome e toque em **Adicionar**.

### 🍎 iPhone / iPad (Safari)
1. Abra o MarPDF no Safari.
2. Toque no botão **Compartilhar** (quadrado com uma seta para cima).
3. Role as opções e toque em **"Adicionar à Tela de Início"**.
4. Confirme tocando em **Adicionar**.

---

## ❓ 9. Central de Ajuda e FAQ

O aplicativo conta com uma **Central de Ajuda integrada** com barra de busca local, dividida em categorias para esclarecer dúvidas sobre:
* Gratuidade e ausência de login.
* Funcionamento offline e dependências.
* Privacidade e segurança dos dados.
* Passo a passo para utilização de cada ferramenta.
* Solução de problemas comuns e compatibilidade de navegadores.

Cada ferramenta possui também um botão dedicado **"Como usar esta ferramenta?"** com orientações contextuais rápidas.

---

## 👤 10. Autor

Desenvolvido por **Mar1nho**.

---

## 🤖 11. Divulgação do Uso de IA (Transparência)

Transparência e integridade são valores essenciais para este projeto. Durante o desenvolvimento do **MarPDF**, ferramentas de Inteligência Artificial (IA) foram utilizadas como assistentes no fluxo de trabalho (*pair-programming*), atuando estritamente para acelerar etapas de codificação, diagnosticar erros e lidar com tarefas repetitivas.

### Como a IA foi utilizada neste projeto:
- **Desenvolvimento e Manipulação do DOM:** Auxílio na estruturação de código performático em Vanilla JavaScript, HTML5 e CSS3, além de pesquisas de sintaxe para a integração de bibliotecas *client-side* (como `PDF-lib`, `PDF.js`, `Cropper.js` e `JSZip`).
- **Documentação e Central de Ajuda:** Elaboração de rascunhos para este `README.md` e estruturação dos conteúdos explicativos da Central de Ajuda e FAQ integrada.

### Supervisão e Direção Humana:
Embora a IA tenha acelerado significativamente o fluxo de trabalho e eliminado atritos técnicos, toda a idealização, definição das regras de negócio, testes de usabilidade, validação de segurança do processamento local e decisões arquitetônicas foram inteiramente conduzidas e validadas por intervenção humana. A IA serviu como uma ferramenta complementar de apoio à execução, permitindo que o foco do desenvolvimento permanecesse na acessibilidade, estabilidade e na criação de valor real para o usuário final.

---

## 📄 12. Licença

Este projeto é distribuído sob a licença **MIT**, sendo livre para uso, estudo e compartilhamento sem restrições comerciais.
