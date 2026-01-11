# App Diagram Plugin

Generate and maintain comprehensive state machine and sequence diagrams that document all application logic, data flows, and system interactions.

## What It Does

**Generate:** Forces exhaustive analysis of your entire codebase to produce:
- **State machine diagrams** - All application states and transitions
- **Sequence diagrams** - All user journeys and system interactions

**Update:** Incrementally updates existing diagrams after code changes:
- **Change detection** - Git-based and inventory comparison
- **Impact analysis** - Identifies which diagrams need updates
- **Targeted updates** - Modifies only affected diagrams

Outputs Mermaid diagrams to `docs/diagrams/` with full inventory tracking.

## Key Features

- **Documents only what exists** - No invented or assumed functionality
- **Complete coverage** - Every endpoint, route, and entity is diagrammed
- **Flexible organization** - Agent chooses logical grouping for each project
- **Mermaid validation** - Syntax guidelines to prevent rendering errors
- **Verification checklist** - Ensures nothing is missed
- **Fresh context** - Agents run as subprocess for focused analysis
- **Incremental updates** - Don't regenerate everything after changes

## Usage

### Generate Diagrams (First Time)

Use the `diagram-generator` agent (Opus + fresh context):

```
"Generate diagrams for this application"
"Map out all the state machines and sequences"
"Create visual documentation of the codebase"
```

### Update Diagrams (After Changes)

Use the `diagram-updater` agent (Opus + fresh context):

```
"Update the diagrams to reflect recent changes"
"Sync diagrams after refactoring"
"Are my diagrams still accurate? Update if needed"
```

### Skills (Auto-triggered)

Skills trigger automatically and provide detailed guidance:
- `generate-app-diagrams` - Full diagram generation process
- `update-app-diagrams` - Incremental update process

## Output Structure

```
docs/diagrams/
├── README.md          # Index of all diagrams
├── _inventory.md      # Component checklist with coverage tracking
└── [logical-grouping]/
    └── [diagram].md   # Mermaid diagrams
```

## Agents

| Agent | Model | Purpose |
|-------|-------|---------|
| `diagram-generator` | Opus | Full codebase analysis and diagram creation |
| `diagram-updater` | Opus | Incremental updates after code changes |

Both agents run with fresh context for focused, thorough analysis.

## Workflow

```
┌─────────────────────────────────────────────────────────┐
│  New Project / No Diagrams                              │
│  └─> diagram-generator (full analysis)                  │
│      └─> docs/diagrams/ created                         │
└─────────────────────────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────┐
│  Code Changes / Refactoring                             │
│  └─> diagram-updater (incremental)                      │
│      ├─> Detect changes (git + inventory)               │
│      ├─> Identify affected diagrams                     │
│      ├─> Update only what changed                       │
│      └─> Sync inventory                                 │
└─────────────────────────────────────────────────────────┘
                          │
                          ▼
                       (repeat)
```

## Why Use This

This plugin forces the agent to thoroughly analyze your codebase rather than making assumptions. The discovery phase requires building a complete inventory before any diagramming begins, ensuring comprehensive coverage.

The Opus model and fresh context ensure deep, focused analysis for both initial generation and subsequent updates.
