## About
Notes and example on using Jev.


## Prerequisites

In this project we use Jev with OpenRouter. See more in the official OpenRouter's [documentation](https://openrouter.ai/docs/guides/community/jev).


## Requirements

- Python 3.12
- [UV](https://docs.astral.sh/uv/)
- [OpenRouter](https://openrouter.ai/) API key


## Usage

Step 1. Install dependencies:
```bash
uv sync
```

Step 2. Create the <ins>.env</ins> file with your OpenRouter API key. See [.env example](./.env.example)

Step 3. Explore the [Notebook](./main.ipynb)

Step 4. Select the kernel (<ins>./venv/bin/python</ins>), and run the cells.


## Jev Notes

- Jev is neither an LLM nor its replacement.

- Jev is a *System One* model, designed to make structured decisions based on the input state and questions, providing probabilities and confidence.

- Jev cannot return an option outside the schema.

- Jev is designed for consistency rather than determinism.

- Jev parallelizes processing of multiple structured questions in a single request.

- Jev's primitives:
	1. [Choice](https://docs.typesafe.ai/primitives/choice) - pick one option from a list you define and returns a probability for every option.
	2. [Noul](https://docs.typesafe.ai/primitives/noul) - yes/no question by returning the probability that it is true.
	3. [Score](https://docs.typesafe.ai/primitives/score) - place the input on an ordered scale you define, such as low, medium, and high.

- Jev expects 2 attributes in its input:
  1. [State](https://docs.typesafe.ai/sdk/python/api/types/questions#state): text or JSON describing the current situation.
  2. [Questions](https://docs.typesafe.ai/sdk/python/api/types/questions#questions): decisions you want it to make about that state.

- When to use Jev:
	1. Model routing.
	2. Tool risk gating.
	3. Verification and supervision.

- When not to use Jev:
	1. Jev can't write a response, summarize documents, generate code, or explain its reasoning.
	2. Jev is unreliable for arithmetic, counting, date comparison, or exact string manipulation.
	3. Jev struggles when a solution requires multiple reasoning steps.
	4. Jev can't extract an unknown value directly. Find candidate values first, then let Jev choose among them.
	5. Irrelevant context can reduce accuracy. Send only the state required for the decision.
	6. Closed weights, early access, text-only input, and limited independent calibration data make it too early for blind trust.

<hr>


## References

- Official Documentation:
  - [Jev quickstart](https://docs.typesafe.ai/introduction/quickstart)
  - [OpenRouter + Jev](https://openrouter.ai/docs/guides/community/jev)

- Blog:
  - [Jev’s Architecture Unmasked](https://archerhume.com/posts/jevs-architecture-unmasked/)
  - [Introducing System One Models & Jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev)

- Other:
  - [Jev cheatsheet](https://jev-cheatsheet.vercel.app/)
