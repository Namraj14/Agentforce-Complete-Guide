# Steps to Set Up Agentforce Vibes

## Overview

Before using Agentforce Vibes, you need to configure your Salesforce org and development environment.

There are **two ways** to use Agentforce Vibes:

1. **Agentforce Vibes IDE (Browser-Based)**
2. **Agentforce Vibes VS Code Extension**

The setup differs slightly for each.

---

# Option 1: Agentforce Vibes IDE (Browser-Based)

## Prerequisites

- Supported Salesforce Edition
  - Developer Edition
  - Enterprise Edition
  - Unlimited Edition
  - Performance Edition
  - Partner Developer Edition
- Sandbox or supported development environment
- System Administrator access (for initial org setup)
- View All Data permission (for users accessing the IDE)
- API access enabled for the org (required in supported editions) :contentReference[oaicite:0]{index=0}

---

# Step 1: Login to Salesforce

Login to your Salesforce Org.

```
https://login.salesforce.com
```

or

```
https://test.salesforce.com
```

---

# Step 2: Open Setup

```
Setup
```

↓

Search

```
Agentforce Vibes
```

---

# Step 3: Enable Agentforce Vibes

Open

```
Setup

↓

Agentforce Vibes
```

If prompted,

✔ Accept the Terms & Conditions.

This enables Agentforce Vibes for your organization. :contentReference[oaicite:1]{index=1}

---

# Step 4: Launch Agentforce Vibes IDE

Click

```
Launch Agentforce Vibes
```

The browser-based IDE opens.

It is essentially a cloud-hosted version of VS Code.

---

# Step 5: Wait for Initialization

During the first launch,

Salesforce automatically prepares:

- Salesforce CLI
- Development Environment
- Project Workspace
- Authentication

This may take a few minutes. :contentReference[oaicite:2]{index=2}

---

# Step 6: Start Building

Once initialization completes,

the IDE is ready.

You can now:

- Create Apex Classes
- Create LWCs
- Build Flows
- Generate Agents
- Deploy Metadata

---

# Browser IDE Setup Flow

```text
Login

↓

Setup

↓

Search "Agentforce Vibes"

↓

Accept Terms

↓

Launch IDE

↓

Initialize Environment

↓

Start Building
```

---

# Option 2: Agentforce Vibes VS Code Extension

## Prerequisites

Install:

- Visual Studio Code
- Salesforce CLI (`sf`)
- Salesforce Extension Pack
- Git (recommended for source control)
- Windows users: Microsoft Visual C++ Redistributable (if required) :contentReference[oaicite:3]{index=3}

---

# Step 1: Install VS Code

Download and install

Visual Studio Code.

---

# Step 2: Install Salesforce CLI

Install the Salesforce CLI.

Verify installation:

```bash
sf --version
```

---

# Step 3: Install Salesforce Extension Pack

Open VS Code

↓

Extensions

↓

Search

```
Salesforce Extension Pack
```

↓

Install

---

# Step 4: Install Agentforce Vibes Extension

Open Extensions

↓

Search

```
Agentforce Vibes
```

↓

Install

---

# Step 5: Create an SFDX Project

Open Command Palette

```
Ctrl + Shift + P
```

Run:

```
SFDX: Create Project
```

This creates a project containing:

```
sfdx-project.json
```

Agentforce Vibes requires a valid SFDX project. :contentReference[oaicite:4]{index=4}

---

# Step 6: Authorize Your Salesforce Org

Authenticate using the Salesforce CLI.

Example:

```bash
sf org login web
```

Choose:

- Production
- Sandbox
- Developer Org

Log in successfully.

---

# Step 7: Complete the Setup Checklist

When Agentforce Vibes starts, it verifies:

✔ Salesforce CLI installed

✔ Salesforce Extension Pack installed

✔ Valid SFDX Project

✔ Connected Salesforce Org

✔ AI Provider configured (when applicable)

When all items show **Ready**, setup is complete. :contentReference[oaicite:5]{index=5}

---

# Step 8: Open Agentforce Vibes Chat

Click

```
Agentforce Vibes

↓

Chat
```

Start asking questions like:

```
Generate an Apex Trigger.
```

or

```
Explain this LWC.
```

---

# VS Code Setup Flow

```text
Install VS Code

↓

Install Salesforce CLI

↓

Install Salesforce Extension Pack

↓

Install Agentforce Vibes Extension

↓

Create SFDX Project

↓

Authorize Salesforce Org

↓

Complete Setup Checklist

↓

Start Coding
```

---

# Setup Checklist

| Requirement | Browser IDE | VS Code |
|------------|-------------|---------|
| Salesforce Org | ✅ | ✅ |
| System Admin (initial enablement) | ✅ | ✅ |
| Salesforce CLI | Preinstalled | Required |
| VS Code | ❌ | ✅ |
| Salesforce Extension Pack | Preinstalled | Required |
| Agentforce Vibes Extension | Preinstalled | Required |
| SFDX Project | Auto-created/available | Required |
| Org Authentication | Automatic in IDE | Required |
| AI Chat | ✅ | ✅ |

---

# After Setup, What Can You Do?

You can use Agentforce Vibes to:

- Generate Apex Classes
- Generate Apex Triggers
- Generate Test Classes
- Build Lightning Web Components
- Create Flows
- Explain Existing Code
- Optimize SOQL
- Generate Documentation
- Debug Errors
- Build Agentforce Agents
- Deploy Metadata

---

# Common Setup Issues

## Issue 1

**Agentforce Vibes not visible in Setup**

**Possible Causes**

- Unsupported Salesforce edition
- Feature unavailable in your org
- Org administrator hasn't enabled it

---

## Issue 2

**Salesforce CLI not detected**

**Solution**

Update or reinstall the latest Salesforce CLI.

---

## Issue 3

**No SFDX Project Found**

**Solution**

Run:

```
SFDX: Create Project
```

---

## Issue 4

**No Connected Org**

**Solution**

Authenticate your org using:

```bash
sf org login web
```

---

## Issue 5

**Checklist Not Completing**

Verify:

- Latest Salesforce CLI
- Latest Salesforce Extension Pack
- Valid `sfdx-project.json`
- Connected Salesforce Org

---

# Interview Questions

## Q1. What are the prerequisites for Agentforce Vibes?

### Answer

Supported Salesforce edition, a properly enabled org, and either the browser-based IDE or a local environment with VS Code, Salesforce CLI, Salesforce Extension Pack, a valid SFDX project, and an authenticated Salesforce org.

---

## Q2. What are the two ways to use Agentforce Vibes?

### Answer

1. Agentforce Vibes IDE (Browser-Based)

2. Agentforce Vibes VS Code Extension

---

## Q3. Why do we need an SFDX Project?

### Answer

Agentforce Vibes uses the Salesforce DX project structure (including `sfdx-project.json`) to understand the project's metadata layout and work with Salesforce source files.

---

## Q4. Why do we authenticate a Salesforce Org?

### Answer

Authentication allows Agentforce Vibes to access metadata, retrieve records, deploy changes, execute Salesforce CLI commands, and interact securely with the connected org.

---

## Q5. What happens after setup?

### Answer

Developers can use natural language to generate Apex, LWC, Flows, SOQL, test classes, documentation, debug code, and build Agentforce solutions.

---

# Memory Trick

Remember:

**"LSECA"**

- **L** → Login
- **S** → Setup Agentforce Vibes
- **E** → Enable / Extension
- **C** → Connect Org
- **A** → Ask AI

---

# Interview One-Liner

> **Setting up Agentforce Vibes involves enabling it in a supported Salesforce org, launching either the browser-based IDE or the VS Code extension, ensuring the required Salesforce development tools are available, connecting a Salesforce org, completing the setup checklist, and then using AI-assisted development for Salesforce projects.**
