### NPM dependencies install composite action

This composite action installs NPM dependencies for a Node.js project.
It leverages cached NPM dependencies to speed up the process if there are no changes in the dependencies.

This action will also add a comment in the PR if the Node.js version specified in the `engines` field in the `package.json` file should be updated.

#### Usage

```yaml
uses: actions/npm-install@v2
with:
    # Required. NPM token for the Debitoor NPM registry.
    debitoor-npm-token: ${{ secrets.DEBITOOR_NPM_TOKEN }}
    # Optional. NPM token for the SumUp NPM registry. 
    # If secret names are different, you can provide them both as below.
    sumup-npm-token: ${{ secrets.GH_PACKAGES_TOKEN != '' && secrets.GH_PACKAGES_TOKEN || secrets.READ_PACKAGES_PAT }}
    # Optional: SSH private key used to install NPM packages referenced by SSH URLs.
    gh-ssh-private-key: ${{ secrets.GH_SSH_PRIVATE_KEY }}
    gh-ssh-known-hosts: ${{ secrets.KNOWN_HOSTS }}
    # Optional. Set to true to use npm ci instead of npm install.
    # Default: true
    npm-ci-install: true
    # Optional. Additional flags to pass to the npm ci or npm install command.
    # Example: --legacy-peer-deps
    npm-command-flags: ''
```