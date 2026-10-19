I build automation that runs without me. Agent pipelines, print-on-demand tooling,
iOS apps. Mostly Python and Swift, lately a lot of Claude Code.

### What I am working on now

**claude5-readiness**, a checker for published Claude Code tooling. Anthropic retires model ids on a schedule and a
retired id does not fall back, the API returns an error, so a repository still
shipping one is broken for everyone who runs it. GitHub code search finds retired
ids in tens of thousands of files. I scan skill and plugin repositories for those,
plus sampling parameters that current models reject, and send the fixes upstream.

The hard part is not finding the strings. It is not touching the ones that belong
where they are: pricing tables, end-of-life databases, recorded API responses in
test fixtures, SDK constants named after the model they hold. In one sample of 18
repositories only 4 were safe to patch. The other 14 would have been damage.

<!-- OZET:BASLA -->
**Open source record.** 6 published security advisories with reporter credit and 32 fixes merged into other projects. Full list with links in [security-research](https://github.com/kasparovabi/security-research).
<!-- OZET:BITIR -->

### Selected work

| | |
|---|---|
| [claude-audit-20](https://github.com/kasparovabi/claude-audit-20) | Twenty failure classes as write-time coding rules, then a twenty-pass audit with a false-positive filter as the last pass |
| [security-research](https://github.com/kasparovabi/security-research) | Findings and coordinated disclosures |
| [busted](https://github.com/kasparovabi/busted) | Mac desk guard that catches snoops |
| [claude-mythos-scaffold](https://github.com/kasparovabi/claude-mythos-scaffold) | Agentic discipline for Opus 4.x. Retired in August 2026 because Claude 5 no longer needs it |

Retiring that last one was the right call and worth saying out loud. Boris Cherny,
who created Claude Code, tells people to delete their CLAUDE.md files, skills and
hooks every six months and see what the model does without them. Anthropic cut
roughly 80 percent of Claude Code's own system prompt for the Claude 5 generation.
I ran that on my own setup: 41 global skills and most of a CLAUDE.md went into an
archive folder, and the result was better.

### How I work with agents

Verify before reporting. Most of what an agent gets wrong is not the code, it is
the confidence. Every claim in the tooling above has to survive a check that tries
to refute it, and every past false positive becomes a permanent test case so the
same mistake cannot ship twice.
