# aiccm
## An LLM engine for running Collosal Cave Adventure.

### Option A - Manual Upload
For this option, you manually interact with the prompt interface for all fies.
1. You'll need to download all of the files from this repo from /src
2. Open Qwen3-Max and upload all 6 files. Qwen allows just 5 files at a time.
3. Paste this into the Qwen prompt:

`Read and parse the uploaded files. Begin the game as described.`

### Option B - Single GitHub Call
For this option, you just copy and paste this command into the LLM prompt:

```text
Access these files at:

https://raw.githubusercontent.com/robert-kurcina/aiccm/refs/heads/main/src/nodes.json
https://raw.githubusercontent.com/robert-kurcina/aiccm/refs/heads/main/src/items.json
https://raw.githubusercontent.com/robert-kurcina/aiccm/refs/heads/main/src/initial_state.json
https://raw.githubusercontent.com/robert-kurcina/aiccm/refs/heads/main/src/engine_schema.json
https://raw.githubusercontent.com/robert-kurcina/aiccm/refs/heads/main/src/edges.json
https://raw.githubusercontent.com/robert-kurcina/aiccm/refs/heads/main/src/llm_execution_guide.md

Read and parse the JSON files. Play the game as described.
```

## Screenshots
![Overview](/img/info.png)

![Scenarios](/img/sample.png)

