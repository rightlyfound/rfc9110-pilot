# Header-Fence Rule

## Purpose

Exclude bindings resolvable from an RFC's metadata header alone
(Updates / Obsoletes / Normative References) without engaging body text.

## Rule

A binding is header-fenced (excluded from scoring) if:

1. The binding can be satisfied solely from the RFC's metadata header, AND
2. No body section is required to interpret the claim.

## Examples

Header-fenced (excluded):
- "RFC 9110 obsoletes RFC 7231."   (from Obsoletes header)
- "RFC 8174 updates RFC 2119."     (from Updates header)

Not header-fenced (included):
- "RFC 8174 clarifies lowercase 'must' has normal English meaning."
  (requires RFC 8174 §2)
- "A cache MUST NOT store a response with no-store directive."
  (requires RFC 9111 §5.2.2.5)

## Implementation

Annotator marks `header_fenced: true|false` per claim. Header-fenced
claims are retained in the dataset but excluded from the disagreement
rate denominator.
