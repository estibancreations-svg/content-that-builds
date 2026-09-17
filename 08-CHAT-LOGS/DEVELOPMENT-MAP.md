# Development Map

How this repository came to exist, and why the path looks the way it does.

Reconstructed from working sessions between 2026-08-19 and 2026-09-17. **Partial — see completeness note at the end.**

---

## Phase 1 — No connector (Aug 19 – Aug 26, 2026)

The earliest relevant work had no GitHub access at all.

**Aug 19** — A deployment status check was attempted against the GitHub repositories. No GitHub connector was active. The available registry was searched; Vercel was the closest connected deployment tool. Setup instructions for adding a GitHub connector were produced, and the session ended there.

**Aug 26** — Automation architecture work for THELMA across four production pipelines: Book Creation, Video Production, Character Production, Podcast Production. A GitHub connector was searched for twice in the MCP registry and was not found. Vercel's deployment context tool was used instead to confirm live repository data without GitHub access.

*Why it matters:* the account infrastructure was being designed before there was any way to read or write the repositories directly. Early architecture decisions were made from Vercel-side metadata.

---

## Phase 2 — Connector established (Sep 15–16, 2026)

Runway was connected successfully as a custom connector via OAuth.

GitHub was then attempted using the remote MCP server endpoint. The connection came up, but with two limitations that would shape everything after:

1. Organization-owned repositories can remain invisible even after a successful OAuth handshake.
2. The installed app lacked administration scope.

Neither was apparent until the connector was put under load.

---

## Phase 3 — The Second Edition is written (Sep 16, 2026)

Session: *Workbook redesign as governing system.*

The full Second Edition upgrade was built in three sequential passes:

1. **Generalize the spine** — remove anchoring to any single campaign or product category
2. **Add Narrative Mode** — film and story work: scene beat map, 180-degree rule, coverage system, screen direction discipline, two narrative prompt templates
3. **Complete Chapter 13** — a three-column worked walkthrough

### Structural changes made

- An eight-type **Lock Family**, replacing the original two-slot identity/product system, with a selector tool and a stacking table
- **Diagnostic Router** extended to 18 entries
- **Drift Ladder** at 14 symptoms
- **Chapter 7 rebuilt** around job types rather than named campaigns
- **Command library format** moved to five columns, adding *Fails when* and *Pairs with*
- Compliance page added
- Glossary added

### Two corrections made during the session

**Order of work.** The assistant drifted toward system architecture when the task was the document. This was flagged and corrected. The order of record is: **document first, system second.**

**Chapter 13 scope.** The initial approach built Chapter 13 around a single worked example. This was rejected. The requirement is three *unrelated* job types — object, experience, narrative — precisely to prove the spine holds regardless of subject.

### The blocker appears

With the content written, a repository check revealed **all four existing repositories were public**. The material was co-owned and had not yet been reviewed by the co-creator.

The instruction given was: create a private repository, mirror into the system hub, and flip everything to private.

The repository creation call returned:

```
403 Resource not accessible by integration
```

Retried once. Same result. Diagnosed as a permissions wall rather than a transient failure — the installed app lacked **Administration: Read and write**.

Nothing was committed.

---

## Phase 4 — Attempted workaround (Sep 16–17, 2026)

Session: *GitHub assistant setup for content builds.*

With direct creation blocked, the approach shifted to handing the work to GitHub's own coding agent, which runs under the account holder's credentials rather than the connector's.

A seven-step `AGENT_TASK.txt` was produced covering visibility flips, repository creation, folder structure, per-file content requirements, root files, the mirror into the system hub, and a completion checklist. It was written order-dependent, with an explicit instruction to halt rather than proceed if any visibility step failed.

Repository creation was attempted again from the connector. Still 403.

The repository was then **created manually** by hand on 2026-09-16. The connector returned 404 against it — newly created repositories are not automatically included when an app's access is scoped to a selected list.

---

## Phase 5 — Connector rebuilt (Sep 17, 2026)

The existing GitHub connection was deleted and rebuilt from scratch.

A GitHub OAuth App was registered manually, with the redirect URI pointed at the Claude MCP callback, and its client credentials supplied to a custom connector configured against the remote GitHub MCP server.

On reconnection, identity resolved and admin permissions were confirmed across all repositories.

### Repository audit on reconnection

Ten repositories total. Counted directly: five public, five private.

`content-that-builds` existed, was empty, and was **public** — with the attribution line visible in its description.

### Visibility flips

The flips were performed by hand. There is no tool in the GitHub connector that changes repository visibility; this is unavoidable manual work.

Result verified by direct query: nine of ten private. One outstanding at time of writing — `-HisMajesty0225-CEO-Dashboard`, an empty repository that was skipped in the pass.

---

## Phase 6 — Provenance clarified (Sep 17, 2026)

Before committing, a question was raised about the rights position on the source material, prompted by ambiguity over how the document had been obtained and whether attribution was being dropped.

The position was clarified: the document originated inside a small group who shared their learning freely, was assembled by Christian for the group's common use, is not being sold, and is being used internally to advance existing systems.

The commit gate was lifted on that basis. Attribution retained. See `00-GOVERNANCE/PROVENANCE.md`.

---

## What this cost

The workbook content was finished on Sep 16. It reached a repository the following day. The intervening day was spent entirely on access control and permissions — not on the work itself.

Three things caused it:

1. An app installation scoped to selected repositories rather than all repositories
2. Missing administration scope, which is not visible until a creation call fails
3. Repository visibility being unreachable through tooling, so every flip is manual

Worth knowing before the next repository is created.

---

## Completeness note

This map was assembled by searching prior working sessions. Search is keyword-based and cannot certify that every relevant session was found. Sessions covering adjacent work — logistics systems, the CEO dashboard platform, the GoHighLevel-equivalent build — exist and are referenced only where they touch this repository's history.

Treat this as an accurate record of what was found, not an exhaustive record of everything that happened.
