# Runik AI — MCP Server

> Chat-first business management platform. Describe your business, get a complete system in seconds.

[![MCP](https://img.shields.io/badge/MCP-Streamable%20HTTP-6366f1)](https://modelcontextprotocol.io)
[![License](https://img.shields.io/badge/License-AGPL--3.0-green)](LICENSE)
[![Website](https://img.shields.io/badge/Website-runikapp.com-blue)](https://runikapp.com)

## What is Runik AI?

Runik AI is a business management platform that works as a **remote MCP server**. Connect it to ChatGPT, Claude, or any MCP-compatible client and manage your entire business through natural conversation.

- **21 industry templates** — Restaurant, Hotel, Gym, CRM, Inventory, HR, and more
- **14 interactive widgets** — Table, Kanban, Calendar, Pipeline, Floorplan, Gantt, Report...
- **Per-company data isolation** — Each company's data is fully separated
- **OAuth 2.0 + PKCE** — Secure authentication for external clients
- **LLM-agnostic** — Claude, ChatGPT, Mistral, Ollama

## Quick Connect

### ChatGPT

1. Go to **Settings → Connectors → New**
2. Enter URL: `https://runikapp.com/mcp`
3. Auth: OAuth 2.0
4. Authorize with your Runik account

### Claude Desktop

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "runik-ai": {
      "url": "https://runikapp.com/mcp",
      "transport": "streamable-http"
    }
  }
}
```

### Any MCP Client

```
Server URL: https://runikapp.com/mcp
Transport: Streamable HTTP
Auth: OAuth 2.0 (PKCE)
```

## Available Tools

Runik dynamically generates MCP tools based on your data:

| Tool Pattern | Description | Annotations |
|---|---|---|
| `tables_list` | List all tables | readOnly |
| `table_schema` | Get table structure | readOnly |
| `{table}_list` | List records with search/filter/sort | readOnly |
| `{table}_get` | Get single record by ID | readOnly |
| `{table}_create` | Create new record | write |
| `{table}_update` | Update record by ID | write |
| `{table}_delete` | Delete record by ID | destructive |
| `template_list` | List available templates | readOnly |
| `template_install` | Install industry template | write |
| `views_list` | List configured views | readOnly |

All tools include [MCP annotations](https://developers.openai.com/api/docs/mcp) for safety (`readOnlyHint`, `destructiveHint`, `openWorldHint`).

## Industry Templates

| Template | Tables | Views |
|---|---|---|
| 🍽 Restaurant | Mesas, Carta, Pedidos, Ingredientes, Caja | Floorplan, Kanban, Report |
| 🏨 Hotel | Habitaciones, Huéspedes, Reservas, Pagos, Housekeeping | Floorplan, Calendar, Kanban |
| 🏋 Gimnasio | Espacios, Socios, Clases, Pagos | Floorplan, Schedule, Report |
| 💼 CRM Servicios | Empresas, Contactos, Oportunidades, Actividades | Pipeline, Calendar, Report |
| 🏥 Clínica | Pacientes, Citas, Tratamientos, Pagos | Schedule, Kanban, Master-Detail |
| 📦 Inventario | Productos, Proveedores, Movimientos, Compras | Table, Report, Kanban |
| ...and 15 more | | |

## Example Conversation (ChatGPT)

```
You: What tables do I have?
AI: You have 7 tables: Mesas (7), Pedidos (4), Carta (6)...

You: Which tables are available right now?
AI: Mesa 1 (Interior) - Available, Mesa 4 (Terraza) - Available...

You: Create a new order for table 1, lomo saltado and pisco sour
AI: Created order #5 for Mesa 1, total $20,000 ✓
```

## Security

- OAuth 2.0 with PKCE for external clients
- Per-company data isolation (no cross-tenant access)
- Tool annotations for ChatGPT safety compliance
- Rate limiting on all endpoints

## Links

- 🌐 **Website:** [runikapp.com](https://runikapp.com)
- 📖 **Docs:** [runikapp.com/support](https://runikapp.com/support)
- 🔒 **Privacy:** [runikapp.com/privacy](https://runikapp.com/privacy)
- 💬 **Support:** shabit@allware.cl

## License

AGPL-3.0 — See [LICENSE](LICENSE) for details.
