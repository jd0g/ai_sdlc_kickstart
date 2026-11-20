# EARS Standard

Use the simplest applicable pattern. Do not add the pattern label to the controlled statement unless requested.

- Ubiquitous: `The <system> shall <response>.`
- Event-driven: `When <trigger>, the <system> shall <response>.`
- State-driven: `While <state>, the <system> shall <response>.`
- Optional feature: `Where <feature is enabled>, the <system> shall <response>.`
- Unwanted behavior: `If <undesired condition>, then the <system> shall <response>.`
- Complex: combine valid preconditions with one trigger and one response only when splitting would change meaning.

Name the responsible system/component, use one shall and one primary response, make conditions observable, quantify supported limits, exclude rationale from the normative sentence, and avoid unnecessary design detail.
