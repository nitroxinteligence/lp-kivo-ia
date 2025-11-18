## Objetivo

* Adicionar o conector MCP do Nuxt UI ao arquivo de configuração `mcp.json` do Trae: `"/Users/mateusmpz/Library/Application Support/Trae/User/mcp.json"`.

* Garantir que a configuração esteja válida em JSON e não conflite com entradas existentes.

## Contexto

* O Nuxt UI expõe um servidor MCP via HTTP em `https://ui.nuxt.com/mcp` que fornece acesso estruturado a componentes, exemplos e documentação.

* Em IDEs e ferramentas, a chave de configuração mais comum é `mcpServers` com servidores nomeados; algumas integrações usam `servers`. Usaremos `mcpServers` como padrão, preservando qualquer conteúdo já existente.

## O que será alterado

* Atualizar o `mcp.json` para incluir a entrada `nuxt-ui` sob `mcpServers`:

```json
{
  "mcpServers": {
    "nuxt-ui": {
      "type": "http",
      "url": "https://ui.nuxt.com/mcp"
    }
  }
}
```

* Se já houver conteúdo no arquivo, será feito merge sem remover outras configurações. Se houver apenas `{`, trataremos como objeto vazio e preencheremos corretamente.

## Passos de Implementação

* Abrir `mcp.json` e validar o JSON atual.

* Criar backup do arquivo atual como `mcp.backup.json` no mesmo diretório.

* Inserir/mesclar a chave `mcpServers`:

  * Se `mcpServers` não existir, criar e adicionar `nuxt-ui`.

  * Se `mcpServers` existir, adicionar/atualizar o bloco `nuxt-ui` com `type: "http"` e `url: "https://ui.nuxt.com/mcp"`.

* Garantir formatação consistente (indentação, nova linha final) e JSON válido.

## Validação

* Reabrir/recaregar o Trae para que a configuração seja lida.

* Confirmar que o servidor `nuxt-ui` aparece entre MCPs disponíveis e pode listar componentes (ex.: tentar listar componentes do Nuxt UI via interface da IDE).

* Se a IDE suportar logs de MCP, verificar que a conexão HTTP ao `https://ui.nuxt.com/mcp` foi estabelecida sem erros.

## Reversão

* Restaurar rapidamente o estado anterior substituindo `mcp.json` pelo backup `mcp.backup.json` caso algo não funcione.

## Observações

* Caso o Trae exija a chave `servers` em vez de `mcpServers`, ajustaremos a estrutura para:

```json
{
  "servers": {
    "nuxt-ui": {
      "type": "http",
      "url": "https://ui.nuxt.com/mcp"
    }
  }
}
```

* Preferimos `mcpServers` por ser o formato usado por Cursor e Windsurf; adaptamos se necessário após leitura do arquivo existente.

