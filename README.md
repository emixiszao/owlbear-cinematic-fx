# Owlbear Cinematic FX

Extensão experimental para Owlbear Rodeo, estruturada como a extensão de exemplo enviada pelo usuário: `manifest.json`, `index.html` e `icon.svg`.

## Recursos incluídos

- Vinheta de tela cheia.
- Grão de filme animado.
- Color grading: frio, âmbar, paranormal e preto e branco (um preset por vez).
- Névoa, chuva, partículas de poeira e feixes de luz estilizados em shaders 2D.
- Flash vermelho paranormal de curta duração.
- Botão para criar uma lanterna em cone ligada ao token selecionado, usando a API Dynamic Fog do Owlbear.
- Remoção de efeitos e lanternas criados por esta extensão.

## Compatibilidade e limitações importantes

- Os efeitos de shader (`EFFECT`) usam a API experimental de efeitos do Owlbear e são **locais**. Eles alteram a visão de quem os ativou; não são automaticamente transmitidos aos outros jogadores. Cada pessoa que quiser ver os filtros deve ativá-los no próprio Owlbear.
- A lanterna é uma luz local. Para produzir iluminação/sombras visíveis, a cena precisa estar usando o sistema Dynamic Fog; o resultado também depende da configuração de neblina e paredes do mapa.
- Névoa, chuva, partículas e feixes são simulações 2D em pós-processamento; não são física volumétrica nem reflexos realistas.
- O SDK do Owlbear pode mudar APIs experimentais. Teste numa cópia da sala antes de usar em uma sessão importante.

## Como hospedar (configurado para o GitHub Pages já usado pela extensão Cris)

O manifest já aponta para a subpasta `owlbear-cinematic-fx` do site `emixiszao.github.io/cris-owlbear`, com URLs absolutos. Para que funcione assim:

1. Extraia o ZIP.
2. No repositório GitHub que publica `https://emixiszao.github.io/cris-owlbear/`, envie a pasta `owlbear-cinematic-fx` inteira para a raiz do repositório (sem mover os arquivos para outra pasta).
3. Depois que o GitHub Pages atualizar, teste estes endereços no navegador: `https://emixiszao.github.io/cris-owlbear/owlbear-cinematic-fx/manifest.json` e `https://emixiszao.github.io/cris-owlbear/owlbear-cinematic-fx/index.html`.
4. No Owlbear Rodeo, abra o gerenciador de extensões, escolha adicionar extensão e informe: `https://emixiszao.github.io/cris-owlbear/owlbear-cinematic-fx/manifest.json`.
5. Ative a extensão na sala e teste os efeitos um por um.

Se for hospedar em outro repositório/conta, edite no `manifest.json` as três URLs absolutas (`icon`, `action.icon` e `action.popover`) para o novo endereço publicado.

## Desenvolvimento

O SDK é importado diretamente do `esm.sh` como no exemplo fornecido:

```js
import OBR, { buildEffect, buildLight } from "https://esm.sh/@owlbear-rodeo/sdk@3";
```

Documentação oficial consultada:
- https://docs.owlbear.rodeo/extensions/reference/effects/
- https://docs.owlbear.rodeo/extensions/reference/items/effect/
- https://docs.owlbear.rodeo/extensions/reference/items/light/
- https://docs.owlbear.rodeo/extensions/reference/dynamic-fog/
- https://docs.owlbear.rodeo/extensions/apis/scene/local/
- https://docs.owlbear.rodeo/extensions/apis/player/
