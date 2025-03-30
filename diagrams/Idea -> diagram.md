When I want to make a github issue I’d like to trigger the request from my phone. When I make an issue request in “diagrams” repo, I want to create an initial copy of the diagram


Here, the credentials are not hardcoded directly in the workflow, but they are being used in a command to authenticate with the GitHub CLI. This is actually a good practice as it uses GitHub Secrets, which are securely stored and managed by GitHub.

To improve the security and usage of this workflow, here’s a step-by-step approach:

Ensure that the GitHub Token is stored securely in GitHub Secrets:

Go to your repository settings.

Navigate to “Secrets and variables” > “Actions”.

Add a new repository secret with the name GITHUB_TOKEN and the respective token value.

Reference the Secret in the Workflow:

The workflow already references the secret correctly. Ensure that no credentials are hardcoded directly in the workflow file.

Update the Workflow:The workflow is already using best practices by leveraging GitHub Secrets. No changes are needed for using the GitHub Token.

Here is the updated workflow with additional comments for clarity:

`name: Run Command in Codespace`
`on:`
  `workflow_dispatch:`
    `inputs:`
      `codespace:`
        `description: "The Codespace name or ID to operate on."`
        `required: true`
      `command:`
        `description: "The terminal command to execute inside the Codespace."`
        `required: true`

`jobs:`
  `run-command:`
    `runs-on: ubuntu-latest`
    `steps:`
      `- name: Install GitHub CLI if needed`
        `run: |`
          `if ! command -v gh >/dev/null; then`
            `sudo apt-get update && sudo apt-get install -y gh`
          `fi`
      `- name: Authenticate GitHub CLI`
        `run: echo "${{ secrets.GITHUB_TOKEN }}" | gh auth login --with-token > /dev/null`
      `- name: Unpause Codespace`
        `run: gh codespace resume "${{ github.event.inputs.codespace }}" > /dev/null`
      `- name: Execute Terminal Command`
        `run: gh codespace exec "${{ github.event.inputs.codespace }}" -- ${{ github.event.inputs.command }} > /dev/null`
      `- name: Pause Codespace`
        `run: gh codespace stop "${{ github.event.inputs.codespace }}" > /dev/null`