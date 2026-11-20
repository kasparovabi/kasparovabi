I find security bugs in open source code, reproduce them locally and help the
maintainers fix them. I also build automation that runs without me. Agent pipelines,
iOS and macOS apps. Mostly Python and Swift, lately a lot of
Claude Code.

### What I am working on now

Coordinated disclosure. Each report goes to the maintainers privately, through GitHub
private vulnerability reporting or the channel in their SECURITY.md, and recent ones
came with a proposed patch in the advisory's temporary private fork. Some of the
published results:

- Two heap buffer overflows in [Rufus](https://github.com/pbatard/rufus), one from a short md5sum.txt line in an ISO and one from a downloaded sbat_level.txt with CR line endings. Fixed for 4.16 ([GHSA-877g-r8h5-fq8p](https://github.com/pbatard/rufus/security/advisories/GHSA-877g-r8h5-fq8p), [GHSA-hcpc-vq8c-923h](https://github.com/pbatard/rufus/security/advisories/GHSA-hcpc-vq8c-923h)).
- An out-of-bounds read in [Avalonia](https://github.com/AvaloniaUI/Avalonia) when a CF_DIB bitmap comes from the Windows clipboard or a drop ([GHSA-x3fw-83fm-ggpp](https://github.com/AvaloniaUI/Avalonia/security/advisories/GHSA-x3fw-83fm-ggpp)).
- The emailed sign in link in [Magic](https://github.com/polterguy/magic) took its domain from the Origin header, so a root session token could go to an attacker's site. Fixed in v24.4.23 ([GHSA-5rxf-pwv4-5fm9](https://github.com/polterguy/magic/security/advisories/GHSA-5rxf-pwv4-5fm9)).
- Eight advisories in [lean-ctx](https://github.com/yvgude/lean-ctx), from workspace trust gaps to symlinks in a cloned repository that carry writes out of the project. Two of them cover paths an earlier fix in the same series missed.
- Two fixes merged in [hashcat](https://github.com/hashcat/hashcat), a heap use-after-free in the brain server ([#5085](https://github.com/hashcat/hashcat/pull/5085)) and a wrong plain written for 32 to 39 byte passwords on slow hashes with rules and `-O` ([#5087](https://github.com/hashcat/hashcat/pull/5087)).

Each bug class I report also becomes Semgrep rules with positive and negative tests in
[semgrep-rules](https://github.com/kasparovabi/semgrep-rules). The loopback server rules
are open upstream as [semgrep/semgrep-rules#4125](https://github.com/semgrep/semgrep-rules/pull/4125).

Smaller work in between. I send fixes to projects that still import modules removed
from the standard library in Python 3.12 and 3.13 (cgi, pipes, telnetlib, uu and a few
more), and I answer questions in GitHub Discussions, with accepted answers in
[sqlmodel](https://github.com/fastapi/sqlmodel/discussions/2117),
[semantic-release](https://github.com/semantic-release/semantic-release/discussions/4328),
[reflex](https://github.com/reflex-dev/reflex/discussions/7730) and
[django-rest-framework](https://github.com/encode/django-rest-framework/discussions/10110).

From August to October most of my upstream fixes were retired Claude model ids. A
retired id does not fall back, the API returns an error, so a skill or plugin still
shipping one is broken for everyone who runs it. The hard part was leaving alone the
ids that belong where they are, such as pricing tables, recorded API responses in test
fixtures and SDK constants named after the model they hold.

<!-- OZET:BASLA -->
**Open source record.** 19 published security advisories with reporter credit and 40 fixes merged into other projects. Full list with links in [security-research](https://github.com/kasparovabi/security-research).
<!-- OZET:BITIR -->

### Selected work

| Repository | What it is |
|---|---|
| [security-research](https://github.com/kasparovabi/security-research) | Coordinated disclosures, published advisories and the fixes merged upstream |
| [semgrep-rules](https://github.com/kasparovabi/semgrep-rules) | Detection rules derived from these advisories, with tests and a guide per bug class |
| [claude-audit-20](https://github.com/kasparovabi/claude-audit-20) | Twenty failure classes as write-time coding rules, then a twenty-pass audit with a false-positive filter as the last pass |
| [drama-3-tr](https://github.com/kasparovabi/drama-3-tr) | Fish Audio Drama 3 in Turkish on one 16 GB GPU, with a distilled 32-expert speaker |
| [dsh-studio](https://github.com/kasparovabi/dsh-studio) | Unofficial native macOS client for dsh, the DeepSeek agent harness |
| [busted](https://github.com/kasparovabi/busted) | Mac desk guard that catches snoops |

### How I work with agents

Verify before reporting. Agents get the confidence wrong more often than the code.
Every claim in the work above has to survive a check that tries to refute it, and every
past false positive becomes a permanent test case so the same mistake cannot ship twice.

You can reach me at kasparovabi@gmail.com.
