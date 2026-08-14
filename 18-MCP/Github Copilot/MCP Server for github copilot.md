# Salesforce DX MCP Server with VS Code & GitHub Copilot

## Overview

The **Salesforce DX MCP Server** allows AI coding assistants such as GitHub Copilot to interact with Salesforce development tools through the **Model Context Protocol (MCP)**.

Instead of manually executing Salesforce CLI commands for common development activities, you can use natural-language prompts in VS Code to perform tasks such as:

* Retrieve Salesforce metadata
* Deploy metadata
* Query Salesforce records
* Run Apex tests
* View authorized Salesforce orgs
* Work with Salesforce users and permissions
* Perform common Salesforce DX development tasks

The basic architecture is:

```text
VS Code
   ↓
GitHub Copilot
   ↓
MCP Client
   ↓
Salesforce DX MCP Server
   ↓
Salesforce CLI / DX Project
   ↓
Salesforce Org
```

Salesforce's DX MCP Server is designed to work with Salesforce orgs that have already been authenticated through the Salesforce CLI.

---

# Prerequisites

Before configuring MCP, make sure the following are installed and configured.

## 1. Node.js

Install the **Active LTS version of Node.js**.

MCP uses `npx` to launch the Salesforce MCP package.

Verify the installation:

```bash
node --version
npm --version
```

---

## 2. Salesforce CLI

Install Salesforce CLI on your machine.

Verify the installation:

```bash
sf --version
```

The Salesforce CLI is important because the local Salesforce DX MCP Server works with the Salesforce orgs that you have authenticated through the CLI.

---

## 3. Visual Studio Code

Install Visual Studio Code.

A Salesforce DX project should be opened as the VS Code workspace.

You can create a new Salesforce DX project using the Salesforce Extensions for VS Code or clone an existing DX project from GitHub.

---

## 4. Salesforce Extension Pack

Install the **Salesforce Extension Pack** in VS Code.

This provides Salesforce development functionality such as:

* Apex development
* LWC development
* Salesforce project support
* Org authorization
* Metadata deployment/retrieval
* Salesforce CLI integration

---

## 5. Salesforce DX Project

You need a Salesforce DX project.

Example project structure:

```text
my-salesforce-project/
│
├── force-app/
│   └── main/
│       └── default/
│           ├── classes/
│           ├── lwc/
│           ├── objects/
│           ├── flows/
│           ├── triggers/
│           └── ...
│
├── manifest/
├── sfdx-project.json
└── .vscode/
```

If the `.vscode` folder doesn't exist, create it.

---

# Step 1 — Authenticate a Salesforce Org

Open the VS Code terminal and run:

```bash
sf org login web
```

A browser window will open.

Log in to the Salesforce org that you want to use.

For example:

* Developer Edition
* Trailhead Playground
* Sandbox
* Scratch Org

After authentication, verify the authorized orgs:

```bash
sf org list
```

You should see your authorized org in the list.

---

# Step 2 — Set the Default Salesforce Org

Choose the org that you want to use as your default target org.

For example:

```bash
sf config set target-org=MySandbox
```

Replace `MySandbox` with your actual org alias.

Verify the configuration:

```bash
sf config get target-org
```

The Salesforce DX MCP Server uses orgs that have already been authenticated through Salesforce CLI.

> **Note:** If you want to create or manage scratch orgs through MCP, you also need an authorized Dev Hub org.

---

# Step 3 — Set Up GitHub Copilot

You need:

* A GitHub account
* Access to GitHub Copilot
* GitHub Copilot extension installed in VS Code

In VS Code:

```text
Extensions
    ↓
Search for "GitHub Copilot"
    ↓
Install GitHub Copilot
    ↓
Sign in with GitHub
```

Open the Copilot Chat/Agent interface after installation.

---

# Step 4 — Create the MCP Configuration File

Inside the root of your Salesforce DX project, create:

```text
.vscode/mcp.json
```

Your project should now look like:

```text
my-salesforce-project/
│
├── .vscode/
│   └── mcp.json
│
├── force-app/
├── manifest/
└── sfdx-project.json
```

---

# Step 5 — Configure Salesforce DX MCP

Add the Salesforce DX MCP Server configuration to `.vscode/mcp.json`:

```json
{
  "servers": {
    "Salesforce DX": {
      "command": "npx",
      "args": [
        "-y",
        "@salesforce/mcp",
        "--orgs",
        "DEFAULT_TARGET_ORG",
        "--toolsets",
        "orgs,metadata,data,users",
        "--tools",
        "run_apex_test",
        "--allow-non-ga-tools"
      ]
    }
  }
}
```

### Configuration Breakdown

#### `command`

```json
"command": "npx"
```

Runs the MCP server using `npx`.

#### Salesforce MCP Package

```json
"-y",
"@salesforce/mcp"
```

Uses the Salesforce DX MCP package.

#### Org Configuration

```text
--orgs DEFAULT_TARGET_ORG
```

Specifies the Salesforce orgs that MCP can work with.

Replace the placeholder with the appropriate org configuration for your environment.

#### Toolsets

```text
--toolsets orgs,metadata,data,users
```

Enables the following groups of functionality:

| Toolset    | Purpose                              |
| ---------- | ------------------------------------ |
| `orgs`     | Work with Salesforce org information |
| `metadata` | Retrieve and deploy metadata         |
| `data`     | Query Salesforce data                |
| `users`    | Work with users and permissions      |

Salesforce groups MCP tools into logical toolsets so that an AI client can load only the capabilities needed for a task.

#### Apex Test Tool

```text
--tools run_apex_test
```

Enables the Apex test execution capability.

#### Non-GA Tools

```text
--allow-non-ga-tools
```

Allows access to tools that aren't yet generally available.

Only enable non-GA functionality when you understand the implications for your development environment.

---

# Step 6 — Start the MCP Server

Once `.vscode/mcp.json` has been created:

1. Save the file.
2. Open GitHub Copilot Chat/Agent in VS Code.
3. Allow VS Code/Copilot to start the configured MCP server if prompted.
4. Check that the **Salesforce DX** MCP server is connected.
5. Verify that the available Salesforce tools are visible.

If the server fails to connect, first verify:

```bash
sf org list
```

and confirm that the required Salesforce org is authenticated.

---

# Step 7 — Test the Connection

Start with a simple read-only request.

For example:

```text
Show me my authorized Salesforce orgs.
```

You can then test a metadata operation:

```text
Retrieve the Account object metadata from my Salesforce org.
```

Test Salesforce data access:

```text
Query 10 Accounts from my Salesforce org and show their Name and Industry.
```

Test Apex:

```text
Run the Apex tests for AccountFeedController.
```

The MCP client determines which MCP tools are appropriate for the natural-language request and executes them.

---

# Example Prompts

## Org Information

```text
Show me my authorized Salesforce orgs.
```

```text
Tell me which Salesforce org is configured as my target org.
```

---

## Metadata

```text
Retrieve the Case object metadata from my Salesforce org.
```

```text
Retrieve the Account object and its fields into my DX project.
```

```text
Deploy the metadata changes from force-app to my target org.
```

---

## SOQL / Data

```text
Query 10 Accounts where Industry is not null.
```

```text
Find Cases that are currently in Escalated status.
```

```text
Show me the number of Cases grouped by Status.
```

---

## Apex Testing

```text
Run the Apex tests for AccountFeedController.
```

```text
Run all Apex tests and tell me which tests failed.
```

```text
Run the test class for my latest Apex changes and summarize the failures.
```

---

## LWC Development

```text
Review the LWC components in my project and identify potential issues.
```

```text
Find the LWC that uses the AccountFeedController.
```

```text
Explain how this LWC communicates with Apex.
```

---

# MCP Toolsets

The Salesforce DX MCP Server provides capabilities through different toolsets.

```text
orgs
metadata
data
users
```

Conceptually:

```text
                Salesforce DX MCP
                       │
        ┌──────────────┼──────────────┐
        │              │              │
      Orgs          Metadata         Data
        │              │              │
   Org details    Retrieve        SOQL queries
   Org access     Deploy          Records
        │              │              │
        └──────────────┼──────────────┘
                       │
                     Users
                       │
                User / Permission
                    operations
```

The available MCP tools can evolve as Salesforce adds capabilities to the DX MCP Server.

---

# MCP vs Salesforce CLI

MCP does **not** replace Salesforce CLI.

Instead, MCP provides an AI-friendly interface on top of Salesforce development capabilities.

### Traditional approach

```text
Developer
    ↓
Salesforce CLI command
    ↓
Salesforce Org
```

For example:

```bash
sf project retrieve start
```

### MCP approach

```text
Developer
    ↓
Natural-language prompt
    ↓
GitHub Copilot
    ↓
MCP
    ↓
Salesforce
```

For example:

```text
Retrieve the Case object metadata from my Salesforce org.
```

Copilot determines which MCP capability is required to perform the task.

---

# Security Considerations

Be careful when connecting AI coding agents to Salesforce.

Recommended practices:

* Start with a sandbox or Developer Edition.
* Avoid giving AI agents unnecessary access to production.
* Use the minimum required MCP toolsets.
* Review proposed write/deployment operations before approving them.
* Avoid exposing sensitive Salesforce data unnecessarily.
* Do not commit credentials or authentication tokens to Git.
* Keep `.vscode/mcp.json` free of secrets.
* Use appropriate Salesforce permissions for the authenticated user.

For production environments, treat AI-assisted deployment and data modification the same way you would treat any other automated development tooling.

---

# Troubleshooting

## MCP Server Is Not Connecting

Check Salesforce authentication:

```bash
sf org list
```

If your org isn't authorized, authenticate again:

```bash
sf org login web
```

Then verify your target org:

```bash
sf config get target-org
```

---

## Wrong Salesforce Org Is Being Used

Check the current target org:

```bash
sf config get target-org
```

Set the correct one:

```bash
sf config set target-org=YOUR_ORG_ALIAS
```

Then restart/reload the MCP connection in VS Code.

---

## MCP Tools Are Not Available

Check:

1. `.vscode/mcp.json` exists.
2. The JSON is valid.
3. Node.js is installed.
4. Salesforce CLI is installed.
5. The Salesforce org is authenticated.
6. GitHub Copilot is signed in.
7. The MCP server is enabled/connected in VS Code.
8. The requested toolset/tool is included in the configuration.

---

# Important: Local DX MCP vs Salesforce Hosted MCP

Salesforce now provides multiple MCP approaches.

### Salesforce DX MCP Server

The local DX MCP Server is primarily aimed at developers working with:

* VS Code
* Salesforce CLI
* Local DX projects
* Local development workflows
* Metadata
* Apex
* Salesforce data

### Salesforce Hosted MCP Servers

Salesforce also provides hosted MCP servers that allow compatible AI clients to securely connect to Salesforce through Salesforce-hosted infrastructure and OAuth-based authentication.

These are different approaches and should not be confused with the local `@salesforce/mcp` setup described in this document.

---

# Recommended Learning Path

If you are new to Salesforce MCP, follow this order:

```text
1. Salesforce CLI
        ↓
2. Salesforce DX Project
        ↓
3. Authenticate Salesforce Org
        ↓
4. GitHub Copilot
        ↓
5. MCP Configuration
        ↓
6. Test Org Access
        ↓
7. Query Salesforce Data
        ↓
8. Retrieve Metadata
        ↓
9. Run Apex Tests
        ↓
10. Deploy Metadata
```

Start with **read operations** before allowing AI-assisted changes to your Salesforce org.

---

# Useful References

* Salesforce Developer documentation
* Salesforce DX MCP Server documentation
* Salesforce CLI documentation
* Salesforce Extensions for VS Code
* GitHub Copilot documentation
* Model Context Protocol documentation

> **Note:** Salesforce MCP capabilities are evolving quickly. Always verify the current Salesforce documentation before using a configuration copied from an older MCP guide, particularly because Salesforce has introduced newer hosted MCP and agentic development capabilities.

Refrence: https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_mcp_get_started.htm
