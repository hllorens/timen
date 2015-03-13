We developed TIMEN as a resource that given a timex and a set of features outputs the timex's normalized value. A timex often cannot be normalized in isolation -- it may need context information such as temporal references consisting of previous timexes.

In order to handle this favouring independence and modularity, TIMEN is divided into modules:

  * xml\_wrapper, which takes TimeML and manages document-level timex extraction and annotation, and [tnf](tnf.md) generation;
  * [timen\_consumer](timen_consumer.md), An application which uses TIMEN to normalize a list of timexes. This controls timex processing flow and saves previously normalized timexes in order to track reference time.
  * [timen](timen.md), A library that contains functions for normalizing input timexes given a set of features and an input language. This also handles language-specific mappings (e.g. from weekday names to weekday numbers) and rule data.

Our system takes a document containing delimited timexes as input and generates an intermediate description (shown in our full paper) of each timex that includes information such as part-of-speech, applicable reference time and linguistic context. These descriptions are then passed to the TIMEN component, which generates TIMEX3-format normalized interpretations.

Based on a feature description of a timex, TIMEN normalizes the timex using language knowledge (e.g. month name to month number mappings) and the rule databases. Rules operate on a constraint-satisfaction basis. The most-constraining rule that satisfies each timex's feature description is chosen for normalization first. We introduce the normalisation rule syntax in our full paper and its complete documentation is included with TIMEN.


There are two distinct stores of information local to TIMEN:

  * [Knowledge base](KB.md) - these are language-specific, and contain static mappings of strings such as weekday names and month names to an interlingua representation (e.g. 'Monday' => 'day0')
  * [Rule base](Rulebase.md) - rules for converting a timex described as features in TNF into a TIMEX3 annotation.

In this technical documentation, we define:

  * [Rule syntax](Rule_syntax.md)
  * [System architecture](Architecture.md)
  * [Knowledge base syntax](KB_syntax.md)