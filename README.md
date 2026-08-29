# Scribe

Report engine for the [Citadel](https://github.com/sltcnb/citadel) pipeline. Turns a case timeline, its findings and its evidence into a document someone will actually read.

The same case has to be explained to different people. Scribe renders one case into Markdown, graphical HTML or DOCX, so the technical appendix and the summary a client sees come from the same source of truth instead of being retyped.

## Install

```bash
pip install git+https://github.com/sltcnb/scribe
```

Python 3.11 or newer.

## Rendering

```python
from scribe.render import merge_template
from scribe.document import Document

doc = merge_template(template, case_data)
```

| Module | Role |
|---|---|
| `render.py` | Template merge, event and aggregate tables, timestamp formatting |
| `document.py` | Document model the renderers share |
| `docx_render.py` | Word output |
| `labels.py` | Human-readable names for fields and artifact types |

## Templates

A template is merged with case data rather than assembled in code, so changing the wording of a report does not mean changing Python. Event tables, aggregate rows and timestamps are formatted by `render.py`, which keeps the same case rendering consistently across output formats.

`proofread()` flags the things that embarrass you in a delivered report: placeholders left unfilled, findings with no evidence attached, timestamps in mixed zones.

## Tests

```bash
pip install pytest
pip install -e .
pytest -q
```

## License

[PolyForm Noncommercial 1.0.0](LICENSE). Run, modify and self-host it for any noncommercial purpose. Commercial use needs written authorization from the copyright holder; see [LICENSING.md](LICENSING.md).

This is a source-available license, not an OSI-approved open source license.

## Related

[Citadel](https://github.com/sltcnb/citadel) · [Sigil](https://github.com/sltcnb/sigil) and [Anvil](https://github.com/sltcnb/anvil) produce the findings · [Pilot](https://github.com/sltcnb/pilot) writes the narrative · [citadel-contracts](https://github.com/sltcnb/citadel-contracts)
