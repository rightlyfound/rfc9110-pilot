# Disagreement Measurement

## Inputs

- annotations/pass1.json
- annotations/pass2.json
- claims.txt

## Per-claim disagreement

Claim c disagrees if any of:

- upstream(c, pass1) ≠ upstream(c, pass2) as sets of (rfc, section, quote)
- open_slots(c, pass1) ≠ open_slots(c, pass2) as sets of (slot_type, description)
- header_fenced(c, pass1) ≠ header_fenced(c, pass2)

Set comparison is literal string equality on the tuple fields.
No semantic merging. No fuzzy matching. If it doesn't match, it's
disagreement.

## Rate

  denominator = 20 − count(header_fenced in either pass)
  numerator   = count(claims disagreeing)
  rate        = numerator / denominator

Report the claim ids that disagree. That list is the finding.

## Threshold

  pass  if rate ≤ 0.10
  fail  if rate >  0.10

## Residual

Claims with no disagreement are mechanically clean, not verified.
The absence of annotator disagreement does not mean the binding is
correct — both annotators may have made the same error. The residual
is out of scope for this pilot.
