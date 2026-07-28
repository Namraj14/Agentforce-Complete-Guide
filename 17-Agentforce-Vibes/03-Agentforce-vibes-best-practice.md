# Best Practices

Here's a list of best practices for using Agentforce Vibes Extension

### Write Effective Requests

- **Be specific about your goals**: Instead of "help with testing," say "run all Apex tests in my AccountController class".
- **Provide context**: Mention specific orgs, projects, or files you're working with.
- **Use natural language**: Describe what you want to accomplish rather than trying to format commands.
- **Ask for explanations**: Request explanations of actions for learning purposes.

### Manage Tool Execution

- **Review before approving**: Always check proposed actions before confirming execution.
- **Use incremental steps**: Break complex workflows into manageable pieces.
- **Monitor progress**: Pay attention to progress indicators and error messages.
- **Verify results**: Check that completed actions meet your expectations.

### Security Considerations

- **Verify org contexts**: Ensure actions target the correct Salesforce org.
- **Review metadata changes**: Check what's being deployed before confirmation.
- **Use appropriate environments**: Use sandboxes for testing, production org for final deployment.
- **Monitor permissions**: Ensure you have appropriate access for requested actions.

### Initial Setup

- **Use sample projects**: Start with [dreamhouse-lwc](https://github.com/trailheadapps/dreamhouse-lwc) or [ebikes-lwc](https://github.com/trailheadapps/ebikes-lwc) for rich testing.
- **Test incrementally**: Verify each step before proceeding to the next.
- **Document your setup**: Note any custom configurations for team sharing.
- **Regular updates**: Keep the VS Code extension updated as new versions are released.

### Security Considerations

- **Use sandbox orgs**: Connect to sandbox environments for testing Agentforce.
- **Review permissions**: Ensure your user has appropriate development permissions.
- **Monitor org access**: Regularly review and refresh org authorizations.
- **Backup important work**: Maintain version control for critical development.

### Model Selection

- **Match the model to the task**: Use a balanced model (Sonnet) for everyday questions, explanations, and single-file edits. Switch to the most capable model (Opus) for complex multi-file builds, architectural planning, and Plan Mode approval.
- **Switch mid-session when scope changes**: You can change models without losing context. Start on a faster model while exploring, then switch up before generating a plan or executing a complex task.
- **Monitor token usage**: The context-window indicator shows your current usage. More capable models consume more tokens per response. Start a fresh conversation rather than continuing in a heavily compacted session.
- **Factor in Flex Credits**: If your org uses metered billing, model choice affects cost. Use balanced or fast models for exploration and iteration. Reserve premium models for tasks where output quality justifies the expense. See [Usage and Billing](/docs/platform/agentforcevibes/guide/afv-admin-billing.html).

### Team Setup

- **Standardize configurations**: Share common settings across your development team.
- **Document custom tools**: If you add custom MCP servers, document them for the team.
- **Regular sync**: Ensure all team members use compatible extension versions.
