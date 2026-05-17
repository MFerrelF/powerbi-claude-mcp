# 02 — Configuração

Este documento cobre a configuração do Claude Desktop e do Power BI Desktop para que a integração via MCP funcione corretamente.

---

## 1. Configurar o Claude Desktop

### 1.1 Localize a pasta de configuração

O caminho da pasta de configuração varia conforme o método de instalação do Claude Desktop. Para encontrá-lo com precisão:

1. Abra o Claude Desktop
2. Acesse **Settings → Developer → Edit Config**

O Explorador de Arquivos abrirá automaticamente na pasta correta.

> **Ponto crítico:** Na pasta de configuração podem existir dois arquivos com nomes parecidos:
> - `claude_desktop_config` — sem extensão, **ignorado** pelo Claude Desktop
> - `claude_desktop_config.json` — **este é o arquivo correto**
>
> Edite sempre o arquivo com extensão `.json`.

---

### 1.2 Edite o arquivo de configuração

Abra o arquivo `claude_desktop_config.json` no VS Code e substitua o conteúdo pelo template abaixo:

```json
{
  "mcpServers": {
    "powerbi-modeling": {
      "command": "C:\\Users\\SEU_USUARIO\\.vscode\\extensions\\analysis-services.powerbi-modeling-mcp-X.X.X-win32-x64\\server\\powerbi-modeling-mcp.exe",
      "args": ["--start", "--skipconfirmation"]
    }
  }
}
```

Substitua:
- `SEU_USUARIO` — pelo seu nome de usuário do Windows
- `X.X.X` — pela versão da extensão instalada (ex: `0.4.0`)

> O template pronto está disponível em [`config/claude_desktop_config_template.json`](../config/claude_desktop_config_template.json).

> **Atenção:** No JSON, as barras do caminho devem ser **duplas** (`\\`). Barras simples causam erro de leitura.

---

### 1.3 Reinicie o Claude Desktop

Encerre o Claude Desktop completamente pelo PowerShell:

```powershell
Stop-Process -Name "claude" -Force
```

Reabra o Claude Desktop e acesse **Settings → Developer**.

O servidor `powerbi-modeling` deve aparecer com o status **running**.

---

## 2. Configurar o Power BI Desktop

### 2.1 Ative os recursos necessários

No Power BI Desktop: **Arquivo → Opções e configurações → Opções → Recursos de visualização**

Ative os seguintes itens:
- Armazenar modelo semântico usando o formato TMDL
- Armazene relatórios usando formato de metadados aprimorado (PBIR)
- Armazenar relatórios PBIX usando o formato de metadados aprimorado (PBIR)
- Preparar dados para IA

Clique em **OK**.

---

### 2.2 Reinicie e salve o arquivo

Reinicie o Power BI Desktop após ativar os recursos.

Com o arquivo `.pbix` aberto, salve com `Ctrl + S`. Se o Power BI solicitar confirmação para converter ao novo formato — aceite.

> Este passo é essencial. O MCP detecta o modelo semântico apenas quando o arquivo está salvo no novo formato PBIR/TMDL.

---

Após concluir a configuração, siga para [04_primeiros_passos.md](04_primeiros_passos.md) para testar a integração.

Se encontrar problemas, consulte [03_troubleshooting.md](03_troubleshooting.md).
