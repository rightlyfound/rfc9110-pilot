# rfc9110-pilot

Measures cross-document binding disagreement on 20 hand-written claims
against RFCs 9110, 9111, 9112, 2119, 8174.

## Protocol

1. Fixture frozen at tag `pilot-fixture-v1`.
2. Annotator A produces annotations/pass1.json.
3. Wait 14 days.
4. Annotator B (same person) produces annotations/pass2.json.
5. Run measure.py. The disagreement rate is the finding.

## Files

- claims.txt            — 20 claims, frozen
- annotator_protocol.md — what the annotator is given
- annotation_format.json— output schema
- disagreement_measurement.md — scoring
- entity_model.json     — shared glossary, extended during pass 1
- header_fence_rule.md  — exclusion rule
- annotations/          — pass1.json, pass2.json

## Timeline

  T0        freeze (tag pilot-fixture-v1)
  T0        pass 1 recorded
  T0+14d    pass 2 recorded
  T0+14d    measure

## Success

  disagreement rate ≤ 0.10  → pass
  disagreement rate >  0.10  → fail, report the ids
