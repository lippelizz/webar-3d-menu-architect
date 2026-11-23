---
name: webar-3d-menu-architect
description: Use quando o usuário pedir cardápio 3D, menu WebAR sem aplicativo, integração com model-viewer, prompts de pratos para Meshy ou Tripo, otimização GLB/USDZ ou proposta comercial de cardápio 3D para alimentação.
---

# WebAR 3D Menu Architect

Crie, otimize e empacote cardápios digitais interativos em 3D com realidade aumentada via navegador para restaurantes e outros negócios de alimentação.

## Defina o escopo

Alinhe o foco da entrega antes de começar:

- **Produto técnico:** escolha entre MVP e produção, defina a identidade visual, o fluxo de pedido e quantos pratos terão modelos 3D. Como ponto de partida, use de 8 a 20 pratos principais em 3D e mantenha o restante em 2D para preservar a velocidade.
- **Assets 3D:** prepare prompts e especificações para transformar fotos reais em modelos `.glb` e `.usdz`.
- **Entrega comercial:** estruture a proposta pelo valor gerado, como aumento de ticket médio, clareza da porção e diferenciação da experiência.

## Gere pratos 3D

Ao orientar Meshy, Tripo ou outra ferramenta Image-to-3D/Text-to-3D:

- Peça imagem de referência com fundo neutro, enquadramento limpo e luz difusa.
- Evite sombras duras projetadas na mesa; o WebAR deve gerar a sombra dinamicamente.
- Informe dimensões reais, como prato de 28 cm, tábua de 30 cm ou hambúrguer de 12 cm de altura.
- Exporte `.glb` com materiais PBR e texturas, preferencialmente abaixo de 8 a 10 MB.
- Exporte também `.usdz` com escala real em metros para Safari no iPhone.

## Construa o WebAR mobile-first

Use `@google/model-viewer` por CDN estável. Configure o visualizador ativo com:

```html
<model-viewer
  src="prato.glb"
  ios-src="prato.usdz"
  poster="prato.webp"
  alt="Prato em visualização 3D"
  ar
  ar-modes="webxr scene-viewer quick-look"
  ar-scale="fixed"
  camera-controls
  shadow-intensity="1"
  environment-image="neutral"
></model-viewer>
```

Na listagem, mostre cards leves em 2D. Instancie apenas um `<model-viewer>` quando o usuário abrir o prato selecionado. Inclua uma ação clara, como "Ver na minha mesa em AR", um fallback para dispositivos sem AR e um carrinho simples com envio formatado para o WhatsApp do restaurante.

O deploy precisa usar HTTPS para que WebXR e a permissão da câmera funcionem.

## Normalize os assets

Antes da entrega:

1. Ajuste a origem e a orientação do modelo.
2. Normalize a escala em metros conforme o tamanho real da porção.
3. Comprima geometria e texturas sem degradar a aparência do alimento.
4. Teste o `.glb` no Android e o `.usdz` no Safari/iPhone.
5. Verifique o carregamento em uma conexão móvel real.

## Estruture a oferta comercial

Posicione a solução como acelerador de ticket médio e da experiência gastronômica, não apenas como um QR Code 3D.

Use três níveis de ancoragem quando isso ajudar a venda:

| Pacote | Escopo sugerido |
|---|---|
| Essencial | 5 pratos em 3D |
| Profissional | 12 pratos em 3D e checkout pelo WhatsApp |
| Premium | 20 pratos em 3D, QR Codes personalizados e analytics |

O pacote principal pode chegar a R$ 5.000, com hospedagem e atualizações recorrentes opcionais. Adapte quantidade, prazo e preço ao material fornecido e à complexidade real.

## Erros comuns

- **Escala incorreta:** modelos de IA podem surgir gigantes ou minúsculos. Normalize em metros e use `ar-scale="fixed"`.
- **Ausência de USDZ:** `.glb` atende Android, mas não substitui `ios-src` no iPhone.
- **Tela pesada:** não mantenha vários visualizadores 3D ativos na vitrine.
- **Hospedagem sem HTTPS:** câmera e WebXR podem falhar silenciosamente.
