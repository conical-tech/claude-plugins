# Conical Claude plugins

Claude plugins from [Conical Technologies](https://conical-tech.com). Each folder is one plugin; each is submitted to Anthropic's directory on its own.

| Plugin | What it does |
| --- | --- |
| [`conical-record`](conical-record) | Connects Claude to your Conical Forum record (beliefs, domains, how you think) through the Forum connector, and teaches Claude when and how to use it. |

## Layout

```
conical-record/
├── .claude-plugin/plugin.json   manifest
├── .mcp.json                    points at the Forum connector
├── skills/conical-record/       the skill
├── README.md
└── LICENSE
```

## Using a plugin

See each plugin's README for what it sends and how to connect. For Conical Forum, setup is documented at <https://conical-tech.com/docs/connect-to-your-ai/claude-connector>.

## Validate

```bash
claude plugin validate --strict ./conical-record
```

## Privacy and terms

<https://forum.conical.tech/privacy> · <https://forum.conical.tech/terms> · contact@conical-tech.com

Each plugin folder carries its own license. See the `LICENSE` file inside it.
