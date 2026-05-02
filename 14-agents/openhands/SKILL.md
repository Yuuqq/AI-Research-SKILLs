---
  title: "OpenHands"
  description: "Autonomous AI software engineering agent (formerly OpenDevin) that can write code, run commands, browse the web, and interact with files. Runs in sandboxed Docker environments. Supports 50+ LLM backends. Use for automated research coding, experiment implementation, and autonomous repository management."
  skillName: "openhands"
  skillVersion: "1.0.0"
  skillAuthor: "Orchestra Research"
  skillLicense: "MIT"
  skillTags: ["Agents", "OpenHands", "Autonomous Coding", "Software Engineering", "Docker", "Code Generation", "Research Automation", "Multi-LLM"]
  skillDeps: ["openhands-ai", "docker"]
  ---

  | | |
  |---|---|
  | **Version** | 1.0.0 |
  | **Author** | Orchestra Research |
  | **License** | MIT |
  | **Tags** | `Agents` `OpenHands` `Autonomous Coding` `Software Engineering` `Docker` |
  | **Dependencies** | `openhands-ai` `docker` |


  # OpenHands — Autonomous AI Software Engineer

  Formerly OpenDevin. An AI agent that writes code, runs experiments, and manages repositories autonomously.

  ## When to use OpenHands

  **Use OpenHands when:**
  - Automating research experiment implementation
  - Autonomous codebase exploration and modification
  - Running multi-step coding tasks without human intervention
  - Integrating with GitHub for PR creation and review
  - Building research pipelines that write their own code

  **Metrics**:
  - **40,000+ GitHub stars**
  - **50+ LLM backends** supported
  - Sandboxed Docker execution (safe by default)
  - Can browse web, run terminal, edit files autonomously

  ## Quick start

  ```bash
  # Using Docker (recommended)
  docker pull docker.all-hands.dev/all-hands-ai/runtime:0.38-nikolaik

  docker run -it --rm --pull=always \
      -e SANDBOX_RUNTIME_CONTAINER_IMAGE=docker.all-hands.dev/all-hands-ai/runtime:0.38-nikolaik \
      -e LOG_ALL_EVENTS=true \
      -v /var/run/docker.sock:/var/run/docker.sock \
      -p 3000:3000 \
      --add-host host.docker.internal:host-gateway \
      --name openhands-app \
      docker.all-hands.dev/all-hands-ai/openhands:0.38

  # Access web UI at http://localhost:3000
  ```

  ### Python API

  ```python
  from openhands.core.main import create_runtime, run_controller
  from openhands.core.config import AppConfig, SandboxConfig, LLMConfig

  # Configure
  config = AppConfig(
      llm=LLMConfig(
          model="claude-sonnet-4-5-20250929",
          api_key="your-api-key"
      ),
      sandbox=SandboxConfig(
          base_container_image="python:3.12-slim"
      )
  )

  # Run autonomous task
  task = """
  Implement a GRPO training loop using TRL.
  The script should:
  1. Load a base model (e.g., Qwen2.5-1.5B)
  2. Define a reward function based on format compliance
  3. Run 100 training steps and log metrics to W&B
  4. Save the final checkpoint
  """

  await run_controller(config=config, initial_user_action=task)
  ```

  ### Research automation workflow

  ```python
  from openhands_ai import OpenHands

  client = OpenHands(api_key="your-key")

  # Autonomous experiment implementation
  session = client.create_session(
      llm_config={"model": "claude-opus-4-5", "temperature": 0.1},
      sandbox_config={"image": "pytorch/pytorch:2.5.1-cuda12.4-cudnn9-runtime"}
  )

  result = session.run("""
  Read the paper at ./papers/flash_attention_3.pdf.
  Implement the core algorithm in PyTorch.
  Run a benchmark comparing throughput vs standard attention on seq_len=[512, 1024, 2048, 4096].
  Generate a plot and save to ./results/benchmark.png.
  """)

  print(result.summary)
  print(result.files_created)
  ```

  ## GitHub integration

  ```python
  # Resolve GitHub issues autonomously
  resolver = GitHubIssueResolver(
      github_token="ghp_...",
      llm_config={"model": "claude-sonnet-4-5-20250929"},
  )

  # Process a batch of issues
  resolver.resolve_issues(
      repo="your-org/research-repo",
      issue_numbers=[42, 43, 44],
      max_iterations=50  # per issue
  )
  ```

  ## Key capabilities

  | Capability | Description |
  |-----------|-------------|
  | **File editing** | Read, write, and refactor code files |
  | **Terminal** | Run bash commands, pip installs, training scripts |
  | **Web browsing** | Fetch papers, documentation, GitHub repos |
  | **GitHub** | Create PRs, resolve issues, review code |
  | **Jupyter** | Execute notebooks interactively |
  | **Multi-step planning** | Break down complex research tasks |

  ## Supported LLM backends

  ```yaml
  # config.toml
  [llm]
  model = "claude-sonnet-4-5-20250929"
  # OR
  model = "gpt-4o"
  model = "gemini/gemini-2.0-flash"
  model = "ollama/llama3.2"
  model = "deepseek/deepseek-chat"
  ```

  ## Best practices for research

  - Use **Claude Opus/Sonnet** for complex multi-step research tasks
  - Set `max_iterations=100` for long experiments
  - Mount your dataset directory as a volume: `-v /data:/workspace/data`
  - Use `LOG_ALL_EVENTS=true` to trace agent decisions
  - For reproducibility: pin the runtime container version

  ## Common pitfalls

  - **Docker not running**: OpenHands requires Docker daemon
  - **Context window exceeded**: Break large tasks into subtasks
  - **Infinite loops**: Set `max_iterations` as a hard stop
  - **Slow startup**: Runtime container pull can take 2–5 minutes first time

  ## References
  - [OpenHands GitHub](https://github.com/All-Hands-AI/OpenHands)
  - [Documentation](https://docs.all-hands.dev/)
  - [Model Support](https://docs.all-hands.dev/usage/llms)
  