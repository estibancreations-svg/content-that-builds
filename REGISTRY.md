# Numbering Registry — system-wide

Canonical folder numbering across all `estibancreations-svg` repositories.
One number, one meaning, everywhere. Check here before creating any folder.

## Reserved blocks

| Block | Purpose |
|---|---|
| 00–09 | Core system structure |
| 10–19 | Governance and control |
| 20–29 | Content and document work |
| 99 | Archive |

## Canonical assignments

| No. | Name | Scope |
|---|---|---|
| 00 | CENTRAL-HUB | System |
| 01 | ARCHITECTURE | System |
| 02 | SYSTEM-SPECIFICATIONS | System |
| 03 | AI-PROMPTS | System |
| 04 | DATABASE-DESIGN | System |
| 05 | AUTOMATION | System |
| 06 | DEPLOYMENT | System |
| 07 | DOCUMENTATION | System |
| 08 | CHAT-LOGS | System |
| 09 | CONTINUITY | System |
| 10 | GOVERNANCE | Control |
| 11 | MEMORY-GEMS | Control |
| 20 | WORKBOOK | Content |
| 21 | COMMAND-LIBRARIES | Content |
| 22 | TEMPLATES | Content |
| 99 | ARCHIVE | All |

## Rules

1. Two-digit prefix, hyphen, uppercase hyphenated name. No underscores.
2. A number may not carry two meanings across the system.
3. New folder types take the next free number in the correct block and are added to this table in the same commit.
4. This file lives at repository root in every repo, identical in all of them.

## Known collisions — migration pending

`Master-System-Buildout` currently violates this registry in four places:

| Current | Target |
|---|---|
| `00-GOVERNANCE` | merge into `10-GOVERNANCE` |
| `05-GOVERNANCE` | rename to `10-GOVERNANCE` |
| `00_CONTINUITY` | rename to `09-CONTINUITY` |
| `08-MEMORY-GEMS` | rename to `11-MEMORY-GEMS` |

`content-that-builds` violates it in four places:

| Current | Target |
|---|---|
| `00-GOVERNANCE` | `10-GOVERNANCE` |
| `01-WORKBOOK` | `20-WORKBOOK` |
| `02-COMMAND-LIBRARIES` | `21-COMMAND-LIBRARIES` |
| `04-TEMPLATES` | `22-TEMPLATES` |

Unchanged in both: `03-AI-PROMPTS`, `07-DOCUMENTATION`, `08-CHAT-LOGS`, `99-ARCHIVE`.
The `03-AI-PROMPTS` mirror path is deliberately preserved.

Migration not yet executed. Git has no folder rename — each file must be written to the new path and deleted from the old.
