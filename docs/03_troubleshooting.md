# 03 — Troubleshooting

Problemas encontrados durante a implementação real desta integração, com as respectivas soluções.

---

## Problema 1 — "No servers added" após reiniciar o Claude Desktop

**Sintoma:** O Claude Desktop abre normalmente, mas em **Settings → Developer** aparece a mensagem "No servers added" mesmo após configurar o arquivo JSON.

**Causa:** Existência de dois arquivos de configuração na mesma pasta — `claude_desktop_config` (sem extensão) e `claude_desktop_config.json`. O Claude Desktop lê apenas o arquivo com extensão `.json`. Se o conteúdo foi editado no arquivo sem extensão, a configuração é ignorada.

**Solução:** Verifique o conteúdo de ambos os arquivos. Para listar os arquivos da pasta com detalhes, use o PowerShell:

```powershell
dir "CAMINHO_DA_PASTA_DE_CONFIGURACAO"
```

Edite o arquivo correto (`claude_desktop_config.json`) e reinicie o Claude Desktop.

---

## Problema 2 — Pasta de configuração do Claude Desktop não encontrada

**Sintoma:** O caminho `%APPDATA%\Claude` não existe ou está vazio.

**Causa:** O Claude Desktop instalado via Microsoft Store usa um caminho de configuração diferente, dentro da pasta `Packages` do Windows.

**Solução:** Não tente localizar a pasta manualmente. Use o botão **Edit Config** em **Settings → Developer** do Claude Desktop — ele abre automaticamente a pasta correta, independente do método de instalação.

---

## Problema 3 — Variáveis de ambiente não funcionam no terminal

**Sintoma:** Ao tentar usar `dir "%APPDATA%"` no terminal, o PowerShell retorna erro de caminho não encontrado.

**Causa:** A sintaxe `%VARIAVEL%` é exclusiva do CMD. No PowerShell, a sintaxe é diferente.

**Solução:** Use a sintaxe correta conforme o terminal:

```powershell
# PowerShell — correto
dir $env:APPDATA
dir $env:LOCALAPPDATA

# CMD — correto
dir %APPDATA%
dir %LOCALAPPDATA%
```

---

## Problema 4 — Power BI Desktop não é detectado pelo Claude

**Sintoma:** Ao perguntar ao Claude sobre o modelo do Power BI, ele responde que não encontrou nenhuma instância local ativa.

**Causas possíveis e soluções:**

**a) O arquivo .pbix não foi salvo no novo formato**
Após ativar os recursos TMDL e PBIR, salve o arquivo. O Power BI pode solicitar confirmação para converter ao novo formato — aceite e salve novamente.

**b) O Power BI Desktop não está aberto**
O MCP detecta instâncias ativas do Power BI Desktop em tempo real. O arquivo `.pbix` precisa estar aberto durante a conversa com o Claude.

**c) O servidor MCP não está running**
Verifique em **Settings → Developer** do Claude Desktop se o servidor `powerbi-modeling` está com status **running**. Se não estiver, revise o caminho do executável no arquivo `claude_desktop_config.json`.

---

## Problema 5 — Erro ao abrir o Claude Desktop após editar o JSON

**Sintoma:** O Claude Desktop não abre ou trava após a edição do arquivo de configuração.

**Causa:** Erro de sintaxe no arquivo JSON — vírgula faltando, aspas incorretas ou barras simples no caminho.

**Solução:** Valide o JSON antes de reiniciar. No VS Code, o próprio editor aponta erros de sintaxe com sublinhado vermelho. Verifique especialmente:
- Barras duplas no caminho (`\\` e não `\`)
- Vírgulas entre propriedades
- Chaves e colchetes fechados corretamente

Use um validador online como [jsonlint.com](https://jsonlint.com/) se necessário.
