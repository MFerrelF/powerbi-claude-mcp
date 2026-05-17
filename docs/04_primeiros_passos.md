# 04 — Primeiros Passos

Com a integração configurada e funcionando, este documento apresenta os primeiros comandos úteis e boas práticas para começar a trabalhar com o Claude + Power BI.

---

## Testando a conexão

Com o arquivo `.pbix` aberto no Power BI Desktop, abra uma nova conversa no Claude Desktop e use um dos comandos abaixo:

```
Conecte ao Power BI Desktop local e liste as tabelas disponíveis
```

```
Liste as tabelas e colunas do modelo Power BI aberto
```

Se a integração estiver funcionando corretamente, o Claude irá:
1. Encontrar a instância local do Power BI automaticamente
2. Conectar ao modelo semântico
3. Listar todas as tabelas, colunas e medidas disponíveis

---

## Comandos úteis para começar

### Explorar o modelo

```
Descreva o modelo semântico atual — tabelas, relacionamentos e medidas existentes
```

```
Quais são os relacionamentos entre as tabelas do modelo?
```

### Criar medidas DAX

```
Crie uma medida DAX de faturamento líquido considerando devoluções
```

```
Crie uma medida de ticket médio baseada na tabela de vendas
```

```
Crie uma medida de crescimento percentual mês a mês para o faturamento
```

### Verificar medidas existentes

```
Liste todas as medidas DAX existentes no modelo e explique o que cada uma calcula
```

### Gerar dashboard em HTML

```
Com base nos dados de vendas, gere uma medida DAX em HTML com um resumo executivo 
contendo faturamento total, ticket médio e total de devoluções
```

---

## Boas práticas

**Valide os números antes de apresentar ao cliente**
O Claude cria as medidas com base na estrutura do modelo, mas sempre confira se os resultados batem com os dados reais antes de usar em apresentações.

**Seja específico nos pedidos**
Quanto mais contexto você fornecer — nomes de tabelas, colunas relevantes, regras de negócio — mais preciso será o resultado. Em vez de "crie uma medida de vendas", prefira "crie uma medida de faturamento líquido usando a coluna valor_faturado da tabela base_vendas_tiny, descontando os valores da tabela base_devolucoes".

**Use uma conversa por contexto**
Inicie uma nova conversa no Claude Desktop para cada projeto ou cliente. Isso evita que contextos de projetos diferentes se misturem e mantém o consumo de tokens eficiente.

**Atenção com dados pessoais**
Evite pedir ao Claude que exiba registros individuais com dados de clientes. Trabalhe com agregações — totais, médias, percentuais — para manter conformidade com a LGPD.

---

## Fluxo recomendado para criar um dashboard

1. Peça ao Claude para listar e entender o modelo atual
2. Defina com o Claude quais KPIs o dashboard deve apresentar
3. Deixe o Claude criar as medidas DAX necessárias
4. Valide os números no Power BI Desktop
5. Peça ao Claude para gerar a medida HTML com o layout do dashboard
6. Adicione o visual **HTML Content** no canvas do Power BI
7. Arraste a medida HTML para o visual
8. Ajuste dimensões e finalize

---

## Próximos passos sugeridos

- Explore a criação de medidas DAX complexas com inteligência de tempo (YTD, MoM, YoY)
- Experimente pedir ao Claude para identificar inconsistências ou anomalias no modelo
- Crie um Project no Claude Desktop dedicado a cada cliente, com contexto fixo sobre as regras de negócio
