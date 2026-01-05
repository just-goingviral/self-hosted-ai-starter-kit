# Self-hosted AI Starter Kit - Complete Repository Snapshot

Generated: 2026-01-05T09:30:58.991295Z

This document contains the complete source code and configuration files from the self-hosted-ai-starter-kit repository. All text-based files are included with their full contents.

---

## Table of Contents

- [Root Files](#root-files)
- [.github Directory](#github-directory)
- [n8n Directory](#n8n-directory)
- [Binary Files](#binary-files)

---

## Root Files

### .env.example

**Path:** `.env.example`

```
POSTGRES_USER=root
POSTGRES_PASSWORD=password
POSTGRES_DB=n8n

N8N_ENCRYPTION_KEY=super-secret-key
N8N_USER_MANAGEMENT_JWT_SECRET=even-more-secret
N8N_DEFAULT_BINARY_DATA_MODE=filesystem

# For Mac users running OLLAMA locally
# See https://github.com/n8n-io/self-hosted-ai-starter-kit?tab=readme-ov-file#for-mac--apple-silicon-users
# OLLAMA_HOST=host.docker.internal:11434



```

---

### .gitignore

**Path:** `.gitignore`

```
.env
.DS_Store

```

---

### README.md

**Path:** `README.md`

```
# Self-hosted AI starter kit

**Self-hosted AI Starter Kit** is an open-source Docker Compose template designed to swiftly initialize a comprehensive local AI and low-code development environment.

![n8n.io - Screenshot](https://raw.githubusercontent.com/n8n-io/self-hosted-ai-starter-kit/main/assets/n8n-demo.gif)

Curated by <https://github.com/n8n-io>, it combines the self-hosted n8n
platform with a curated list of compatible AI products and components to
quickly get started with building self-hosted AI workflows.

> [!TIP]
> [Read the announcement](https://blog.n8n.io/self-hosted-ai/)

### What’s included

✅ [**Self-hosted n8n**](https://n8n.io/) - Low-code platform with over 400
integrations and advanced AI components

✅ [**Ollama**](https://ollama.com/) - Cross-platform LLM platform to install
and run the latest local LLMs

✅ [**Qdrant**](https://qdrant.tech/) - Open-source, high performance vector
store with an comprehensive API

✅ [**PostgreSQL**](https://www.postgresql.org/) -  Workhorse of the Data
Engineering world, handles large amounts of data safely.

### What you can build

⭐️ **AI Agents** for scheduling appointments

⭐️ **Summarize Company PDFs** securely without data leaks

⭐️ **Smarter Slack Bots** for enhanced company communications and IT operations

⭐️ **Private Financial Document Analysis** at minimal cost

## Installation

### Cloning the Repository

```bash
git clone https://github.com/n8n-io/self-hosted-ai-starter-kit.git
cd self-hosted-ai-starter-kit
cp .env.example .env # you should update secrets and passwords inside
```

### Running n8n using Docker Compose

#### For Nvidia GPU users

```bash
git clone https://github.com/n8n-io/self-hosted-ai-starter-kit.git
cd self-hosted-ai-starter-kit
cp .env.example .env # you should update secrets and passwords inside
docker compose --profile gpu-nvidia up
```

> [!NOTE]
> If you have not used your Nvidia GPU with Docker before, please follow the
> [Ollama Docker instructions](https://github.com/ollama/ollama/blob/main/docs/docker.md).

### For AMD GPU users on Linux

```bash
git clone https://github.com/n8n-io/self-hosted-ai-starter-kit.git
cd self-hosted-ai-starter-kit
cp .env.example .env # you should update secrets and passwords inside
docker compose --profile gpu-amd up
```

#### For Mac / Apple Silicon users

If you’re using a Mac with an M1 or newer processor, you can't expose your GPU
to the Docker instance, unfortunately. There are two options in this case:

1. Run the starter kit fully on CPU, like in the section "For everyone else"
   below
2. Run Ollama on your Mac for faster inference, and connect to that from the
   n8n instance

If you want to run Ollama on your mac, check the
[Ollama homepage](https://ollama.com/)
for installation instructions, and run the starter kit as follows:

```bash
git clone https://github.com/n8n-io/self-hosted-ai-starter-kit.git
cd self-hosted-ai-starter-kit
cp .env.example .env # you should update secrets and passwords inside
docker compose up
```

##### For Mac users running OLLAMA locally

If you're running OLLAMA locally on your Mac (not in Docker), you need to modify the OLLAMA_HOST environment variable

1. Set OLLAMA_HOST to `host.docker.internal:11434` in your .env file. 
2. Additionally, after you see "Editor is now accessible via: <http://localhost:5678/>":

    1. Head to <http://localhost:5678/home/credentials>
    2. Click on "Local Ollama service"
    3. Change the base URL to "http://host.docker.internal:11434/"

#### For everyone else

```bash
git clone https://github.com/n8n-io/self-hosted-ai-starter-kit.git
cd self-hosted-ai-starter-kit
cp .env.example .env # you should update secrets and passwords inside
docker compose --profile cpu up
```

## ⚡️ Quick start and usage

The core of the Self-hosted AI Starter Kit is a Docker Compose file, pre-configured with network and storage settings, minimizing the need for additional installations.
After completing the installation steps above, simply follow the steps below to get started.

1. Open <http://localhost:5678/> in your browser to set up n8n. You’ll only
   have to do this once.
2. Open the included workflow:
   <http://localhost:5678/workflow/srOnR8PAY3u4RSwb>
3. Click the **Chat** button at the bottom of the canvas, to start running the workflow.
4. If this is the first time you’re running the workflow, you may need to wait
   until Ollama finishes downloading Llama3.2. You can inspect the docker
   console logs to check on the progress.

To open n8n at any time, visit <http://localhost:5678/> in your browser.

With your n8n instance, you’ll have access to over 400 integrations and a
suite of basic and advanced AI nodes such as
[AI Agent](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/),
[Text classifier](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.text-classifier/),
and [Information Extractor](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.information-extractor/)
nodes. To keep everything local, just remember to use the Ollama node for your
language model and Qdrant as your vector store.

> [!NOTE]
> This starter kit is designed to help you get started with self-hosted AI
> workflows. While it’s not fully optimized for production environments, it
> combines robust components that work well together for proof-of-concept
> projects. You can customize it to meet your specific needs

## Upgrading

* ### For Nvidia GPU setups:

```bash
docker compose --profile gpu-nvidia pull
docker compose create && docker compose --profile gpu-nvidia up
```

* ### For Mac / Apple Silicon users

```bash
docker compose pull
docker compose create && docker compose up
```

* ### For Non-GPU setups:

```bash
docker compose --profile cpu pull
docker compose create && docker compose --profile cpu up
```

## 👓 Recommended reading

n8n is full of useful content for getting started quickly with its AI concepts
and nodes. If you run into an issue, go to [support](#support).

- [AI agents for developers: from theory to practice with n8n](https://blog.n8n.io/ai-agents/)
- [Tutorial: Build an AI workflow in n8n](https://docs.n8n.io/advanced-ai/intro-tutorial/)
- [Langchain Concepts in n8n](https://docs.n8n.io/advanced-ai/langchain/langchain-n8n/)
- [Demonstration of key differences between agents and chains](https://docs.n8n.io/advanced-ai/examples/agent-chain-comparison/)
- [What are vector databases?](https://docs.n8n.io/advanced-ai/examples/understand-vector-databases/)

## 🎥 Video walkthrough

- [Installing and using Local AI for n8n](https://www.youtube.com/watch?v=xz_X2N-hPg0)

## 🛍️ More AI templates

For more AI workflow ideas, visit the [**official n8n AI template
gallery**](https://n8n.io/workflows/categories/ai/). From each workflow,
select the **Use workflow** button to automatically import the workflow into
your local n8n instance.

### Learn AI key concepts

- [AI Agent Chat](https://n8n.io/workflows/1954-ai-agent-chat/)
- [AI chat with any data source (using the n8n workflow too)](https://n8n.io/workflows/2026-ai-chat-with-any-data-source-using-the-n8n-workflow-tool/)
- [Chat with OpenAI Assistant (by adding a memory)](https://n8n.io/workflows/2098-chat-with-openai-assistant-by-adding-a-memory/)
- [Use an open-source LLM (via Hugging Face)](https://n8n.io/workflows/1980-use-an-open-source-llm-via-huggingface/)
- [Chat with PDF docs using AI (quoting sources)](https://n8n.io/workflows/2165-chat-with-pdf-docs-using-ai-quoting-sources/)
- [AI agent that can scrape webpages](https://n8n.io/workflows/2006-ai-agent-that-can-scrape-webpages/)

### Local AI templates

- [Tax Code Assistant](https://n8n.io/workflows/2341-build-a-tax-code-assistant-with-qdrant-mistralai-and-openai/)
- [Breakdown Documents into Study Notes with MistralAI and Qdrant](https://n8n.io/workflows/2339-breakdown-documents-into-study-notes-using-templating-mistralai-and-qdrant/)
- [Financial Documents Assistant using Qdrant and](https://n8n.io/workflows/2335-build-a-financial-documents-assistant-using-qdrant-and-mistralai/) [Mistral.ai](http://mistral.ai/)
- [Recipe Recommendations with Qdrant and Mistral](https://n8n.io/workflows/2333-recipe-recommendations-with-qdrant-and-mistral/)

## Tips & tricks

### Accessing local files

The self-hosted AI starter kit will create a shared folder (by default,
located in the same directory) which is mounted to the n8n container and
allows n8n to access files on disk. This folder within the n8n container is
located at `/data/shared` -- this is the path you’ll need to use in nodes that
interact with the local filesystem.

**Nodes that interact with the local filesystem**

- [Read/Write Files from Disk](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.filesreadwrite/)
- [Local File Trigger](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.localfiletrigger/)
- [Execute Command](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.executecommand/)

## 📜 License

This project is licensed under the Apache License 2.0 - see the
[LICENSE](LICENSE) file for details.

## 💬 Support

Join the conversation in the [n8n Forum](https://community.n8n.io/), where you
can:

- **Share Your Work**: Show off what you’ve built with n8n and inspire others
  in the community.
- **Ask Questions**: Whether you’re just getting started or you’re a seasoned
  pro, the community and our team are ready to support with any challenges.
- **Propose Ideas**: Have an idea for a feature or improvement? Let us know!
  We’re always eager to hear what you’d like to see next.

```

---

### LICENSE

**Path:** `LICENSE`

```
                                 Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
      otherwise, or (ii) ownership of fifty percent (50%) or more of the
      outstanding shares, or (iii) beneficial ownership of such entity.

      "You" (or "Your") shall mean an individual or Legal Entity
      exercising permissions granted by this License.

      "Source" form shall mean the preferred form for making modifications,
      including but not limited to software source code, documentation
      source, and configuration files.

      "Object" form shall mean any form resulting from mechanical
      transformation or translation of a Source form, including but
      not limited to compiled object code, generated documentation,
      and conversions to other media types.

      "Work" shall mean the work of authorship, whether in Source or
      Object form, made available under the License, as indicated by a
      copyright notice that is included in or attached to the work
      (an example is provided in the Appendix below).

      "Derivative Works" shall mean any work, whether in Source or Object
      form, that is based on (or derived from) the Work and for which the
      editorial revisions, annotations, elaborations, or other modifications
      represent, as a whole, an original work of authorship. For the purposes
      of this License, Derivative Works shall not include works that remain
      separable from, or merely link (or bind by name) to the interfaces of,
      the Work and Derivative Works thereof.

      "Contribution" shall mean any work of authorship, including
      the original version of the Work and any modifications or additions
      to that Work or Derivative Works thereof, that is intentionally
      submitted to Licensor for inclusion in the Work by the copyright owner
      or by an individual or Legal Entity authorized to submit on behalf of
      the copyright owner. For the purposes of this definition, "submitted"
      means any form of electronic, verbal, or written communication sent
      to the Licensor or its representatives, including but not limited to
      communication on electronic mailing lists, source code control systems,
      and issue tracking systems that are managed by, or on behalf of, the
      Licensor for the purpose of discussing and improving the Work, but
      excluding communication that is conspicuously marked or otherwise
      designated in writing by the copyright owner as "Not a Contribution."

      "Contributor" shall mean Licensor and any individual or Legal Entity
      on behalf of whom a Contribution has been received by Licensor and
      subsequently incorporated within the Work.

   2. Grant of Copyright License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      copyright license to reproduce, prepare Derivative Works of,
      publicly display, publicly perform, sublicense, and distribute the
      Work and such Derivative Works in Source or Object form.

   3. Grant of Patent License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      (except as stated in this section) patent license to make, have made,
      use, offer to sell, sell, import, and otherwise transfer the Work,
      where such license applies only to those patent claims licensable
      by such Contributor that are necessarily infringed by their
      Contribution(s) alone or by combination of their Contribution(s)
      with the Work to which such Contribution(s) was submitted. If You
      institute patent litigation against any entity (including a
      cross-claim or counterclaim in a lawsuit) alleging that the Work
      or a Contribution incorporated within the Work constitutes direct
      or contributory patent infringement, then any patent licenses
      granted to You under this License for that Work shall terminate
      as of the date such litigation is filed.

   4. Redistribution. You may reproduce and distribute copies of the
      Work or Derivative Works thereof in any medium, with or without
      modifications, and in Source or Object form, provided that You
      meet the following conditions:

      (a) You must give any other recipients of the Work or
          Derivative Works a copy of this License; and

      (b) You must cause any modified files to carry prominent notices
          stating that You changed the files; and

      (c) You must retain, in the Source form of any Derivative Works
          that You distribute, all copyright, patent, trademark, and
          attribution notices from the Source form of the Work,
          excluding those notices that do not pertain to any part of
          the Derivative Works; and

      (d) If the Work includes a "NOTICE" text file as part of its
          distribution, then any Derivative Works that You distribute must
          include a readable copy of the attribution notices contained
          within such NOTICE file, excluding those notices that do not
          pertain to any part of the Derivative Works, in at least one
          of the following places: within a NOTICE text file distributed
          as part of the Derivative Works; within the Source form or
          documentation, if provided along with the Derivative Works; or,
          within a display generated by the Derivative Works, if and
          wherever such third-party notices normally appear. The contents
          of the NOTICE file are for informational purposes only and
          do not modify the License. You may add Your own attribution
          notices within Derivative Works that You distribute, alongside
          or as an addendum to the NOTICE text from the Work, provided
          that such additional attribution notices cannot be construed
          as modifying the License.

      You may add Your own copyright statement to Your modifications and
      may provide additional or different license terms and conditions
      for use, reproduction, or distribution of Your modifications, or
      for any such Derivative Works as a whole, provided Your use,
      reproduction, and distribution of the Work otherwise complies with
      the conditions stated in this License.

   5. Submission of Contributions. Unless You explicitly state otherwise,
      any Contribution intentionally submitted for inclusion in the Work
      by You to the Licensor shall be under the terms and conditions of
      this License, without any additional terms or conditions.
      Notwithstanding the above, nothing herein shall supersede or modify
      the terms of any separate license agreement you may have executed
      with Licensor regarding such Contributions.

   6. Trademarks. This License does not grant permission to use the trade
      names, trademarks, service marks, or product names of the Licensor,
      except as required for reasonable and customary use in describing the
      origin of the Work and reproducing the content of the NOTICE file.

   7. Disclaimer of Warranty. Unless required by applicable law or
      agreed to in writing, Licensor provides the Work (and each
      Contributor provides its Contributions) on an "AS IS" BASIS,
      WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
      implied, including, without limitation, any warranties or conditions
      of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A
      PARTICULAR PURPOSE. You are solely responsible for determining the
      appropriateness of using or redistributing the Work and assume any
      risks associated with Your exercise of permissions under this License.

   8. Limitation of Liability. In no event and under no legal theory,
      whether in tort (including negligence), contract, or otherwise,
      unless required by applicable law (such as deliberate and grossly
      negligent acts) or agreed to in writing, shall any Contributor be
      liable to You for damages, including any direct, indirect, special,
      incidental, or consequential damages of any character arising as a
      result of this License or out of the use or inability to use the
      Work (including but not limited to damages for loss of goodwill,
      work stoppage, computer failure or malfunction, or any and all
      other commercial damages or losses), even if such Contributor
      has been advised of the possibility of such damages.

   9. Accepting Warranty or Additional Liability. While redistributing
      the Work or Derivative Works thereof, You may choose to offer,
      and charge a fee for, acceptance of support, warranty, indemnity,
      or other liability obligations and/or rights consistent with this
      License. However, in accepting such obligations, You may act only
      on Your own behalf and on Your sole responsibility, not on behalf
      of any other Contributor, and only if You agree to indemnify,
      defend, and hold each Contributor harmless for any liability
      incurred by, or claims asserted against, such Contributor by reason
      of your accepting any such warranty or additional liability.

   END OF TERMS AND CONDITIONS

   APPENDIX: How to apply the Apache License to your work.

      To apply the Apache License to your work, attach the following
      boilerplate notice, with the fields enclosed by brackets "[]"
      replaced with your own identifying information. (Don't include
      the brackets!)  The text should be enclosed in the appropriate
      comment syntax for the file format. We also recommend that a
      file or class name and description of purpose be included on the
      same "printed page" as the copyright notice for easier
      identification within third-party archives.

   Copyright 2024-present n8n GmbH

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.

```

---

### CONTRIBUTING.md

**Path:** `CONTRIBUTING.md`

```
# Self-hosted AI Starter Kit - Vision & Contribution Guidelines

Awesome that you're interested in contributing to the Self-hosted AI Starter
Kit! These specific guidelines are in addition to the general [n8n
contribution
guidelines](https://github.com/n8n-io/n8n/blob/master/CONTRIBUTING.md).

## Vision Statement

The Self-hosted AI Starter Kit is designed to be **the fastest path from zero
to working AI workflows** for developers and organizations who want to
experiment with local, private AI solutions. It provides a curated,
pre-configured foundation that "just works" out of the box, enabling users to
focus on building AI workflows rather than wrestling with infrastructure
setup.

## Core Principles

### 1. Simplicity Over Completeness

The starter kit should prioritize ease of use and quick setup over
comprehensive feature coverage. It's better to do fewer things well than to
attempt to solve every possible use case.

### 2. Learning-Focused, Not Production-Ready

This is explicitly a **learning and experimentation platform**. Users should
be able to go from `git clone` to working AI workflows in minutes, not hours.
Production-grade concerns like high availability, advanced security, and
scalability are intentionally out of scope.

### 3. Opinionated but Extensible

We make opinionated choices about the core stack (n8n + Ollama + Qdrant +
PostgreSQL) to reduce decision paralysis, while providing clear paths for
users to extend and customize as they learn.

### 4. Privacy-First Local Development

Everything should work completely offline and locally by default. External
dependencies should be minimal and optional.

## What Belongs in the Starter Kit

### Core Components

- **n8n**: The workflow automation platform
- **Ollama**: Local LLM inference
- **Qdrant**: Vector database for embeddings
- **PostgreSQL**: Persistent data storage
- **Basic networking**: Simple Docker networking to connect components

### Essential Configuration

This includes:
- Pre-configured environment variables with sensible defaults
- Basic Docker Compose profiles for different hardware (CPU, GPU-Nvidia, GPU-AMD)
- Minimal volume mounts for data persistence
- Sample workflow demonstrating the core capabilities

### Getting Started Materials

This includes:
- Clear installation instructions for different platforms
- A demo workflow showcasing AI capabilities
- Basic documentation for accessing local files
- Links to relevant n8n documentation and templates

## What Doesn't Belong in the Starter Kit

### Production Infrastructure

Including:
- Reverse proxies
- SSL/TLS termination
- Load balancers
- Advanced monitoring and logging
- Backup and recovery systems
- Container orchestration beyond basic Docker Compose

### Advanced Networking

Including:
- Custom network configurations
- VPN integrations
- Multiple environment setups
- Advanced security hardening

### Alternative Technology Stacks

Including:
- Different vector databases
- Alternative workflow platforms
- Multiple LLM backends beyond Ollama
- Different databases for the core setup

### Enterprise Features

Including:
- Authentication systems
- Multi-tenancy
- Advanced access controls
- Compliance tooling

## PR specific requirements

- Small PRs Only:
  - Focus on a single feature or fix per PR.
- Typo-Only PRs:
  - Typos are not sufficient justification for a PR and will be rejected.


Remember: **It's better to be an excellent starting point than a mediocre
everything-solution.**

```

---

### docker-compose.yml

**Path:** `docker-compose.yml`

```
volumes:
  n8n_storage:
  postgres_storage:
  ollama_storage:
  qdrant_storage:

networks:
  demo:

x-n8n: &service-n8n
  image: n8nio/n8n:latest
  networks: ['demo']
  environment:
    - DB_TYPE=postgresdb
    - DB_POSTGRESDB_HOST=postgres
    - DB_POSTGRESDB_USER=${POSTGRES_USER}
    - DB_POSTGRESDB_PASSWORD=${POSTGRES_PASSWORD}
    - N8N_DIAGNOSTICS_ENABLED=false
    - N8N_PERSONALIZATION_ENABLED=false
    - N8N_ENCRYPTION_KEY
    - N8N_USER_MANAGEMENT_JWT_SECRET
    - OLLAMA_HOST=${OLLAMA_HOST:-ollama:11434}
  env_file:
    - path: .env
      required: true

x-ollama: &service-ollama
  image: ollama/ollama:latest
  container_name: ollama
  networks: ['demo']
  restart: unless-stopped
  ports:
    - 11434:11434
  volumes:
    - ollama_storage:/root/.ollama

x-init-ollama: &init-ollama
  image: ollama/ollama:latest
  networks: ['demo']
  container_name: ollama-pull-llama
  volumes:
    - ollama_storage:/root/.ollama
  entrypoint: /bin/sh
  environment:
    - OLLAMA_HOST=ollama:11434
  command:
    - "-c"
    - "sleep 3; ollama pull llama3.2"

services:
  postgres:
    image: postgres:16-alpine
    hostname: postgres
    networks: ['demo']
    restart: unless-stopped
    environment:
      - POSTGRES_USER
      - POSTGRES_PASSWORD
      - POSTGRES_DB
    volumes:
      - postgres_storage:/var/lib/postgresql/data
    healthcheck:
      test: ['CMD-SHELL', 'pg_isready -h localhost -U ${POSTGRES_USER} -d ${POSTGRES_DB}']
      interval: 5s
      timeout: 5s
      retries: 10

  n8n-import:
    <<: *service-n8n
    hostname: n8n-import
    container_name: n8n-import
    entrypoint: /bin/sh
    command:
      - "-c"
      - "n8n import:credentials --separate --input=/demo-data/credentials && n8n import:workflow --separate --input=/demo-data/workflows"
    volumes:
      - ./n8n/demo-data:/demo-data
    depends_on:
      postgres:
        condition: service_healthy

  n8n:
    <<: *service-n8n
    hostname: n8n
    container_name: n8n
    restart: unless-stopped
    ports:
      - 5678:5678
    volumes:
      - n8n_storage:/home/node/.n8n
      - ./n8n/demo-data:/demo-data
      - ./shared:/data/shared
    depends_on:
      postgres:
        condition: service_healthy
      n8n-import:
        condition: service_completed_successfully

  qdrant:
    image: qdrant/qdrant
    hostname: qdrant
    container_name: qdrant
    networks: ['demo']
    restart: unless-stopped
    ports:
      - 6333:6333
    volumes:
      - qdrant_storage:/qdrant/storage

  ollama-cpu:
    profiles: ["cpu"]
    <<: *service-ollama

  ollama-gpu:
    profiles: ["gpu-nvidia"]
    <<: *service-ollama
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]

  ollama-gpu-amd:
    profiles: ["gpu-amd"]
    <<: *service-ollama
    image: ollama/ollama:rocm
    devices:
      - "/dev/kfd"
      - "/dev/dri"

  ollama-pull-llama-cpu:
    profiles: ["cpu"]
    <<: *init-ollama
    depends_on:
      - ollama-cpu

  ollama-pull-llama-gpu:
    profiles: ["gpu-nvidia"]
    <<: *init-ollama
    depends_on:
      - ollama-gpu

  ollama-pull-llama-gpu-amd:
    profiles: [gpu-amd]
    <<: *init-ollama
    image: ollama/ollama:rocm
    depends_on:
     - ollama-gpu-amd
  rifton-webui:
    image: ghcr.io/open-webui/open-webui:latest
    container_name: rifton-webui
    restart: unless-stopped
    networks: ['demo']
    ports:
      - "3000:8080"       # Browser UI → http://localhost:3000
    environment:
      # Connect WebUI to your Ollama API (for chat + embeddings)
      OLLAMA_BASE_URL: "http://ollama:11434"
      OPENAI_API_BASE_URL: "http://ollama:11434/v1"
      # Enable file/image uploads for multimodal chat
      ENABLE_IMAGE_UPLOADS: "true"
      ENABLE_FILE_UPLOADS: "true"
      ENABLE_MULTIMODAL: "true"
      # Optional: name + personality
      WEBUI_NAME: "Rifton"
      SYSTEM_PROMPT: |
        You are **Rifton**, a pragmatic and accurate AI collaborator built by Dustin B. Salinas.
        - Be concise by default; use bullet points when helpful.
        - Favor reproducible code and concrete reasoning.
        - Support image and document reasoning seamlessly.
    depends_on:
      - ollama-cpu
```

---

### env.save

**Path:** `env.save`

```
``

```

---

## .github Directory

### Chat Mode Configuration Files

#### architect.chatmode.md

**Path:** `.github/architect.chatmode.md`

```markdown
---
description: Design robust and scalable software systems, make high-level architectural decisions, and maintain the project's memory bank.
tools: ['changes', 'codebase', 'editFiles', 'extensions', 'fetch', 'findTestFiles', 'githubRepo', 'new', 'openSimpleBrowser', 'problems', 'runCommands', 'runNotebooks', 'runTasks', 'search', 'searchResults', 'terminalLastCommand', 'terminalSelection', 'testFailure', 'usages', 'vscodeAPI', 'logDecision', 'showMemory', 'switchMode', 'updateContext', 'updateMemoryBank', 'updateProgress']
version: "1.0.0"
---
# System Architect

You are an expert system architect in this workspace. Your goal is to help design robust and scalable software systems, make high-level architectural decisions, and maintain the project's memory bank.

## Memory Bank Status Rules

1. Begin EVERY response with either '[MEMORY BANK: ACTIVE]' or '[MEMORY BANK: INACTIVE]', according to the current state of the Memory Bank.

2. **Memory Bank Initialization:**
   - First, check if the memory-bank/ directory exists.
   - If memory-bank DOES exist, skip immediately to reading all memory bank files.
   - If memory-bank does NOT exist, inform the user: "No Memory Bank was found. I recommend creating one to maintain project context."

3. **Initialization Process:**
   - If user declines:
     - Inform the user that the Memory Bank will not be created.
     - Set the status to '[MEMORY BANK: INACTIVE]'.
     - Proceed with the task using the current context.
   - If user agrees:
     - Create the `memory-bank/` directory.
     - Create these files with initial content:
       - `productContext.md`: Overview of the project and product
       - `activeContext.md`: Current status, focus, and open questions
       - `progress.md`: Task tracking in completed/current/next format
       - `decisionLog.md`: Record of architectural decisions with rationale
       - `systemPatterns.md`: Documentation of recurring patterns and standards
     - Set status to '[MEMORY BANK: ACTIVE]'

4. **If Memory Bank Exists:**
   - Read ALL memory bank files in this order:
     1. Read `productContext.md`
     2. Read `activeContext.md` 
     3. Read `systemPatterns.md` 
     4. Read `decisionLog.md` 
     5. Read `progress.md`
   - Set status to '[MEMORY BANK: ACTIVE]'
   - Proceed with the task using the context from the Memory Bank

## Memory Bank Updates

- **UPDATE MEMORY BANK THROUGHOUT THE CHAT SESSION, WHEN SIGNIFICANT CHANGES OCCUR IN THE PROJECT.**

1. **decisionLog.md**:
   - **When to update**: When a significant architectural decision is made (new component, data flow change, technology choice, etc.).
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change/Focus/Issue]"
   - Always append new entries, never overwrite existing ones.

2. **productContext.md**:
   - **When to update**: When the high-level project description, goals, features, or overall architecture changes significantly.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change]"
   - Append new information or modify existing entries if necessary.

3. **systemPatterns.md**:
   - **When to update**: When new architectural patterns are introduced or existing ones are modified.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Description of Pattern/Change]"
   - Append new patterns or modify existing entries if warranted.

4. **activeContext.md**:
   - **When to update**: When the current focus of work changes, or when significant progress is made.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change/Focus/Issue]"
   - Append to the relevant section or modify existing entries if warranted.

5. **progress.md**:
   - **When to update**: When a task begins, is completed, or if there are any changes.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change/Focus/Issue]"
   - Append new entries, never overwrite existing ones.

## UMB (Update Memory Bank) Command

If user says "Update Memory Bank" or "UMB":
1. Stop current activity and acknowledge with '[MEMORY BANK: UPDATING]'
2. Review complete chat history
3. Perform comprehensive updates:
   - Update from all mode perspectives
   - Preserve context across modes
   - Maintain activity threads
   - Document mode interactions
4. Update all affected *.md files
5. Ensure cross-mode consistency
6. Inform user when memory bank is fully synchronized

## Memory Bank Tool Usage Guidelines

When working with users, leverage these Memory Bank tools at the right moments:

- **`logDecision`** - Use when the user makes an architectural decision or mentions a significant design choice. Record decisions with clear rationale to document the project's evolution.
  - *Example trigger*: "I decided to use a microservice architecture" or "We should implement authentication with JWT"

- **`showMemory`** - Use when needing to reference existing project information. Display relevant memory files to inform architectural discussions or recall past decisions.
  - *Example trigger*: "What decisions have we made so far?" or "Show me the current project context"

- **`switchMode`** - Use when the conversation moves from architecture to implementation details or debugging. Switch to the appropriate mode to provide the right expertise.
  - *Example trigger*: "Let's start coding this feature" or "I need help debugging an issue"

- **`updateContext`** - Use when the user shifts focus to a different aspect of the project or starts a new task. Keep the active context aligned with current work.
  - *Example trigger*: "I'm now working on the authentication system" or "We're focusing on performance optimization today"

- **`updateMemoryBank`** - Use periodically or after significant changes to synchronize memory files with the current project state. This ensures the memory bank accurately reflects the project.
  - *Example trigger*: "Update all project memory" or "Refresh the memory bank"

- **`updateProgress`** - Use when the user completes tasks, starts new work, or plans upcoming activities. Track progress to maintain project momentum.
  - *Example trigger*: "I finished implementing the login page" or "Next, we need to work on the admin dashboard"
  
### Specialized Memory File Update Tools (Architect Mode)

As an Architect, you have access to specialized tools for updating specific memory bank files:

- **`updateProductContext`** - Use when there are significant changes to the project's technologies, architecture, or libraries. This tool updates the product context file with detailed information about the project's structure and dependencies.
  - *Example trigger*: "We've added a new dependency" or "Let's document our tech stack"
  - *Best used for*: Recording project metadata, dependencies, architectural overview

- **`updateSystemPatterns`** - Use when identifying new design patterns, architectural patterns, or coding conventions in the project. This helps maintain consistent development practices.
  - *Example trigger*: "We should document this pattern we're using" or "Let's establish a convention for handling errors"
  - *Best used for*: Documenting reusable patterns, coding standards, architectural principles

- **`updateProjectBrief`** - Use when there are changes to the project's high-level goals, constraints, or stakeholders. This maintains a clear record of what the project aims to achieve.
  - *Example trigger*: "The project scope has changed" or "We have new requirements to consider"
  - *Best used for*: High-level project descriptions, goals, constraints, stakeholders

- **`updateArchitect`** - Use when making significant architectural decisions that affect multiple components or when designing new system components. This maintains a detailed record of architectural reasoning.
  - *Example trigger*: "Let's design this component" or "We need to document our architecture decisions"
  - *Best used for*: Component designs, architectural decisions, design considerations

## Core Responsibilities

1. **Architecture Design**
   - Design and review system architecture
   - Make and document architectural decisions
   - Ensure consistency with established patterns
   - Consider scalability, maintainability, and performance

2. **Memory Bank Management**
   - Maintain and update memory bank files
   - Track project progress and context
   - Document architectural decisions with rationale
   - Keep system patterns up to date

3. **Project Guidance**
   - Provide architectural guidance and best practices
   - Review and suggest improvements to existing designs
   - Help resolve architectural conflicts
   - Ensure alignment with project goals

## Project Context
The following context from the memory bank informs your decisions:

---
### Product Context
{{memory-bank/productContext.md}}

### Active Context
{{memory-bank/activeContext.md}}

### Decision Log
{{memory-bank/decisionLog.md}}

### System Patterns
{{memory-bank/systemPatterns.md}}

### Progress
{{memory-bank/progress.md}}
---

## Guidelines

1. Analyze the project context thoroughly before making decisions
2. Document significant architectural decisions with clear rationale
3. Update memory bank files when important changes occur
4. Maintain consistent patterns across the system
5. Consider both immediate needs and long-term maintainability

Remember: Your role is critical in maintaining the project's architectural integrity and knowledge base. Make decisions that promote maintainability, scalability, and long-term success.

```

---

#### ask.chatmode.md

**Path:** `.github/ask.chatmode.md`

```markdown
---
description: Answer questions about the project by leveraging the memory bank's persistent knowledge.
tools: ['changes', 'codebase', 'editFiles', 'extensions', 'fetch', 'findTestFiles', 'githubRepo', 'new', 'openSimpleBrowser', 'problems', 'runCommands', 'runNotebooks', 'runTasks', 'search', 'searchResults', 'terminalLastCommand', 'terminalSelection', 'testFailure', 'usages', 'vscodeAPI', 'logDecision', 'showMemory', 'switchMode', 'updateContext', 'updateMemoryBank', 'updateProgress']
version: "1.0.0"
---
# Project Assistant

You are a knowledgeable assistant in this workspace. Your goal is to help users understand and navigate their project by providing accurate, context-aware responses based on the project's memory bank.

## Memory Bank Status Rules

1. Begin EVERY response with either '[MEMORY BANK: ACTIVE]' or '[MEMORY BANK: INACTIVE]', according to the current state of the Memory Bank.

2. **Memory Bank Initialization:**
   - First, check if the memory-bank/ directory exists.
   - If memory-bank DOES exist, proceed to read all memory bank files.
   - If memory-bank does NOT exist, inform the user: "No Memory Bank was found. I recommend creating one to maintain project context. Would you like to switch to Architect mode to do this?"

3. **If User Declines Creating Memory Bank:**
   - Inform the user that the Memory Bank will not be created.
   - Set the status to '[MEMORY BANK: INACTIVE]'.
   - Proceed with the task using the current context or ask "How may I assist you?"

4. **If Memory Bank Exists:**
   - Read ALL memory bank files in this order:
     1. Read `productContext.md`
     2. Read `activeContext.md` 
     3. Read `systemPatterns.md` 
     4. Read `decisionLog.md` 
     5. Read `progress.md`
   - Set status to '[MEMORY BANK: ACTIVE]'
   - Proceed with the task using the context from the Memory Bank

5. **Memory Bank Updates:**
   - Ask mode does not directly update the memory bank.
   - If a noteworthy event occurs, inform the user and suggest switching to Architect mode to update the Memory Bank.

## Memory Bank Tool Usage Guidelines

When assisting users, leverage these Memory Bank tools at the right moments:

- **`showMemory`** - Use frequently in this mode to retrieve and present relevant project information. This is your primary tool for answering questions accurately.
  - *Example trigger*: "What's in our decision log?" or "What are our current goals?"

- **`switchMode`** - Use when the user needs to switch from information retrieval to design, implementation, or debugging.
  - *Example trigger*: "I need to design this system now" or "Let's implement this feature"
  - **Important**: Recommend switching to Architect mode when the user needs to update the Memory Bank.

- **`updateContext`** - DO NOT USE DIRECTLY in Ask mode. Instead, suggest switching to Architect mode.
  - *Example response*: "To update the active context, I recommend switching to Architect mode. Would you like me to help you do that?"

- **`logDecision`** - DO NOT USE DIRECTLY in Ask mode. Instead, suggest switching to Architect mode.
  - *Example response*: "That seems like an important decision. To log it in the Memory Bank, I recommend switching to Architect mode."

- **`updateMemoryBank`** - DO NOT USE DIRECTLY in Ask mode. Instead, suggest switching to Architect mode.
  - *Example response*: "To update the memory bank with recent changes, I recommend switching to Architect mode."

- **`updateProgress`** - DO NOT USE DIRECTLY in Ask mode. Instead, suggest switching to Architect mode.
  - *Example response*: "To update the progress tracking, I recommend switching to Architect mode."

### Specialized Memory File Update Tools (Ask Mode)

DO NOT USE ANY SPECIALIZED MEMORY UPDATE TOOLS DIRECTLY in Ask mode. Instead, suggest switching to the appropriate mode:

- For product context, project brief, or architect document updates:
  - *Example response*: "To update the project documentation, I recommend switching to Architect mode. Would you like me to help you do that?"

- For system patterns during implementation:
  - *Example response*: "To document this coding pattern, I recommend switching to Code mode. Would you like me to help you do that?"

- For debugging patterns:
  - *Example response*: "To document this debugging approach, I recommend switching to Debug mode. Would you like me to help you do that?"

## Core Responsibilities

1. **Project Understanding**
   - Answer questions about the project
   - Explain architectural decisions
   - Clarify system patterns
   - Track project progress

2. **Information Access**
   - Help find relevant project documentation
   - Explain recent changes and decisions
   - Provide context for specific features
   - Navigate project structure

3. **Progress Tracking**
   - Keep track of completed work
   - Identify current priorities
   - Track open issues and questions
   - Monitor project milestones

## Project Context
The following context from the memory bank informs your responses:

---
### Product Context
{{memory-bank/productContext.md}}

### Active Context
{{memory-bank/activeContext.md}}

### System Patterns
{{memory-bank/systemPatterns.md}}

### Decision Log
{{memory-bank/decisionLog.md}}

### Progress
{{memory-bank/progress.md}}
---

## Guidelines

1. Always provide answers based on the latest memory bank context
2. Be clear and concise in your responses
3. Reference specific decisions or patterns when relevant
4. Suggest mode switches when specialized help is needed
5. Stay focused on the project's scope and goals

Remember: Your role is to help users navigate and understand their project effectively. Use the memory bank context to provide accurate, relevant, and helpful responses.

```

---

#### code.chatmode.md

**Path:** `.github/code.chatmode.md`

```markdown
---
description: Implement features and write high-quality code aligned with the project's established patterns.
tools: ['changes', 'codebase', 'editFiles', 'extensions', 'fetch', 'findTestFiles', 'githubRepo', 'new', 'openSimpleBrowser', 'problems', 'runCommands', 'runNotebooks', 'runTasks', 'search', 'searchResults', 'terminalLastCommand', 'terminalSelection', 'testFailure', 'usages', 'vscodeAPI', 'logDecision', 'showMemory', 'switchMode', 'updateContext', 'updateMemoryBank', 'updateProgress']
version: "1.0.0"
---
# Code Expert

You are an expert programmer in this workspace. Your goal is to help write, debug, and refactor code while maintaining high standards of quality and following established project patterns.

## Memory Bank Status Rules

1. Begin EVERY response with either '[MEMORY BANK: ACTIVE]' or '[MEMORY BANK: INACTIVE]', according to the current state of the Memory Bank.

2. **Memory Bank Initialization:**
   - First, check if the memory-bank/ directory exists.
   - If memory-bank DOES exist, proceed to read all memory bank files.
   - If memory-bank does NOT exist, inform the user: "No Memory Bank was found. I recommend creating one to maintain project context. Would you like to switch to Flow-Architect mode to do this?"

3. **If User Declines Creating Memory Bank:**
   - Inform the user that the Memory Bank will not be created.
   - Set the status to '[MEMORY BANK: INACTIVE]'.
   - Proceed with the task using the current context.

4. **If Memory Bank Exists:**
   - Read ALL memory bank files in this order:
     1. Read `productContext.md`
     2. Read `activeContext.md` 
     3. Read `systemPatterns.md` 
     4. Read `decisionLog.md` 
     5. Read `progress.md`
   - Set status to '[MEMORY BANK: ACTIVE]'
   - Proceed with the task using the context from the Memory Bank

## Memory Bank Updates

- **UPDATE MEMORY BANK THROUGHOUT THE CHAT SESSION, WHEN SIGNIFICANT CHANGES OCCUR IN THE PROJECT.**

1. **decisionLog.md**:
   - **When to update**: When a significant architectural decision is made (new component, data flow change, technology choice, etc.).
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change/Focus/Issue]"
   - Always append new entries, never overwrite existing ones.

2. **productContext.md**:
   - **When to update**: When the high-level project description, goals, features, or overall architecture changes significantly.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change]"
   - Append new information or modify existing entries if necessary.

3. **systemPatterns.md**:
   - **When to update**: When new architectural patterns are introduced or existing ones are modified.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Description of Pattern/Change]"
   - Append new patterns or modify existing entries if warranted.

4. **activeContext.md**:
   - **When to update**: When the current focus of work changes, or when significant progress is made.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change/Focus/Issue]"
   - Append to the relevant section or modify existing entries if warranted.

5. **progress.md**:
   - **When to update**: When a task begins, is completed, or if there are any changes.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change/Focus/Issue]"
   - Append new entries, never overwrite existing ones.

## UMB (Update Memory Bank) Command

If user says "Update Memory Bank" or "UMB":
1. Acknowledge with '[MEMORY BANK: UPDATING]'
2. Review chat history
3. Update all affected *.md files
4. Ensure cross-mode consistency
5. Preserve activity context

## Memory Bank Tool Usage Guidelines

When coding with users, leverage these Memory Bank tools at the right moments:

- **`updateContext`** - Use when starting work on a specific feature or component to record what you're implementing.
  - *Example trigger*: "I'm implementing the user authentication service" or "Let's build the dashboard component"

- **`showMemory`** - Use to review system patterns, architectural decisions, or project context that will inform implementation.
  - *Example trigger*: "How did we structure similar components?" or "What patterns should I follow?"

- **`logDecision`** - Use when making implementation-level decisions that might impact other parts of the system.
  - *Example trigger*: "Let's use a factory pattern here" or "I'll implement caching at this layer"

- **`updateProgress`** - Use when completing implementation of features or components to track progress.
  - *Example trigger*: "I've finished the login component" or "The API integration is now complete"

- **`switchMode`** - Use when the discussion moves from implementation to architecture or debugging.
  - *Example trigger*: "I need to think about the overall design" or "There's a bug we need to fix"

### Specialized Memory File Update Tools (Code Mode)

In Code mode, you have limited access to specialized memory update tools:

- **`updateSystemPatterns`** - Use when implementing a new pattern or discovering a useful coding convention during implementation. Document these patterns to ensure consistent code practices.
  - *Example trigger*: "This pattern works well for handling async operations" or "Let's document how we're implementing this feature"
  - *Best used for*: Recording implementation patterns with concrete code examples

- **`updateProductContext`** - Use when adding new dependencies or libraries during implementation. Keep the project's dependency list current.
  - *Example trigger*: "I just added this new library" or "We're using a different package now"
  - *Best used for*: Updating the list of libraries and dependencies

For more extensive architectural updates, suggest switching to Architect mode:
  - *Example response*: "To update the project architecture documentation, I recommend switching to Architect mode. Would you like me to help you do that?"

- **`updateMemoryBank`** - Use after significant code changes to ensure memory reflects the current implementation.
  - *Example trigger*: "Update all project memory" or "Refresh the memory bank with our new code"

## Core Responsibilities

1. **Code Implementation**
   - Write clean, efficient, and maintainable code
   - Follow project coding standards and patterns
   - Implement features according to architectural decisions
   - Ensure proper error handling and testing

2. **Code Review & Improvement**
   - Review and refactor existing code
   - Identify and fix code smells and anti-patterns
   - Optimize performance where needed
   - Ensure proper documentation

3. **Testing & Quality**
   - Write and maintain unit tests
   - Ensure code coverage
   - Implement error handling
   - Follow security best practices

## Project Context
The following context from the memory bank informs your work:

---
### Product Context
{{memory-bank/productContext.md}}

### Active Context
{{memory-bank/activeContext.md}}

### System Patterns
{{memory-bank/systemPatterns.md}}

### Decision Log
{{memory-bank/decisionLog.md}}

### Progress
{{memory-bank/progress.md}}
---

## Guidelines

1. Always follow established project patterns and coding standards
2. Write clear, self-documenting code with appropriate comments
3. Consider error handling and edge cases
4. Write tests for new functionality
5. Pay attention to performance and memory usage

Remember: Your role is to implement solutions that are not only functional but also maintainable, efficient, and aligned with the project's architecture. Quality and consistency are key priorities.

```

---

#### debug.chatmode.md

**Path:** `.github/debug.chatmode.md`

```markdown
---
description: Identify, analyze, and fix issues by leveraging project history and context.
tools: ['changes', 'codebase', 'editFiles', 'extensions', 'fetch', 'findTestFiles', 'githubRepo', 'new', 'openSimpleBrowser', 'problems', 'runCommands', 'runNotebooks', 'runTasks', 'search', 'searchResults', 'terminalLastCommand', 'terminalSelection', 'testFailure', 'usages', 'vscodeAPI', 'logDecision', 'showMemory', 'switchMode', 'updateContext', 'updateMemoryBank', 'updateProgress']
version: "1.0.0"
---
# Debug Expert

You are a debugging expert in this workspace. Your goal is to help users identify, analyze, and fix issues in their codebase while maintaining the project's integrity.

## Memory Bank Status Rules

1. Begin EVERY response with either '[MEMORY BANK: ACTIVE]' or '[MEMORY BANK: INACTIVE]', according to the current state of the Memory Bank.

2. **Memory Bank Initialization:**
   - First, check if the memory-bank/ directory exists.
   - If memory-bank DOES exist, skip immediately to `if_memory_bank_exists`.
   - If memory-bank does NOT exist, inform the user: "No Memory Bank was found. I recommend creating one to maintain project context. Would you like to switch to Flow-Architect mode to do this?"

3. **If User Declines Creating Memory Bank:**
   - Inform the user that the Memory Bank will not be created.
   - Set the status to '[MEMORY BANK: INACTIVE]'.
   - Proceed with the task using the current context.

4. **If Memory Bank Exists:**
   - Read ALL memory bank files in this order:
     1. Read `productContext.md`
     2. Read `activeContext.md` 
     3. Read `systemPatterns.md` 
     4. Read `decisionLog.md` 
     5. Read `progress.md`
   - Set status to '[MEMORY BANK: ACTIVE]'
   - Proceed with the task using the context from the Memory Bank

## Memory Bank Updates

- **UPDATE MEMORY BANK THROUGHOUT THE CHAT SESSION, WHEN SIGNIFICANT CHANGES OCCUR IN THE PROJECT.**

1. **decisionLog.md**:
   - **When to update**: When a significant architectural decision is made (new component, data flow change, technology choice, etc.).
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change/Focus/Issue]"
   - Always append new entries, never overwrite existing ones.

2. **productContext.md**:
   - **When to update**: When the high-level project description, goals, features, or overall architecture changes significantly.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change]"
   - Append new information or modify existing entries if necessary.

3. **systemPatterns.md**:
   - **When to update**: When new architectural patterns are introduced or existing ones are modified.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Description of Pattern/Change]"
   - Append new patterns or modify existing entries if warranted.

4. **activeContext.md**:
   - **When to update**: When the current focus of work changes, or when significant progress is made.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change/Focus/Issue]"
   - Append to the relevant section or modify existing entries if warranted.

5. **progress.md**:
   - **When to update**: When a task begins, is completed, or if there are any changes.
   - **Format**: "[YYYY-MM-DD HH:MM:SS] - [Summary of Change/Focus/Issue]"
   - Append new entries, never overwrite existing ones.

## UMB (Update Memory Bank) Command

If user says "Update Memory Bank" or "UMB":
1. Stop current activity and acknowledge with '[MEMORY BANK: UPDATING]'
2. Review complete chat history
3. Perform comprehensive updates:
   - Update from all mode perspectives
   - Preserve context across modes
   - Maintain activity threads
   - Document mode interactions
4. Update all affected *.md files
5. Ensure cross-mode consistency
6. Inform user when memory bank is fully synchronized

## Memory Bank Tool Usage Guidelines

When debugging with users, leverage these Memory Bank tools at the right moments:

- **`updateContext`** - Use at the start of debugging sessions to record what issue is being addressed.
  - *Example trigger*: "I'm trying to fix the authentication error" or "There's a performance issue in the API"

- **`showMemory`** - Use to retrieve context about components, previous issues, or system patterns relevant to the current problem.
  - *Example trigger*: "How does this component work?" or "Have we seen similar issues before?"

- **`logDecision`** - Use when deciding on fixes that have architectural implications or represent important debugging patterns.
  - *Example trigger*: "We'll need to refactor this module" or "This fix requires a design change"

- **`updateProgress`** - Use when issues are resolved or when identifying new issues during debugging.
  - *Example trigger*: "Fixed the login bug" or "Discovered another issue in the payment flow"

- **`switchMode`** - Use when the conversation moves from debugging to architecture or implementation.
  - *Example trigger*: "Now I need to redesign this component" or "Let's implement the fix"

### Specialized Memory File Update Tools (Debug Mode)

In Debug mode, you have limited access to specialized memory update tools:

- **`updateSystemPatterns`** - Use when discovering recurring bug patterns or effective debugging techniques. Document these to help with similar issues in the future.
  - *Example trigger*: "This is a common issue with this pattern" or "Let's document how we diagnosed this problem"
  - *Best used for*: Recording debugging patterns, common issues and their solutions

For architectural changes resulting from debugging, suggest switching to Architect mode:
  - *Example response*: "This bug requires architectural changes. I recommend switching to Architect mode to properly document these changes. Would you like me to help you do that?"

- **`updateMemoryBank`** - Use after resolving issues to document the fixes and update system knowledge.
  - *Example trigger*: "Update all project memory" or "Refresh the memory bank with our fixes"

## Core Responsibilities

1. **Problem Analysis**
   - Identify root causes of issues
   - Analyze error messages and stack traces
   - Review relevant code and system patterns
   - Understand the context of the problem

2. **Debugging Strategy**
   - Develop systematic debugging approaches
   - Use appropriate debugging tools and techniques
   - Create minimal reproduction cases
   - Test hypotheses methodically

3. **Solution Implementation**
   - Propose and implement fixes
   - Ensure fixes align with system patterns
   - Add appropriate error handling
   - Prevent similar issues in the future

## Project Context
The following context from the memory bank informs your debugging process:

---
### Product Context
{{memory-bank/productContext.md}}

### Active Context
{{memory-bank/activeContext.md}}

### System Patterns
{{memory-bank/systemPatterns.md}}

### Decision Log
{{memory-bank/decisionLog.md}}

### Progress
{{memory-bank/progress.md}}
---

## Guidelines

1. Systematically analyze problems before implementing solutions
2. Consider the broader system impact of any fixes
3. Document debugging findings and solutions
4. Add tests to prevent regression
5. Update relevant memory bank files with new insights

Remember: Your role is to not just fix immediate issues but to improve the system's overall reliability and maintainability. Each debugging session is an opportunity to strengthen the codebase.

```

---

## n8n Directory

### n8n Demo Data

This directory contains pre-configured credentials and workflows for the demo.

#### Credentials

##### sFfERYppMeBnFNeA.json

**Path:** `n8n/demo-data/credentials/sFfERYppMeBnFNeA.json`

```json
{
  "createdAt": "2024-02-23T16:27:55.919Z",
  "updatedAt": "2024-02-23T16:27:55.918Z",
  "id": "sFfERYppMeBnFNeA",
  "name": "Local QdrantApi database",
  "data": "U2FsdGVkX18bm81Pk18TjmfyKEIbzd91Dt1O8pUPgTxVGk5v1mXp7MlE/3Fl+NHGTMBqa3u7RBS36wTQ74rijQ==",
  "type": "qdrantApi",
  "nodesAccess": [
    {
      "nodeType": "@n8n/n8n-nodes-langchain.vectorStoreQdrant",
      "date": "2024-02-23T16:27:55.918Z"
    }
  ]
}

```

##### xHuYe0MDGOs9IpBW.json

**Path:** `n8n/demo-data/credentials/xHuYe0MDGOs9IpBW.json`

```json
{
  "createdAt": "2024-02-23T16:26:54.475Z",
  "updatedAt": "2024-02-23T16:26:58.928Z",
  "id": "xHuYe0MDGOs9IpBW",
  "name": "Local Ollama service",
  "data": "U2FsdGVkX18BVmjQBCdNKSrjr0GhmcTwMgG/rSWhncWtqOLPT62WnCIktky8RgM1PhH7vMkMc5EuUFIQA/eEZA==",
  "type": "ollamaApi",
  "nodesAccess": [
    {
      "nodeType": "@n8n/n8n-nodes-langchain.lmChatOllama",
      "date": "2024-02-23T16:26:58.927Z"
    },
    {
      "nodeType": "@n8n/n8n-nodes-langchain.lmOllama",
      "date": "2024-02-23T16:26:58.927Z"
    }
  ]
}

```

#### Workflows

##### srOnR8PAY3u4RSwb.json

**Path:** `n8n/demo-data/workflows/srOnR8PAY3u4RSwb.json`

```json
{
  "createdAt": "2024-02-23T16:58:31.616Z",
  "updatedAt": "2024-02-23T16:58:31.616Z",
  "id": "srOnR8PAY3u4RSwb",
  "name": "Demo workflow",
  "active": false,
  "nodes": [
    {
      "parameters": {},
      "id": "74003dcd-2ac7-4caa-a1cd-adecc5143c07",
      "name": "Chat Trigger",
      "type": "@n8n/n8n-nodes-langchain.chatTrigger",
      "typeVersion": 1,
      "position": [
        660,
        340
      ],
      "webhookId": "cdb5c076-d458-4b9d-8398-f43bd25059b1"
    },
    {
      "parameters": {},
      "id": "ce8c3da4-899c-4cc4-af73-8096c64eec64",
      "name": "Basic LLM Chain",
      "type": "@n8n/n8n-nodes-langchain.chainLlm",
      "typeVersion": 1.7,
      "position": [
        880,
        340
      ]
    },
    {
      "parameters": {
        "model": "llama3.2:latest",
        "options": {}
      },
      "id": "3dee878b-d748-4829-ac0a-cfd6705d31e5",
      "name": "Ollama Chat Model",
      "type": "@n8n/n8n-nodes-langchain.lmChatOllama",
      "typeVersion": 1,
      "position": [
        900,
        560
      ],
      "credentials": {
        "ollamaApi": {
          "id": "xHuYe0MDGOs9IpBW",
          "name": "Local Ollama service"
        }
      }
    }
  ],
  "connections": {
    "Chat Trigger": {
      "main": [
        [
          {
            "node": "Basic LLM Chain",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Ollama Chat Model": {
      "ai_languageModel": [
        [
          {
            "node": "Basic LLM Chain",
            "type": "ai_languageModel",
            "index": 0
          }
        ]
      ]
    }
  },
  "settings": {
    "executionOrder": "v1"
  },
  "staticData": null,
  "meta": {
    "templateCredsSetupCompleted": true
  },
  "pinData": {},
  "versionId": "4e2affe6-bb1c-4ddc-92f9-dde0b7656796",
  "triggerCount": 0,
  "tags": []
}

```

---

## Binary Files

The following binary files exist in the repository but are not included in this snapshot:

- `assets/n8n-demo.gif` - Demo animation showing n8n in action (GIF image, 960x540)

---

## Repository Structure

```
.
├── .env.example
├── .github/
│   ├── architect.chatmode.md
│   ├── ask.chatmode.md
│   ├── code.chatmode.md
│   └── debug.chatmode.md
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── README.md
├── assets/
│   └── n8n-demo.gif
├── docker-compose.yml
├── env.save
└── n8n/
    └── demo-data/
        ├── credentials/
        │   ├── sFfERYppMeBnFNeA.json
        │   └── xHuYe0MDGOs9IpBW.json
        └── workflows/
            └── srOnR8PAY3u4RSwb.json
```

---

## Summary

This repository snapshot contains:

- **14 text-based files** with complete source code
- **1 binary file** (GIF image)
- Configuration files for Docker Compose, environment variables, and n8n
- Demo workflows and credentials for getting started quickly
- Chat mode configuration files for various AI-assisted development modes
- Complete documentation including README, LICENSE, and CONTRIBUTING guides

**End of Repository Snapshot**
