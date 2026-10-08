---

copyright:
  years: 2026
lastupdated: "2026-10-08"

keywords: install paver cli, authenticate paver cli, paver cli macos, paver cli linux, paver cli windows, paver sso login, paver api key login

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Installing Paver CLI
{: #paver-cli-install}

Install the Paver CLI on your local machine and authenticate with your {{site.data.keyword.cloud_notm}} account to start working with Paver directly from the terminal.
{: shortdesc}

## Installing the CLI
{: #paver-install-cli}

You can install Paver CLI on macOS, Linux, or Windows.

### macOS and Linux
{: #paver-install-mac-linux}

Run the following command to install the Paver CLI:

```sh
curl -fsSL https://paver.cloud.ibm.com/cli/install | bash
```
{: pre}

After the installation completes, you must [authenticate with your {{site.data.keyword.cloud_notm}} account](/docs/paver?topic=paver-paver-cli-install#paver-authentication) and target a specific account to get started.

### Windows
{: #paver-install-windows}

The Paver CLI requires a Unix shell. On Windows, install it through the Windows Subsystem for Linux (WSL).

#### Install Linux on WSL
{: #paver-windows-linux}

1. Open PowerShell with **Run as Administrator**.
1. Run the following command to install Ubuntu by default:

   ```sh
   wsl --install
   ```
   {: pre}

1. Complete the Unix account creation prompts when WSL restarts.

#### Install Node.js on WSL
{: #paver-node-on-wsl}

1. Run the following command inside WSL:

   ```sh
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
   ```
   {: pre}

1. Restart the WSL terminal.
1. Install Node.js:

   ```sh
   nvm install node
   ```
   {: pre}

#### Install the Paver CLI on Windows
{: #paver-install-windows-cli}

In PowerShell (not WSL), run:

```sh
iwr https://paver.cloud.ibm.com/cli/install.ps1 | iex
```
{: pre}

## Authenticating with Paver CLI
{: #paver-authentication}

You can authenticate with single sign-on (SSO) or an API key.

### Log in with SSO
{: #paver-sso-login}

To use SSO, run the following command:

```sh
paver login
```
{: pre}

A browser opens and prompts you to select the account that you want to target.

### Log in with an API key
{: #paver-api-key-login}

To use an API key and target your account, run the following commands:

1. Log in with your API key:

   ```sh
   paver login --apikey $CLOUD_API_KEY
   ```
   {: pre}

1. Select your target account:

   ```sh
   paver account target
   ```
   {: pre}

## Updating the Paver CLI
{: #paver-update-cli}

The Paver CLI automatically checks for updates on a schedule. To update immediately to the latest version, run the following command:

```sh
paver update
```
{: pre}

Keep your CLI updated to ensure compatibility with the server.
{: important}

## Next steps
{: #paver-cli-next-steps}

After you authenticate, start an interactive chat session with Paver:

```sh
paver chat
```
{: pre}

In the chat, you can ask Paver about itself, explore available commands, or start working with your {{site.data.keyword.cloud_notm}} account and resources.
