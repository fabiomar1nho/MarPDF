<div align="center">

# 📄 MarPDF

**Central de Ferramentas para PDF • Simples, Rápida e Segura**

Junte, divida, organize, converta, comprima e digitalize documentos em uma única página web,
**100% gratuita, sem login e com processamento local no navegador.**

[![Acessar o MarPDF](https://img.shields.io/badge/Acessar-MarPDF-FDD405?style=for-the-badge&labelColor=001561)](https://fabiomar1nho.github.io/MarPDF/)
[![Licença MIT](https://img.shields.io/badge/Licen%C3%A7a-MIT-FDD405?style=for-the-badge&labelColor=001561)](LICENSE)

</div>

---

## Sumário

- [Visão geral](#visão-geral)
- [Ferramentas](#ferramentas)
- [Scanner com câmera](#scanner-com-câmera)
- [Privacidade](#privacidade)
- [Internet e uso offline](#internet-e-uso-offline)
- [Como usar](#como-usar)
- [Tecnologias](#tecnologias)
- [Identidade visual](#identidade-visual)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Compatibilidade e permissões](#compatibilidade-e-permissões)
- [Problemas comuns](#problemas-comuns)
- [Limitações e melhorias futuras](#limitações-e-melhorias-futuras)
- [Autor](#autor)
- [Licença](#licença)
- [Créditos](#créditos)

## Visão geral

O MarPDF é uma aplicação web de **arquivo único** (`index.html`) que reúne as principais ferramentas para PDF e imagens em um só lugar:

- **Gratuito e sem login:** sem cadastro, senha, cartão, assinatura ou anúncios.
- **Processamento local:** PDFs e imagens são lidos e gerados no seu próprio navegador; o código não envia os documentos a servidores.
- **Mobile-first:** layout responsivo para celular, tablet e computador, com menu em hambúrguer no celular.
- **Tema escuro único**, com identidade visual própria (azul-marinho e amarelo).
- **Central de Ajuda integrada**, com busca local, categorias e ajuda por ferramenta.

## Ferramentas

| Ferramenta | O que faz |
|---|---|
| 📷 **Scanner** | Captura páginas com a câmera (ou da galeria), recorta, aplica filtros e gera um PDF. |
| 📎 **Juntar PDFs** | Une vários PDFs; mostra o número de páginas de cada arquivo, reordena (alça ☰ ou setas), remove e define o nome do arquivo final. |
| ✂️ **Dividir / Extrair** | Extrai páginas por intervalos (`1-3, 5, 8-10`; `8-` vai até o fim) em um novo PDF. |
| 🗂️ **Organizar páginas** | Miniaturas reais (PDF.js); reordena, gira 90° e exclui páginas, mostrando a posição nova e a original. |
| 🖼️ **Imagens para PDF** | Converte PNG, JPG e WEBP; folha proporcional, A4 ou Carta; retrato/paisagem; margem de 0 a 50 mm. |
| 🖼️ **PDF para imagens** | Converte páginas (todas ou por intervalo) em PNG ou JPG, de 72 a 300 dpi, com download individual ou em ZIP. |
| 🗜️ **Comprimir PDF** | Otimiza a estrutura ou rasteriza as páginas em JPEG (150, 110 ou 80 dpi); mostra o tamanho antes e depois e só oferece o download se o arquivo realmente diminuir. |
| 🖨️ **Preparar para impressão** | Ajusta o PDF para A4 ou Carta, com margem de segurança em pontos e encaixe "Conter" ou "Preencher". |
| ❓ **Central de Ajuda** | FAQ com busca por palavras-chave e sinônimos, categorias, ajuda específica de cada ferramenta e tutorial de atalho na tela inicial. |

> Em **Comprimir PDF**, os níveis Leve/Média/Alta transformam cada página em imagem: o arquivo diminui mais, mas o texto deixa de ser selecionável e pesquisável. "Só otimizar a estrutura" mantém o texto, mas costuma economizar pouco. O resultado varia conforme o PDF.

## Scanner com câmera

Fluxo contínuo, sem trocar de tela entre uma página e outra:

1. **Câmera → edição imediata.** "Abrir câmera" usa o visor ao vivo (`MediaDevices`, câmera traseira); também há "Câmera nativa" (`input capture`) e "Da galeria". Cada foto abre na hora em um editor de tela cheia com:
   - recorte com **Cropper.js** (a moldura "gruda" nas bordas da foto);
   - filtros em tempo real: **Original**, **Magic Color**, **Documento P&B** e **Escala de cinza**;
   - rotação de 90°, brilho e contraste;
   - **Refazer Foto** ou **Confirmar Página ➔**.
2. **Ciclo de páginas.** Ao confirmar, a câmera volta automaticamente, com o contador "📸 N Páginas Digitalizadas" e o botão "Concluir / Ver Todas as Páginas (N)".
3. **Páginas do lote.** Miniaturas reordenáveis (mouse ou toque), exclusão, edição individual, "Aplicar este filtro a todas as páginas", "Adicionar fotos" e pré-visualização da ordem final.
4. **Exportar.** Nome do arquivo (padrão `Documento_ano-mês-dia_hora-minuto`), tamanho da página (proporcional, A4 ou Carta), orientação, margens (sem margem, 5 mm ou 10 mm), **Salvar e Baixar PDF** e **Compartilhar PDF** (Web Share API, disponível só em navegadores que permitem compartilhar arquivos).

**Recursos experimentais e opcionais:** "Automático" (sugere a moldura sobre a folha) e "Perspectiva" (4 pontos arrastáveis para endireitar a imagem) usam o **OpenCV.js**, carregado somente quando você os aciona. Nada é aplicado sem a sua confirmação, a foto original é mantida e, se a detecção falhar, o recorte manual continua disponível.

Sair do scanner (ou cancelar) reinicia a ferramenta por completo: libera a câmera, destrói o Cropper e descarta as páginas, sem precisar recarregar a página.

## Privacidade

- PDFs, imagens e nomes de arquivos **não são enviados** a servidores pelo código do MarPDF.
- A rede é usada apenas para baixar as bibliotecas das CDNs (listadas em [Tecnologias](#tecnologias)); os provedores dessas CDNs podem ver as requisições de download.
- Não há analytics, anúncios nem rastreamento, e o MarPDF não guarda documentos nem preferências no aparelho.

## Internet e uso offline

- A primeira abertura **precisa de internet**, porque as bibliotecas vêm de CDNs.
- Com as bibliotecas carregadas, as operações de cada ferramenta rodam no navegador sem usar a conexão durante a sessão.
- O repositório inclui `manifest.json` e ícones, mas **não há service worker**. Por isso, o MarPDF não oferece cache offline próprio: ao fechar a página, será preciso internet de novo (salvo cache do navegador, que não é garantido).
- O OpenCV.js só é baixado se você usar "Automático" ou "Perspectiva", e exige internet nesse momento.
- Uma etiqueta de aviso aparece em uma ferramenta apenas quando ela precisa de internet para carregar ou está indisponível, e o ponto colorido no topo indica o estado da conexão.

## Como usar

**Online:** acesse **https://fabiomar1nho.github.io/MarPDF/**

**Localmente:**

```bash
git clone https://github.com/fabiomar1nho/MarPDF.git
cd MarPDF
```

Abra o `index.html` no navegador. Para testar a câmera ao vivo, sirva a pasta por `localhost` ou HTTPS (o visor ao vivo exige um contexto seguro):

```bash
python -m http.server 8000
# depois acesse http://localhost:8000
```

**Atalho na tela inicial do celular:** abra o MarPDF no Chrome (menu ⋮ → "Adicionar à tela inicial") ou no Safari (Compartilhar → "Adicionar à Tela de Início"). O passo a passo também está na Central de Ajuda do app.

## Tecnologias

| Biblioteca | Versão | Uso |
|---|---|---|
| [Tailwind CSS](https://tailwindcss.com/) (CDN Play) | 3.4.17 | Estilo e tema escuro |
| [Font Awesome](https://fontawesome.com/) | 6.5.1 | Ícones |
| [PDF-Lib](https://pdf-lib.js.org/) | 1.17.1 | Criar, unir, extrair e girar PDFs |
| [PDF.js](https://mozilla.github.io/pdf.js/) | 3.11.174 | Miniaturas e renderização das páginas |
| [Cropper.js](https://fengyuanchen.github.io/cropperjs/) | 1.6.1 | Recorte manual |
| [JSZip](https://stuk.github.io/jszip/) | 3.10.1 | ZIP das imagens (PDF para imagens) |
| [OpenCV.js](https://docs.opencv.org/) | 4.9.0 (sob demanda) | Detecção de bordas e correção de perspectiva |
| Google Fonts: Press Start 2P | — | Fonte do logotipo |


## Estrutura do projeto

```
MarPDF/
├── assets/          # ícones e imagens (favicons, logotipo)
├── index.html       # aplicação completa (HTML, CSS e JavaScript)
├── manifest.json    # manifesto web do aplicativo
├── LICENSE          # licença MIT
└── README.md        # este arquivo
```

## Compatibilidade e permissões

Pensado para navegadores modernos em computador, tablet e celular. Ainda não há testes automatizados nem uma bateria documentada de testes em navegadores reais, então teste no seu ambiente.

- **Câmera:** exige permissão do navegador; o visor ao vivo geralmente exige HTTPS ou `localhost`.
- **Compartilhar PDF:** depende de navegadores que suportam a Web Share API com arquivos.
- **Detecção de bordas:** depende de WebAssembly e de memória suficiente.

## Problemas comuns

- **Ferramenta "indisponível" ou "precisa de internet para carregar":** uma biblioteca não carregou. Conecte-se e recarregue a página.
- **PDF não abre:** pode estar corrompido ou exigir senha para abrir.
- **Câmera não abre:** verifique as permissões ou use "Câmera nativa" / "Da galeria".
- **Bordas não detectadas:** ajuste a moldura manualmente ou use "Perspectiva"; ajudam fundo contrastante e boa iluminação.
- **Documento grande trava:** divida o PDF antes; em "Organizar" as miniaturas consomem bastante memória.

## Limitações e melhorias futuras

Ainda **não implementados**:

- informações e metadados do PDF;
- busca e filtros por categoria na tela de ferramentas;
- PDFs protegidos por senha de abertura;
- uso offline permanente (service worker ou bibliotecas embutidas);
- pré-visualização antes de juntar ou dividir.

## Autor

- GitHub: [@fabiomar1nho](https://github.com/fabiomar1nho)
- Instagram: [@fabio_mar1nho](https://www.instagram.com/fabio_mar1nho/)

## Licença

Distribuído sob a licença **MIT**. Veja o arquivo [LICENSE](LICENSE).

## Créditos

Construído com [PDF-Lib](https://pdf-lib.js.org/), [PDF.js](https://mozilla.github.io/pdf.js/), [Cropper.js](https://fengyuanchen.github.io/cropperjs/), [JSZip](https://stuk.github.io/jszip/), [OpenCV.js](https://docs.opencv.org/), [Tailwind CSS](https://tailwindcss.com/) e [Font Awesome](https://fontawesome.com/).
