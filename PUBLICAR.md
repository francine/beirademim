# Apontar beirademim.com.br para o site

O site já está no ar em **https://francine.github.io/beirademim/**.
Falta só o domínio apontar pra lá. São dois passos, nesta ordem.

## Passo 1 — DNS no registro.br

Entre em https://registro.br, faça login, abra **beirademim.com.br** e vá em
**Editar zona DNS** (ou "DNS" → "Editar zona").

Adicione **quatro registros A**, todos com o nome em branco (ou `@`, dependendo da tela):

| Tipo | Nome | Valor |
|---|---|---|
| A | (em branco) | `185.199.108.153` |
| A | (em branco) | `185.199.109.153` |
| A | (em branco) | `185.199.110.153` |
| A | (em branco) | `185.199.111.153` |

E **um registro CNAME** para o www:

| Tipo | Nome | Valor |
|---|---|---|
| CNAME | `www` | `francine.github.io.` |

> O ponto final em `francine.github.io.` importa em alguns painéis. Se o registro.br
> reclamar, tente sem o ponto.

Salve. A propagação leva de alguns minutos a algumas horas.

**Conferir se já propagou** (rode no terminal):

```bash
dig +short beirademim.com.br
# quando aparecer os quatro 185.199.*.153, está pronto
```

## Passo 2 — avisar o GitHub (só depois do passo 1 propagar)

```bash
gh api -X PUT repos/francine/beirademim/pages -f cname=beirademim.com.br
gh api -X POST repos/francine/beirademim/pages/https_enforced 2>/dev/null || true
```

Ou pela interface: repositório → **Settings** → **Pages** → **Custom domain** →
`beirademim.com.br` → Save. Depois marque **Enforce HTTPS** (ele só fica disponível
depois que o certificado é emitido, o que leva mais alguns minutos).

## Depois

- `https://beirademim.com.br` passa a servir o site
- `https://www.beirademim.com.br` redireciona pro domínio principal
- `https://francine.github.io/beirademim/` passa a redirecionar também

## Para publicar uma alteração

```bash
cd ~/Dev/beirademim
git add -A && git commit -m "o que mudou" && git push
# em ~1 minuto está no ar
```
