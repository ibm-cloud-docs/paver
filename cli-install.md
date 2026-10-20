---

copyright:
  years: 2026
lastupdated: "2026-10-20"

keywords: install paver cli, authenticate paver cli, paver cli macos, paver cli linux, paver cli windows, paver sso login, paver api key login

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Installing {{site.data.keyword.paver_full_notm}} CLI
{: #paver-cli-install}

Install the {{site.data.keyword.paver_full}} CLI and authenticate with your {{site.data.keyword.cloud_notm}} account to start working with {{site.data.keyword.paver}} directly from the terminal.
{: shortdesc}

You can install {{site.data.keyword.paver_full_notm}} CLI on macOS, Linux, or Windows.

## macOS and Linux
{: #paver-install-mac-linux}

Run the following command to install the {{site.data.keyword.paver_full_notm}} CLI:

```sh
curl -fsSL https://paver.cloud.ibm.com/cli/install | bash
```
{: pre}

After the installation completes, you must [authenticate with your {{site.data.keyword.cloud_notm}} account](/docs/paver?topic=paver-paver-cli-install#paver-authentication) and target a specific account to get started.

## Windows
{: #paver-install-windows}

On Windows, install the {{site.data.keyword.paver_full_notm}} CLI by using PowerShell.

### Before you begin
{: #paver-windows-prereqs}

Make sure that you have the following prerequisites:

* Windows 10 or 11
* PowerShell 5.1
* Node.js version 24 or later

### Set up your PowerShell working directory
{: #paver-windows-workdir}

1. Start PowerShell with **Run as administrator**.

   When you start PowerShell as an administrator, the default working directory is `C:\Windows\system32`.
   {: note}

1. Create a dedicated working directory, such as `C:\Paver`, and change to that directory:

   ```powershell
   New-Item -ItemType Directory -Path C:\Paver -Force
   Set-Location C:\Paver
   ```
   {: pre}

Do not run setup commands or store files in `C:\Windows\system32`.
{: important}

### Install the Paver CLI on Windows
{: #paver-install-windows-cli}

1. In the PowerShell window that you started as an administrator, make sure that your current working directory is `C:\Paver`.
1. Run the following command:

   ```powershell
   iwr https://paver.cloud.ibm.com/cli/install.ps1 | iex
   ```
   {: pre}

1. After the installer completes, open a new PowerShell window as an administrator and change to the `C:\Paver` directory.

   ```powershell
   Set-Location C:\Paver
   ```
   {: pre}

   Existing PowerShell windows don't pick up the updated `PATH`, so you must open a new window.
   {: important}

1. Verify the installation. A version string is displayed.

   ```powershell
   paver.cmd --version
   ```
   {: pre}

1. Update the CLI to the latest version, even if the CLI was already installed.

   ```powershell
   paver.cmd update --yes
   ```
   {: pre}

After the installation completes, you must [authenticate with your {{site.data.keyword.cloud_notm}} account](/docs/paver?topic=paver-paver-cli-install#paver-authentication) and target a specific account to get started.

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

Update the CLI to the latest version:

```sh
paver update
```
{: pre}



## Next steps
{: #paver-cli-next-steps}

After you authenticate, start an interactive chat session with {{site.data.keyword.paver}}:

```sh
paver chat
```
{: pre}

In the chat, you can ask {{site.data.keyword.paver}} about itself, explore available commands, or start working with your {{site.data.keyword.cloud_notm}} account and resources.
