# @brizz/sdk

## 0.2.0

### Minor Changes

- The 0.2 line is built on OpenTelemetry JS 3 (`@opentelemetry/api` 1.10) and needs Node.js 22.15 or
  later, as 0.1.55–0.1.59 did. Apps that need `@opentelemetry/api` 1.9 should stay on 0.1.x
  (`@brizz/sdk@latest-0.1`, 0.1.60 or later).
- Releases of the 0.1.x line are listed in
  [CHANGELOG-0.1.md](https://github.com/brizzai/brizz-js/blob/HEAD/typescript/CHANGELOG-0.1.md).

## 0.1.59

### Patch Changes

- `decisionCall()` and `recordDecisionCall()` trace calls to classification models that your own
  code makes. Requires a Brizz backend that reads decision calls; calls sent to an older one are not
  shown with their answers, and are priced only when you set their cost.

## 0.1.58

### Patch Changes

- Add `@brizz/sdk/session`, a lightweight entry point for the session and context helpers.

## 0.1.57

### Patch Changes

- More precise PII masking: long numbers that aren't card numbers are left intact.

## 0.1.56

### Patch Changes

- Improved trace accuracy for concurrent LangChain runs.

## 0.1.55

### Patch Changes

- Built on OpenTelemetry JS 3.x.
- Requires Node.js 22.15 or later.

## 0.1.54

### Patch Changes

- `setGlobalTracerProvider: false` keeps Brizz spans on their own provider, alongside your own
  OpenTelemetry setup.
- `Brizz.flush()` sends queued telemetry without shutting down.
- `getTracerProvider()` for instrumentations you construct yourself.

## 0.1.53

### Patch Changes

- Calls to TypeSafe models such as Jev are traced: each call records the state, the questions and
  the answers.
- Masking leaves numbers and booleans unchanged unless a rule actually masks part of them.

## 0.1.52

### Patch Changes

- LangChain tool calls that fail or are cancelled are now linked to the model request that made them
  (requires `@langchain/core` 1.1.28 or later).

## 0.1.51

### Patch Changes

- Default masking leaves identifiers, custom properties and numeric values unchanged.

## 0.1.50

### Patch Changes

- `recordMetric` accepts `scope: 'trace'`, so a metric reported once per turn keeps one value per
  turn; the session reads as the average of its turns.

## 0.1.49

### Patch Changes

- LangGraph checkpoint tracking now works in ESM apps without passing
  `instrumentModules: { langgraph }`.

## 0.1.48

### Patch Changes

- `recordMetric` accepts `serviceName` and `traceId`, so one evaluation job can score conversations
  across several services. A metric with only a `traceId` is attached to that trace's session.
- A custom log exporter shared by several services is now shut down once, after every service has
  flushed, instead of dropping the records still buffered for the other services.

## 0.1.47

### Patch Changes

- Improved session attribution for LangChain runs in CommonJS applications.

## 0.1.46

### Patch Changes

- Improve LangGraph tracing for conversations that resume from an earlier point.
- Stop reporting a LangGraph graph that pauses for input as a failed run.

## 0.1.45

### Patch Changes

- Improved session attribution for concurrent LangChain runs: the session and account set on the
  Brizz context now travel with each LangChain run, so a span started inside another request's async
  context is still attributed to its own session.

## 0.1.44

### Patch Changes

- Add session tracking for stateless MCP servers. Tool calls from one client now group into a single
  session, with an optional note of what the caller was trying to do. Off by default; enable with
  `mcpSessionTracking`.

- Added `startAgent(...)`, `withAgent(...)` and `setAgent(...)` to mark work that runs as a
  subagent, so its conversation shows as its own lane instead of mixing into the main transcript.
  Works when the subagent runs in a background job too.

## 0.1.42

### Patch Changes

- Added `callWithServiceName(...)` to report part of a process under a different service name.

## 0.1.41

### Patch Changes

- MCP servers now open a session for tool calls only, so listing tools no longer adds empty sessions
  alongside them. Tool schemas are still captured either way.

## 0.1.40

### Patch Changes

- Added `setSessionId(...)` to set the session on the current turn, for when the enclosing span
  already exists — such as inside an MCP tool handler.

- MCP servers that don't use the transport's session management now get a session automatically, so
  their tool calls appear in session views instead of being left out.

## 0.1.39

### Patch Changes

- Modules passed to `instrumentModules` are now instrumented when `disableNodeSdk` is set, so manual
  instrumentation works alongside your own OpenTelemetry setup.

## 0.1.38

### Patch Changes

- Add `recordMetric` to report your own scores and measurements on a conversation.

- Simplified Node.js setup — initialize with `Brizz.initialize()`.

- Removed the unused `vercelAI` and `google_aiplatform` options from `instrumentModules`.

## 0.1.37

### Patch Changes

- Improve OpenAI streaming support, including tool calls and token usage on streamed responses.

## 0.1.36

### Patch Changes

- Add a `tools` option to `callWithMute` / `withMute` to hide or keep tool calls independently of
  the assistant reply. Requires a Brizz backend that understands `brizz.mute.tools`; against an
  older one, the tools-only form (`{ input: false, output: false, tools: true }`) mutes nothing.

## 0.1.35

### Patch Changes

- Add Gemini support: instrument the `@google/genai` client with `instrumentGoogleGenAI` from
  `@brizz/sdk/google-genai`.

## 0.1.33

### Patch Changes

- Add typed setters to identify users, organizations, and messages.
- Add `recordFeedback` to capture end-user reactions on a message or conversation.

## 0.1.32

### Patch Changes

- Add Vercel eve support: wire an eve agent to Brizz in one line with `createEveOtelConfig` from
  `@brizz/sdk/eve`.

## 0.1.31

### Patch Changes

- Support Vercel AI SDK v7.

## 0.1.30

### Patch Changes

- Reduce the SDK's install footprint.

## 0.1.29

### Patch Changes

- Add `dsn` / `BRIZZ_DSN` support for Brizz Server DSN configuration
- Add `callWithMute` / `withMute` to omit user and/or assistant content for calls made within a
  block.
- Improve reliability of built-in PII masking patterns.

## 0.1.28

### Patch Changes

- Attach external links to a session.

## 0.1.27

### Patch Changes

- Recognize human-in-the-loop tool calls from the Vercel AI SDK so they appear distinctly in Brizz
  conversations.

## 0.1.26

### Patch Changes

- Internal refinement to MCP tool-registration instrumentation.

## 0.1.25

### Patch Changes

- PII masking improvements.

## 0.1.24

### Patch Changes

- Capture MCP tool JSON schemas at registration

## 0.1.22

### Patch Changes

- Add MCP (Model Context Protocol) instrumentation. Pass your transport modules and
  `@modelcontextprotocol/sdk/shared/protocol.js` via `instrumentModules.mcp` in `Brizz.initialize()`
  to capture MCP client and server traces.

## 0.1.21

### Patch Changes

- Simplify LangChain setup. Install command is now just `@brizz/sdk @langchain/core`.

## 0.1.20

### Patch Changes

- Fix dropped LangChain spans. `@langchain/core` and
  `@arizeai/openinference-instrumentation-langchain` are now optional peer deps — install them
  alongside `@brizz/sdk` if you use LangChain.

## 0.1.19

### Patch Changes

- Extend `Session.setInput(text, context?)` / `Session.setOutput(text, context?)` to accept an
  optional per-turn context bag. Each call now appends both the text and the bag to parallel
  index-aligned span attributes `brizz.session.input.context` / `brizz.session.output.context`; the
  dashboard renders the bag under a collapsible Context panel on that turn's message.

## 0.1.18

### Patch Changes

- Support `openai@6` (used by `@langchain/openai@1+`).
- Add `beforeSendSpan` filter, `resourceAttributes`, and `appVersion` init options.

## 0.1.17

### Patch Changes

- Add `disableSpanExporter` option (also via `BRIZZ_DISABLE_SPAN_EXPORTER=true` env var) to skip
  span exporter/processor setup. `NodeSDK` still starts and metrics/logs keep working — only spans
  are suppressed. Useful for dev/test environments where you want to keep `Brizz.initialize()` in
  code without sending span data.

## 0.1.16

### Patch Changes

- Add `startSessionTitle()` to exclude title generation LLM calls from conversation view
- Add `mode: 'title'` option to `startSession()`
- Add `Session.setTitle()`

## 0.1.15

### Patch Changes

- Add `getActiveSession()` to retrieve the current session without passing it explicitly

## 0.1.14

### Patch Changes

- Fix crash when `@langchain/core` is not installed by lazily loading LangChain instrumentation via
  dynamic `import()`
- Move `@arizeai/openinference-instrumentation-langchain` to optionalDependencies

## 0.1.13

### Patch Changes

- Fix LangChain instrumentation for CJS based projects

## 0.1.12

### Patch Changes

- Handle LangCain instrumentation along with Langsmith

## 0.1.11

### Patch Changes

- Handle running along Sentry

## 0.1.10

### Patch Changes

- Added optional `extraProperties` parameter to `withSessionId` and `startSession` for propagating
  custom properties to all spans within a session

## 0.1.9

### Patch Changes

- Added `startSession` API for manual input/output tracking with `setInput()` and `setOutput()`
  methods

## 0.1.8

### Patch Changes

- Support Langchain

## 0.1.7

### Patch Changes

- Add SDK version tags to ResourceAttributes

## 0.1.6

### Patch Changes

- Exported withProperties to add custom properties to traces

## 0.1.5

### Patch Changes

- Added optional `environment` parameter to SDK initialization for deployment environment tagging
- Removed Vercel AI transformation from the SDK

## 0.1.4

### Patch Changes

- Added withSessionId wrapper function

## 0.1.3

### Patch Changes

- support for vercel ai sdk builtin telemetries

## 0.1.2

### Patch Changes

- minor esm fixes

## 0.1.1

### Patch Changes

- miner bug fixes

## 0.1.0

### Patch Changes

- Graduate version

## 0.1.0-alpha.6

### Patch Changes

- Initial release
