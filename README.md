# GitHub Agent MCP Setup Guide

This guide provides detailed instructions on setting up and using the GitHub MCP (Model Context Protocol) with Cursor IDE using Smithery.ai.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Creating a GitHub Fine-grained Token](#creating-a-github-fine-grained-token)
- [Setting up Smithery.ai](#setting-up-smitheryai)
- [Configuring Cursor IDE](#configuring-cursor-ide)
- [Testing the Setup](#testing-the-setup)
- [Troubleshooting](#troubleshooting)

## Prerequisites
- A GitHub account
- Cursor IDE installed
- Access to [Smithery.ai](https://smithery.ai/)

## Creating a GitHub Fine-grained Token

1. Go to GitHub Settings > Developer Settings > Personal Access Tokens > Fine-grained tokens
2. Click "Generate new token"
3. Configure the token:
   - Set a token name (e.g., "GitHub MCP Token")
   - Set expiration (recommended: 30-90 days)
   - Select the repositories you want to give access to (or all repositories)
   - Set permissions:
     - Repository permissions:
       - Contents: Read and Write
       - Metadata: Read-only
       - Pull requests: Read and Write
       - Issues: Read and Write

4. Click "Generate token"
5. **IMPORTANT**: Copy and save the token immediately as it won't be shown again

## Setting up Smithery.ai

1. Visit [Smithery.ai](https://smithery.ai/)
2. Create an account or sign in
3. Navigate to the GitHub MCP section
4. Enter your fine-grained token
5. Smithery will generate a configuration JSON file that looks like this:
   ```json
   {
     "mcpServers": {
       "github": {
         "command": "npx",
         "args": [
           "-y",
           "@smithery/cli@latest",
           "run",
           "@smithery-ai/github",
           "--key",
           "your-smithery-key",
           "--profile",
           "your-profile-id"
         ]
       }
     }
   }
   ```

## Configuring Cursor IDE

1. Open Cursor IDE
2. Navigate to Settings > AI > MCP Configuration
3. Paste the Smithery-generated JSON configuration
4. Save the settings
5. Restart Cursor IDE

## Testing the Setup

To test if everything is working:

1. Open Cursor IDE
2. Press Cmd/Ctrl + I to open the AI prompt
3. Type a command like:
   ```
   Create a new GitHub repository called test-repo with a README
   ```
4. The AI should be able to execute the command using the GitHub MCP

Example commands you can try:
- Create a new repository
- Create issues
- Create pull requests
- Modify repository contents
- List repositories
- Search code

## Troubleshooting

### Common Issues

1. **Token Permission Errors**
   - Verify token permissions in GitHub settings
   - Ensure token hasn't expired
   - Check repository access settings

2. **Smithery Connection Issues**
   - Verify Smithery key is valid
   - Check if profile ID is correct
   - Ensure npx is installed globally

3. **Cursor Configuration**
   - Verify JSON format is correct
   - Check if Cursor is up to date
   - Try restarting Cursor

### Error Messages and Solutions

- "Resource not accessible by personal access token":
  - Check token permissions
  - Verify repository access settings
  - Generate a new token if needed

- "Unknown command":
  - Update @smithery/cli to latest version
  - Check npx installation
  - Verify command syntax

## Additional Resources

- [Smithery Documentation](https://smithery.ai/docs)
- [GitHub Fine-grained Token Documentation](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token)
- [Cursor IDE Documentation](https://cursor.sh/docs)

## Contributing

Feel free to contribute to this guide by creating issues or pull requests. Your feedback and improvements are welcome!

## License

This project is licensed under the MIT License - see the LICENSE file for details.