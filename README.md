# MarPDF

**Central de Ferramentas para PDF • Simples, Rápida e Segura**

O MarPDF é uma aplicação web de arquivo único (`index.html`) que reúne ferramentas para PDF e imagens. Ela é gratuita, não tem login nem cadastro e processa os documentos no próprio navegador, sem enviá-los a servidores.

> Desenvolvido com ❤️ por MAR1NHO

## Sumário

- [Ferramentas](#ferramentas)
- [Scanner com câmera](#scanner-com-câmera)
- [Internet e funcionamento offline](#internet-e-funcionamento-offline)
- [Privacidade](#privacidade)
- [Como executar](#como-executar)
- [Tecnologias](#tecnologias)
- [Compatibilidade e permissões](#compatibilidade-e-permissões)
- [Problemas comuns](#problemas-comuns)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Limitações e melhorias futuras](#limitações-e-melhorias-futuras)
- [Créditos](#créditos)

## Ferramentas

| Ferramenta | O que faz | Situação |
|---|---|---|
| **Scanner** | Captura fotos (câmera ou galeria), recorta, aplica filtros e gera um PDF | Concluída |
| **Juntar PDFs** | Une vários PDFs; mostra páginas de cada arquivo; reordena (alça ☰ ou setas), remove e define o nome do arquivo final | Concluída |
| **Dividir / Extrair** | Extrai páginas por intervalos (`1-3, 5, 8-10`; `8-` vai até o fim) em um novo PDF | Concluída |
| **Organizar páginas** | Miniaturas reais (PDF.js); reordena, gira 90° e exclui páginas; mostra posição nova e original | Concluída |
| **Imagens para PDF** | PNG, JPG e WEBP; folha A4, Carta ou proporcional; retrato/paisagem; margem de 0 a 50 mm | Concluída |
| **PDF para imagens** | Converte páginas (todas ou por intervalo) em PNG ou JPG, 72 a 300 dpi, com download individual ou ZIP | Concluída |
| **Comprimir PDF** | Otimiza a estrutura ou rasteriza as páginas em JPEG (150/110/80 dpi); mostra tamanho antes/depois e só oferece o download se o arquivo diminuir | Concluída |
| **Preparar para impressão** | Ajusta para A4 ou Carta com margem em pontos; encaixe "Conter" ou "Preencher" | Concluída |
| **Central de Ajuda** | FAQ com busca local, categorias, ajuda por ferramenta e tutorial de atalho na tela inicial | Concluída |

Uma etiqueta de aviso só aparece em uma ferramenta quando ela precisa de internet para carregar ou está indisponível (calculado a partir das bibliotecas realmente carregadas). O painel “Disponibilidade desta ferramenta” e o indicador de conexão no topo dão os detalhes.

## Scanner com câmera

Fluxo contínuo, sem trocar de tela entre uma página e outra:

1. **Câmera → edição imediata:** "Abrir câmera" usa o visor ao vivo (`MediaDevices`, câmera traseira); há também "Câmera nativa" (`input capture`) e "Da galeria". Cada foto abre na hora em um editor de tela cheia com recorte (Cropper.js, moldura que "gruda" nas bordas), filtros em tempo real (Original, Magic Color, Documento P&B, Escala de cinza), rotação de 90° e brilho/contraste. Ações: **Refazer Foto** ou **Confirmar Página ➔**. Opcionais e experimentais: "Automático" e "Perspectiva" (OpenCV.js sob demanda; nada é aplicado sem confirmação e a foto original é mantida).
2. **Ciclo de páginas:** ao confirmar, a câmera volta automaticamente, com o contador "📸 N Páginas Digitalizadas" e o botão "Concluir / Ver Todas as Páginas (N)".
3. **Páginas do lote:** miniaturas reordenáveis (alça ☰, mouse ou toque), exclusão, edição individual, "Aplicar este filtro a todas as páginas", "Adicionar fotos" e pré-visualização da ordem final.
4. **Exportar:** nome (padrão `Documento_ano-mês-dia_hora`), tamanho (proporcional, A4 ou Carta), orientação, margens (sem margem, 5 mm ou 10 mm), "Salvar e Baixar PDF" e "Compartilhar PDF" (Web Share API; disponível só em navegadores que permitem compartilhar arquivos).

## Internet e funcionamento offline

O MarPDF **não é um PWA**: não há manifesto nem service worker. As bibliotecas vêm de CDNs, portanto:

- A primeira abertura precisa de internet.
- Com as bibliotecas carregadas, as operações não usam a conexão durante a sessão.
- Ao fechar a página, será preciso internet de novo, salvo cache do navegador, que não é garantido.
- O OpenCV.js (detecção de bordas) só é baixado se a opção for ativada e exige internet nesse momento.

Para uso offline permanente seria necessário embutir as bibliotecas ou adicionar um service worker (veja as melhorias futuras).

## Privacidade

- PDFs e imagens são lidos e gerados no navegador; o código não envia documentos nem nomes de arquivos a servidores.
- A rede é usada apenas para baixar bibliotecas das CDNs listadas abaixo (os provedores dessas CDNs podem ver as requisições de download).
- Não há analytics, anúncios nem rastreamento.
- O único dado salvo no aparelho é a preferência de tema, em `localStorage`.

## Como executar

1. Salve `index.html` e abra no navegador (com internet na primeira carga).
2. Para o **atalho na tela inicial do celular**, publique o arquivo em um endereço web (HTTPS), pois um arquivo guardado só no aparelho pode não abrir pelo atalho.
3. O botão *Capturar página* usa o seletor de arquivos com câmera do aparelho. Se o navegador não abrir a câmera, use *Da galeria*.

## Tecnologias

| Biblioteca | Versão | Uso |
|---|---|---|
| Tailwind CSS (CDN Play) | 3.4.17 | Estilo e tema claro/escuro |
| Font Awesome | 6.5.1 | Ícones |
| PDF-Lib | 1.17.1 | Criar, unir, extrair e girar PDFs |
| PDF.js | 3.11.174 | Miniaturas das páginas |
| Cropper.js | 1.6.1 | Recorte manual |
| JSZip | 3.10.1 | ZIP das imagens (PDF para imagens) |
| OpenCV.js | 4.9.0 (sob demanda) | Detecção de bordas e correção de perspectiva |

## Compatibilidade e permissões

Pensado para navegadores modernos em computador, tablet e celular. **Não foi feita uma bateria de testes em navegadores reais**; teste no seu ambiente. Câmera e arrastar com toque dependem do aparelho. A detecção automática depende de WebAssembly e de memória suficiente.

## Problemas comuns

- **Ferramenta "indisponível" ou "precisa de internet para carregar":** uma biblioteca não carregou. Conecte-se e recarregue a página.
- **PDF não abre:** pode estar corrompido ou exigir senha para abrir.
- **Câmera não abre:** verifique permissões ou use *Da galeria*.
- **Bordas não detectadas:** use ⬚ ou ✎; ajuda ter fundo contrastante e boa luz.
- **Documento grande trava:** divida o PDF; em *Organizar* as miniaturas consomem memória.

## Estrutura do projeto

```
index.html   # aplicação completa (HTML, CSS e JavaScript)
README.md    # este arquivo
```

## Limitações e melhorias futuras

**Comprimir PDF:** os níveis Leve/Média/Alta transformam as páginas em imagens (o texto deixa de ser selecionável); “Só otimizar a estrutura” economiza pouco. O resultado varia conforme o PDF.

Ainda **não implementados**: informações/metadados do PDF, cancelar operações em andamento, busca e filtros por categoria na tela de ferramentas, PDFs protegidos por senha de abertura, uso offline permanente (PWA/service worker) e pré-visualização antes de juntar ou dividir.

## Créditos

Construído com [PDF-Lib](https://pdf-lib.js.org/), [PDF.js](https://mozilla.github.io/pdf.js/), [Cropper.js](https://fengyuanchen.github.io/cropperjs/), [OpenCV.js](https://docs.opencv.org/), [Tailwind CSS](https://tailwindcss.com/) e [Font Awesome](https://fontawesome.com/).
