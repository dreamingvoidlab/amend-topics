# Amend Topics

Declarative field rules for Apache Kafka®: enforce on the wire, amend history exactly once.

Amend Topics applies one ruleset of JSON field rules (remove, mask, or hash a field) in two places: on live traffic,
through serializer and deserializer wrappers for producers and consumers, and on data already written, through a
command-line tool that rewrites a topic into a clean copy with exactly-once semantics. Privacy remediation is the lead
use case; the rules are general.

**Pre-release:** v0.1.0 in progress.

## License

Licensed under the [Apache License, Version 2.0](LICENSE).

---

Apache, Apache Kafka, Kafka, and the Kafka logo are either registered trademarks or trademarks of the Apache Software
Foundation in the United States and/or other countries. No endorsement by The Apache Software Foundation is implied by
the use of these marks.
