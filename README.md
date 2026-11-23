# WebAR 3D Menu Architect

Skill para o Codex criar e empacotar cardápios interativos em 3D com realidade aumentada via navegador, sem exigir a instalação de aplicativo.

## Recursos

- Arquitetura mobile-first com `@google/model-viewer`
- Compatibilidade com Android (`.glb`) e iPhone (`.usdz`)
- Prompts para geração de pratos 3D em Meshy e Tripo
- Recomendações de desempenho, escala e publicação HTTPS
- Estruturação de ofertas comerciais de até R$ 5.000

## Instalação

Copie a pasta para o diretório de skills do Codex:

```text
~/.codex/skills/webar-3d-menu-architect
```

Depois, invoque a skill como `$webar-3d-menu-architect` ou faça um pedido relacionado a cardápios 3D/WebAR.

## Estrutura

```text
webar-3d-menu-architect/
├── SKILL.md
└── agents/
    └── openai.yaml
```

## Licença

MIT
