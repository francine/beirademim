# beirademim.com.br

Site pessoal da Fran. Página única, estática, sem build e sem dependência.

- `index.html` — a página inteira (CSS e JS embutidos)
- `assets/` — fotos otimizadas, nenhuma acima de 250 KB

## Editar

Abra o `index.html`. Não há build: salvar já é publicar (depois do push).

```bash
python3 -m http.server 8550 --bind 127.0.0.1   # ver em http://127.0.0.1:8550
git add -A && git commit -m "..." && git push  # publica em ~1 min
```

## Onde as coisas apontam

| | |
|---|---|
| Botão "Conhecer a Mia" | https://oimia.ia.br |
| Contato | DM do Instagram @beirademim |
| Carta | https://beirademim.substack.com |

**E-mail:** ainda não existe caixa em `@beirademim.com.br` (o domínio tem MX nulo, então
mensagem enviada pra lá volta). Quando existir, o contato pode virar `mailto:`.

## Regras de copy

- **Sem travessão (—).** Entrega texto escrito por IA.
- **Sem frase de efeito curta depois do ponto.** Se não acrescenta fato, é enfeite.
- Toda afirmação biográfica vem da Fran, nunca inferida.

## Design

Direção **Marginália** (autoridade tipográfica) com a contenção do **Minimalista**.
Fraunces no logotipo, Newsreader no texto, Caveat na assinatura. O ensaio completo e o
histórico de versões estão em `verve/workspace/verve/beira-de-mim/`.
