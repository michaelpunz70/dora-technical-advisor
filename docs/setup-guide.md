# Setup Guide — Local-First Research Configuration

**Status: documented configuration and reproducibility procedure; no deployment certification or completed model evaluation.** Application labels and capabilities depend on installed versions.

## Architecture and baseline

LM Studio serves local LLM inference through an OpenAI-compatible endpoint. AnythingLLM Desktop handles document ingestion, chunking, local embeddings, and retrieval using embedded LanceDB. The intended inference backend on the project Mac is Apple Silicon Metal.

```text
Public documents → AnythingLLM local embeddings → LanceDB
User query → retrieval (Top-K = 6) → context + workspace prompt
           → LM Studio (localhost:1234) → draft response → human source review
```

| Component | Project baseline |
| --- | --- |
| Hardware | MacBook Air M3; 16 GB unified memory |
| Historical OS label | macOS Sequoia 15.6.1; actual run version must be recorded |
| LM Studio endpoint | `http://localhost:1234/v1` |
| RAG engine / database | AnythingLLM Desktop / LanceDB |
| Embedding | Built-in local embedder; exact artifact and version pending |
| Chat mode | Query; this is not a guarantee against unsupported output |
| Retrieval | Top-K 6; similarity threshold 0.25 as recorded in the original configuration |
| Corpus | 9 regulatory PDFs, 6 mapping Markdown files, 3 context PDFs |

The previously stated 20 GB free disk space is an initial planning estimate, not a tested minimum. Storage depends on the number and size of model artifacts, vector data, and backups. Six models may require substantially more space. Memory use depends on model architecture, quantisation, context length, runtime settings, and other applications. Successful execution of every candidate on 16 GB has not been demonstrated.

## 1. Record the environment

Before installation or testing, record OS version, application versions, hardware, available storage, and any configured external services. Download applications from [LM Studio](https://lmstudio.ai/) and [AnythingLLM Desktop](https://anythingllm.com/download). Check their current requirements and publisher documentation for the installed versions.

## 2. Select and identify a local model

The six candidate labels and unverified inventory specifications are retained in [evaluation-results.md](../tests/evaluation-results.md). Record the publisher model ID, artifact URL, filename, hash, format, quantisation, context limit, and license. Do not infer architecture or compatibility solely from a display label. Begin with an artifact that fits available memory; log loading failures, swap pressure, or incomplete runs rather than reporting them as successful evaluation.

The server base address is `http://localhost:1234`; the API base path is shown below.

## 3. Configure local inference and embeddings

Start LM Studio's server at the intended local endpoint and check Metal acceleration where available. Verify the actual listening interface and loopback-only exposure if that is the intended boundary.

In AnythingLLM, select the LM Studio provider and base URL `http://localhost:1234/v1`, a local embedding provider, and LanceDB. Record exact settings. Disable unneeded external connectors, agent tools, or cloud providers. Review download, update, and telemetry behaviour separately; configuration alone does not prove that no outbound traffic occurs.

## 4. Prepare and ingest the corpus

Use [document-sources.md](document-sources.md) for the source inventory and original download links. Record exact source versions and provenance before ingestion. Create a workspace named **DORA Technical Implementation Advisor** and ingest the 18 baseline documents. Confirm that extraction succeeded, especially for PDF tables, and record document and chunk counts.

Do not count `.gitkeep` placeholders or assume that source PDFs are committed. Confirm the local embedding artifact has been obtained before attempting offline use.

## 5. Apply workspace settings

Set Query mode, Top-K **6**, and similarity threshold **0.25** where supported. Record the threshold's interpretation for the installed version; it is a project setting rather than a validated optimum. Record chunk size, overlap, context window, temperature, sampling parameters, maximum output length, and conversation/reset policy.

Copy the prompt from [system-prompt.md](../config/system-prompt.md). Keep a snapshot or digest of the prompt used for each run.

## 6. Check retrieval and source support

Use a public regulatory query. Inspect retrieved chunks and compare each legal statement with the official source. Check that citations point to supporting text, that proposed technologies are labelled as examples, and that missing context leads to a bounded answer. A plausible response does not establish successful retrieval or factual correctness.

## 7. Run the planned evaluation

Use the 30 cases in [test-queries.md](../tests/test-queries.md) and the recording procedure in [evaluation-results.md](../tests/evaluation-results.md). The methodology is planned; no completed comparative results are evidenced in the supplied repository.

Keep corpus, prompt, retrieval settings, generation settings, and reset policy constant where feasible. Document any necessary model-specific changes and their effect on comparability. Save raw responses and retrieved context, not only averages.

## Privacy and security review

Use public documents and synthetic prompts until the deployment has been assessed. Review storage and deletion of files, embeddings, conversation history, logs, caches, and backups; host access and encryption; application provenance and updates; server exposure; and outbound network behaviour. Local-first architecture does not establish GDPR compliance, zero telemetry, or suitability for a bank's internal network.

The project does not include a network trace, penetration test, organisational approval, or evidence of production operation. Prompt instructions are behavioural guidance, not an access control or a reliable defence against prompt injection.

## Troubleshooting and evidence

| Observation | Action and evidence to retain |
| --- | --- |
| No relevant retrieval | Check extraction, embeddings, indexing, and settings; save retrieved passages. |
| Incorrect legal citation | Check the official article; record whether retrieval or generation caused the error. |
| Model cannot load / out of memory | Record artifact and settings, failure, and any changes; do not fabricate a score. |
| Unexpected network connection | Identify component and purpose; adjust configuration or controls and verify again. |
| Corpus or prompt changes | Create a new configuration snapshot and rerun affected cases. |
