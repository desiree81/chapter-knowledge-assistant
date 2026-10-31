# Chapter Knowledge and Succession Assistant
An agentic system that turns a volunteer chapter's scattered record into a living archive, so leadership transitions stop costing the chapter its memory.

**Status, stated plainly:** A toolkit designed for volunteer-run nonprofit chapters, demonstrated with sample chapter material only. No real member data, chapter documents, or internal records from any actual chapter appear in this repository. Built for use by National Black MBA Association chapters and adaptable by any membership organization with rotating leadership.

## The problem
Chapter leadership turns over on a fixed cycle, and the knowledge walks out with the outgoing officers. Sponsor relationships live in a former president's inbox. The reason a vendor was dropped sits in minutes nobody can find. The new board is capable and committed, and still spends its first six months rediscovering what the last board knew. The records exist. They are just scattered across email threads, shared drives, and meeting notes, in formats no one can search and structures no one maintains.

## The design
Agents that convert raw chapter material into a governed, queryable record, with sourcing treated as non-negotiable:

- **Ingestion agents** — read meeting minutes, event records, and chapter documents and extract structured knowledge entries: decisions and their reasoning, vendor and sponsor contacts, contract terms and dates, recurring deadlines, and open commitments. Every entry carries its source document and date. An entry that cannot be sourced does not enter the archive.
- **Curation step** — a chapter officer reviews extracted entries before they become record. The system drafts; a human ratifies. This is the same human-in-the-loop discipline as any governed system, scaled to a volunteer board.
- **Ask-the-archive agent** — officers query the record in plain language: "What did we pay for the gala venue last cycle, and who negotiated it?" Answers come back with the source entry attached. When the archive holds nothing on the question, it says so. It never fills a gap with a plausible summary.
- **Handover brief generator** — at transition time, produces a brief per incoming role: president, treasurer, programs, membership. Each brief leads with open items, owners, and dates, then the decisions and context that role most needs. The outgoing board's last act becomes the incoming board's first asset.

## Guardrails
- Officer-only access to the archive; the public portfolio artifacts describe the system and contain sample data only.
- Personal member data is excluded from extraction by rule: contact details beyond role-based chapter contacts never become archive entries.
- Every answer is attributable to a source, or is an explicit "not in the record."

## How it is built
- **Google ADK** for agent orchestration, with extraction, curation, query, and briefing as separate agents with defined contracts.
- **Python with Pydantic** models for knowledge entries, so a decision, a vendor term, and a deadline are validated structured records, not paragraphs.
- **Spec-Driven Development:** extraction rules, entry schemas, sourcing requirements, and acceptance criteria specified before implementation. The spec ships in this repository.
- **Evaluation:** a fixed set of sample chapter documents with known facts, tested for extraction accuracy and for the archive's refusal behavior when a fact is absent. The refusal tests matter most.

## What this demonstrates
- Forward deployed design in a civic setting: the client is a volunteer board, the constraint is zero staff, and the system has to survive its own users rotating out.
- Knowledge operations as a governance problem: provenance, ratification, and access control, not just search.
- A companion to the Fair Draw Toolkit. One protects a chapter's money with proof. This one protects its memory the same way.
