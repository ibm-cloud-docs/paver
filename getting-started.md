---

copyright:
  years: 2026
lastupdated: "2026-09-17"

keywords: paver getting started, install paver cli, authenticate paver cli, paver console

subcollection: paver

content-type: tutorial
account-plan: paid
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with IBM Paver
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

Learn how to get started with Paver by using the {{site.data.keyword.cloud_notm}} console or by installing and authenticating with the Paver CLI.
{: shortdesc}

IBM Paver is available in the console where you can quickly start a chat with Paver, or you can download the CLI and interact directly with Paver in your terminal to complete tasks within the context of your {{site.data.keyword.cloud_notm}} account.

## Using Paver in the {{site.data.keyword.cloud_notm}} console
{: #paver-console}
{: step}

You can chat with Paver directly in the {{site.data.keyword.cloud_notm}} console.

1. Log in to your {{site.data.keyword.cloud_notm}} account.
1. From the {{site.data.keyword.cloud_notm}} console menu bar, click **Chat with Paver**.
1. Enter your prompt, and start working with Paver to manage your {{site.data.keyword.cloud_notm}} account and resources.

## Installing the Paver CLI
{: #paver-install-cli}
{: step}

You can install the Paver CLI on macOS, Linux, or Windows.

### macOS and Linux
{: #paver-install-mac-linux}

Run the following command to install the Paver CLI:

```sh
curl -fsSL https://paver.cloud.ibm.com/cli/install | bash
```
{: pre}

The CLI is installed and ready to use immediately after installation completes.

### Windows
{: #paver-install-windows}

The Paver CLI requires a Unix shell. On Windows, install it through the Windows Subsystem for Linux (WSL).

#### Install Linux on WSL
{: #paver-windows-linx}

1. Open PowerShell with **Run as Administrator**.
1. Run the following command to install Ubuntu by default:

   ```sh
   wsl --install
   ```
   {: pre}

1. Complete the Unix account creation prompts when WSL restarts.

#### Install Node.js on WSL
{: #node-on-wsl}

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
{: #windows-paver}

In PowerShell (not WSL), run:

```sh
iwr https://paver.cloud.ibm.com/cli/install.ps1 | iex
```
{: pre}

## Authenticating with the Paver CLI
{: #paver-authentication}
{: step}

You can authenticate with single sign-on (SSO) or an API key.

### Log in with SSO
{: #paver-sso-login}

To use SSO, run the following command:

```sh
paver login
```
{: pre}

A web browser opens and prompts you to select the account that you want to target.

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
