---
name: detran_sp_autenticidade-mcp
description: Skill da REST API do DETRAN SP: Autenticidade de Certidão na MCP.AI: 1 endpoint em /api/detran_sp_autenticidade. DETRAN SP: Autenticidade de Certidão, consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# DETRAN SP: Autenticidade de Certidão — REST API skill

Você tem acesso à **DETRAN SP: Autenticidade de Certidão** REST API na MCP.AI.

> DETRAN SP: Autenticidade de Certidão, consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago.

## Base URL

```
https://api.mcp.ai/api/detran_sp_autenticidade
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/detran_sp_autenticidade/consultar \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"codigo_certidao":"...","login_senha":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/detran_sp_autenticidade/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (1)

#### `detran_sp_autenticidade_consultar`

DETRAN SP: Autenticidade de Certidão, consulta em fonte oficial. _(POST /api/detran_sp_autenticidade/consultar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `codigo_certidao` | string | Sim | Parâmetro de consulta "codigo_certidao". |
| `login_cpf` | string | Não | Parâmetro de consulta "login_cpf". |
| `login_cnpj` | string | Não | Parâmetro de consulta "login_cnpj". |
| `login_senha` | string | Sim | Parâmetro de consulta "login_senha". |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_detran_sp_autenticidade` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
