# Exercicio 4.2 - MCP server local que consome a API (4.1)

**Aluna:** Eliane Ricarte
**Disciplina:** IDP-TD 2026

## O que este projeto faz

Um MCP server local que expoe duas tools - criar_tarefa e listar_tarefas -
para um agente de IA gerenciar uma TODO list. As tools sao implementadas
chamando a API REST do Exercicio 4.1 (http://localhost:8000) via HTTP.

Agente / LLM --MCP--> servidor_mcp.py --HTTP--> API 4.1

## Arquivos

- servidor_mcp.py - MCP server (FastMCP) com as tools criar_tarefa e listar_tarefas
- cliente_teste.py - sobe o server via stdio, exercita as tools e imprime o envelope JSON
- requirements.txt - mcp, httpx

## Como rodar

Terminal A - API do 4.1: uvicorn app.main:app --port 8000
Terminal B - neste repo: pip install -r requirements.txt && python cliente_teste.py

## Reflexao - o que o MCP abstraiu

O MCP escondeu de quem chama a tool todo o detalhe HTTP da API: o agente so
precisa saber que existe criar_tarefa(titulo), sem conhecer a URL, o metodo
POST, o formato do JSON ou os status codes. O protocolo tornou a implementacao
da API um detalhe irrelevante para o consumidor.
