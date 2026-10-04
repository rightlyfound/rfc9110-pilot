# Annotator Protocol

## Input

- claims.txt (frozen at tag `pilot-fixture-v1`)
- Full text of RFC 9110, 9111, 9112, 2119, 8174
- header_fence_rule.md
- annotation_format.json
- entity_model.json (skeleton — extend as you go)

## Task

For each of the 20 claims, produce one object per annotation_format.json.

- upstream[]  = every source passage whose change would falsify the claim.
                Each entry needs a verbatim quote from the source.
- open_slots[] = every referent you could not bind with a quote.
- header_fenced = true if the binding is resolvable from header metadata
                  alone.
- annotator_notes = free text.

## Rules

- A binding is legitimate only if a verbatim quote supports it. No
  inference, no paraphrase.
- If you cannot find a quote, the binding is an open_slot, not an
  upstream entry.
- Uniqueness is a hint, not a binding. A single-bolt corpus does not
  bind "the bolt".
- Do not classify into (a)(b)(c)(d). That taxonomy is post-hoc.

## Output

- annotations/pass1.json (or pass2.json for the second reader)
- one JSON object per claim, array of 20.

## Do not

- Do not consult pass 1 while producing pass 2.
- Do not edit claims.txt.
- Do not add bindings to fill a count.
