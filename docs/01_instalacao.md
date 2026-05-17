# 01 — Instalação

Este documento detalha a instalação de todos os componentes necessários para a integração entre Claude Desktop e Power BI Desktop via MCP.

---

## 1. VS Code

Baixe e instale o Visual Studio Code em [https://code.visualstudio.com/](https://code.visualstudio.com/).

Durante a instalação, marque a opção **"Add to PATH"** — isso facilita o uso do VS Code pelo terminal.

---

## 2. Extensão Power BI Modeling MCP Server

Com o VS Code aberto:

1. Pressione `Ctrl + Shift + X` para abrir o painel de extensões
2. Busque por: `Power BI Modeling MCP Server`
3. Localize a extensão publicada por **Analysis Services**
4. Clique em **Install**

Após a instalação, o executável estará disponível em:
```
C:\Users\SEU_USUARIO\.vscode\extensions\analysis-services.powerbi-modeling-mcp-X.X.X-win32-x64\server\powerbi-modeling-mcp.exe
```

Para confirmar o caminho exato, abra o Explorador de Arquivos e navegue até:
```
C:\Users\SEU_USUARIO\.vscode\extensions\
```
Procure a pasta que começa com `analysis-services.powerbi-modeling-mcp` e abra a subpasta `server`.

---

## 3. Claude Desktop

Baixe o Claude Desktop em [https://claude.ai/download](https://claude.ai/download).

> **Observação:** O Claude Desktop pode ser instalado via Microsoft Store ou via instalador direto. O caminho da pasta de configuração varia conforme o método de instalação — veja mais detalhes em [02_configuracao.md](02_configuracao.md).

---

## 4. Power BI Desktop

Baixe o Power BI Desktop gratuitamente em [https://powerbi.microsoft.com/](https://powerbi.microsoft.com/).

A versão gratuita é suficiente para toda a integração descrita neste repositório.

---

Após instalar todos os componentes, siga para [02_configuracao.md](02_configuracao.md).
