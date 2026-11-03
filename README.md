# Honest Navigator Post Creator

Cria capas de reels e carrosséis fiéis a uma marca, diretamente no telemóvel, sem precisar de saber design. Pensado para a [@sircharlesvonbaptist](https://instagram.com/sircharlesvonbaptist) e para quem a queira usar com a sua própria identidade.

Corre inteiramente no browser: **sem backend, sem conta, sem upload**. As fotos e os textos nunca saem do dispositivo. A única exceção é opcional: ao escolher uma fonte do Google Fonts (ver abaixo), a app faz um pedido ao Google.

**Design system:** a interface usa os tokens do design system (`tokens.css`): tema Noite e Dia, anel de foco de 2 px, contrastes AA, botões com o efeito Registo, Light Chase no botão "Exportar imagem" e a Película (luz e grão) no ecrã vazio. Em *Criar o meu estilo → Aspeto da interface* escolhes o tema (Noite, Dia ou Sistema) e a fonte dos títulos (Besley ou Newsreader). Só muda a interface; as capas exportadas usam sempre o teu estilo.

**Fontes e licenças:** Besley, Newsreader e Anybody, todas SIL OFL, autoalojadas em `fonts/` com as respetivas licenças.

## Como usar

1. Escolhe **Formato** (Reel 9:16, Carrossel 4:5, Quadrado 1:1) e **Fundo**:
   - **Foto**: a tua imagem com uma caixa colorida à volta do rótulo, ou **Sem caixa**, com o texto na cor que escolheres (Branco, Preto ou uma das cores da marca)
   - **Overlay**: a tua imagem com uma camada preta (opacidade ajustável) e o texto diretamente por cima
   - **Sólido**: uma cor da marca com uma grelha subtil de pontos
2. Carrega a foto. No **Carrossel**, usa **Páginas** para juntar slides (cada um com a sua foto e o seu texto) e "Exportar todas as páginas".
3. Separador **Texto**: Rótulo, Contexto e Rodapé. Aceitam Enter para quebras de linha à tua escolha.
4. Separador **Estilo**: cor e estilo da caixa (Sólido ou Sem caixa), ou a cor do texto se escolheres "Sem caixa" (e, no Overlay, a opacidade).
5. Separador **Posição**: grelha 3×3, ajuste fino vertical, tamanho do texto (Pequeno / Médio / Grande) e alinhamento do rodapé (Esquerda / Centro). Em carrossel, o rodapé à esquerda para antes do número de página.
6. **Exportar imagem**: no iPhone abre a folha de partilha; escolhe "Guardar Imagem" para ir para a galeria.

Por baixo da imagem, quando há foto ou overlay e texto por cima, a app indica a **legibilidade** do texto sobre a foto (boa, razoável ou fraca) e, se for fraca, sugere o que experimentar. É uma estimativa feita no próprio telemóvel, só para dar uma ideia: nunca bloqueia a exportação, e uma foto com muito detalhe pode ler-se pior do que o medidor indica. Com caixa, só o rodapé é medido, porque o resto fica sobre a caixa. No fundo Sólido não aparece.

No Reel há ainda o botão **Zona segura** (desligado por omissão), que mostra onde a interface do Instagram tapa o conteúdo. É só uma ajuda no ecrã e nunca aparece na imagem exportada.

## Criar o meu estilo

O botão no topo abre o painel da marca: **2 fontes** (carregadas de um ficheiro TTF, OTF, WOFF ou WOFF2 até 800 KB, ou obtidas do Google Fonts) e **5 cores** com papel definido (Base, Texto, Acento, Secundária, Clara), com pré-visualização antes de guardar. A Honest Navigator é a predefinição.

- A marca aplica-se ao **conteúdo exportado**. A interface do editor mantém sempre as mesmas fontes e cores, para continuar legível seja qual for a fonte escolhida.
- Se uma fonte guardada deixar de carregar, só essa volta à predefinida e a app avisa.
- **Google Fonts:** o botão "Google" ao lado de cada fonte pede-a ao Google uma única vez (o Google vê o teu IP e o nome da fonte). Escreve o nome tal como aparece no Google Fonts, com maiúsculas e espaços (por exemplo "Playfair Display"). A fonte fica guardada no telemóvel e a app volta a funcionar sem internet. Só é preciso ligação na hora de a obter.
- "Exportar estilo" / "Importar estilo" guardam e carregam a marca num ficheiro `.json`, útil para a passar a alguém ou para a levar entre o Safari e a app instalada.
- "Guardar e aplicar" recarrega a app: os textos mantêm-se, mas as fotos têm de ser adicionadas de novo.

## O que fica guardado, e onde

Tudo em `localStorage`, neste dispositivo. As chaves têm nome próprio porque todos os repositórios de `carlos-baptista.github.io` partilham a mesma origem e, com nomes genéricos, duas apps leriam e apagariam os dados uma da outra:

| O quê | Chave | Notas |
|---|---|---|
| Estilo (fontes e cores) | `postCreatorBrandKit` | Fontes guardadas dentro do próprio registo. Validado ao ler; o que for inválido volta à predefinição. |
| Rascunho (textos e definições) | `postCreatorDraft` | Guardado automaticamente. **As fotos nunca são guardadas.** "Recomeçar" apaga-o. |
| Aspeto da interface (tema, fonte dos títulos) | `postCreatorLook` | Aplicado já no arranque, sem flash. |

Se o iOS descartar o separador, os textos voltam; as fotos têm de ser adicionadas de novo. O armazenamento do Safari e o da app instalada no ecrã principal podem ser separados: se configurares o estilo num e não aparecer no outro, usa exportar/importar.

## Fotos grandes

Ao carregar, a foto é reduzida logo para o tamanho de que o Reel precisa (no máximo cobrir 1080×1920 a 1×) e o original é largado, em vez de se manter a resolução total em memória. Se o ficheiro não abrir, aparece um aviso em vez de falhar em silêncio.

## Instalar como app no iPhone

1. Abre o link no **Safari** (não na app do Claude nem noutro browser)
2. Partilhar → **Adicionar ao Ecrã Principal**

## Atualizar

1. No repositório, **Add file → Upload files** e arrasta os ficheiros novos (substituem os que têm o mesmo nome)
2. Com rede, a app abre sempre a versão mais recente (já não fica presa numa cache antiga). Se a app já estiver aberta, ao voltares a ela aparece o aviso **Nova versão disponível**: **Atualizar** recarrega (o texto fica guardado; as fotos carregadas perdem-se, e a app avisa antes) e **Depois** adia
3. Para saberes em que versão estás, vê **Versão N** no fim da página. Em cada alteração, sobe o número da meta `app-version` no `index.html` (formato `v<número>`): é isso que faz o aviso aparecer. O `sw.js` só precisa de ser enviado quando muda
4. Na primeira atualização para esta versão, abre a app duas vezes: a primeira ainda usa a cache antiga, a segunda já traz a versão nova. Se persistir na versão antiga, limpa os dados do site em Definições → Safari → Avançado → Dados de Sites

## Publicar (GitHub Pages)

1. Repositório `honest-navigator-post-creator` → **Settings → Pages** → *Deploy from a branch* → `main` / `(root)`.
2. A app fica em `https://carlos-baptista.github.io/honest-navigator-post-creator/`.
3. Instalada no ecrã principal, aparece como **Post Creator**.

### Origem partilhada

Todos os repositórios de `carlos-baptista.github.io` partilham `localStorage` e `CacheStorage`. Por isso esta app usa chaves (`postCreator…`) e uma cache (`post-creator`) com nome próprio, e o `manifest.json` tem `id` e `scope` próprios, para o iOS a tratar como app separada. O service worker, ao ativar, só apaga caches `post-creator-*`.

Se ainda usares o antigo **Editor de Capas** (repo `honest-navigator-post-template`), o `sw.js` dele apaga todas as caches que não se chamem `editor-capas`, incluindo a desta app, se for reativado. Esta recompõe-se na visita seguinte com rede (os ficheiros são pedidos primeiro à rede). Se editares esse `sw.js`, muda a linha para só apagar chaves `editor-capas-*` que não sejam a dele.

## Testes

Na pasta `tests/` (precisam de Node e `jsdom`; defina `APP_HTML=../index.html`):

```
npm i jsdom
cd tests
APP_HTML=../index.html node smoke_updates.js
APP_HTML=../index.html node smoke_legibility.js
APP_HTML=../index.html node test_legibility.js
node test_sw.js
```

`test_legibilidade.js` tem 2 falhas que já existiam no Editor de Capas original (não são regressões).

## Estrutura

```
index.html   manifest.json   sw.js
fonts/        (Besley, Newsreader, Anybody e licenças OFL)
tokens.css    (tokens do design system v2.1, sem os itálicos)
tests/
icon-120.png  icon-152.png  icon-167.png  icon-180.png  icon-192.png  icon-512.png
```
