# Safety


## LLM Safety

The main safety benchmarks used in this repo are:
- AILuminate (ML Commons): <https://github.com/mlcommons/ailuminate>
- XSTest: <https://github.com/paul-rottger/exaggerated-safety>
- AgentHarm (AISI): <https://github.com/UKGovernmentBEIS/inspect_evals/tree/main/src/inspect_evals/agentharm>

Use AISI's Inspect AI for running the safety benchmark datasets on the models: <https://inspect.ai-safety-institute.org.uk/>

Use Inspect AI VSCode to run experiments and view logs in a graphical interface: <https://inspect.ai-safety-institute.org.uk/vscode.html>

### AILuminate



### XSTest:

Exaggerated safety behaviours in LLMs: <https://arxiv.org/abs/2308.01263>

```sh
inspect eval inspect_evals/xstest --model openai/gpt-4o
```

### AgentHarm

Use AgentHarm directly (<https://github.com/UKGovernmentBEIS/inspect_evals/tree/main/src/inspect_evals/agentharm>):

```sh
inspect eval inspect_evals/agentharm --model openai/gpt-4o
```

Agentharm with benign behaviours:

```sh
inspect eval inspect_evals/agentharm_benign --model openai/gpt-4o
```

Chat-only version of the harmful tasks:

```sh
inspect eval inspect_evals/agentharm_benign --model openai/gpt-4o -T chat_dataset=True
```

Specify using the validation split:

```sh
inspect eval inspect_evals/agentharm --model openai/gpt-4o -T split=val
```

View log:

```sh
inspect view
```
