# mcp-workspace

Production MCP server workspace — scaffold, build, test, and bundle [Model Context Protocol](https://modelcontextprotocol.io) servers with a single `Taskfile.yml`.

## Requirements

- [mise](https://mise.jdx.dev/) — hermetic Node.js version management
- [task](https://taskfile.dev/) — task runner

## Quick Start

```bash
# 1. Global setup
task setup

# 2. Scaffold a new server
task create NAME=my-server

# 3. Develop
task dev NAME=my-server

# 4. Build + test + bundle
task bundle NAME=my-server

# 5. Inspect via MCP Inspector
task inspect NAME=my-server
```

## Available Tasks

| Task | Description |
|---|---|
| `task setup` | Initialize workspace (dirs, biome config) |
| `task create NAME=x` | Scaffold a new production MCP server |
| `task build NAME=x` | Strict TypeScript compilation |
| `task check NAME=x` | Lint + format with zero-warning policy (Biome) |
| `task test NAME=x` | Run tests with coverage |
| `task bundle NAME=x` | Single-file ESM bundle (esbuild) |
| `task inspect NAME=x` | Live debug via MCP Inspector |
| `task dev NAME=x` | Watch mode with auto-restart |
| `task clean NAME=x` | Remove build artifacts |
| `task list-all` | List all servers with build/bundle status |

## Scaffolded Server Structure

```
servers/my-server/
├── src/
│   ├── index.ts          # Server bootstrap + graceful shutdown
│   ├── tools/ping.ts     # Example tool
│   ├── lib/
│   │   ├── logger.ts     # Structured JSON logger (stderr)
│   │   ├── errors.ts     # Typed error hierarchy
│   │   ├── config.ts     # Zod env validation
│   │   └── registry.ts   # Tool/resource/prompt registrar
│   ├── resources/
│   ├── prompts/
│   └── schema/
├── tests/
├── package.json
├── tsconfig.json
└── biome.json
```

## Roadmap

- [ ] OpenTelemetry tracing
- [ ] Rate limiting middleware
- [ ] Circuit breaker middleware
- [ ] Docker multi-stage build
- [ ] GitHub Actions CI/CD
- [ ] SSE transport support

## License

MIT
