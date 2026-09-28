<p align="center">
  <img src=".github/banner.svg" alt="oe, the Opportunity Encoder command line" width="100%">
</p>

# oe

`oe` is the command line for [Opportunity Encoder](https://opportunity-encoder-production.up.railway.app). It lets you, a script, or your coding agent read and change your Workflows, Modules, Visualizations and Blueprints from a terminal. It acts as you, and never beyond what you can reach in OE.

Every command comes from the API description OE serves, so `oe --help` always matches the OE you are signed in to.

## Install

```bash
brew install eidra-umain/oe/oe
```

This works on macOS and Linux. On Windows, or without Homebrew, download the archive for your machine from the [latest release](https://github.com/eidra-umain/homebrew-oe/releases/latest) and put `oe` on your `PATH`.

## Sign in

```bash
oe login
```

This opens OE in your browser and asks you to approve the sign-in. After that, `oe` renews itself while you use it, for up to 90 days. You can see and revoke every sign-in in OE, under **Settings → Personal Access Tokens**.

On a machine that cannot open a browser, such as a CI runner, make a Personal Access Token in Settings and hand it over instead:

```bash
export OE_TOKEN=oe_pat_…
```

## Use

```bash
oe --help                                   # every command
oe list-workflows -o json                   # your Workflows, as JSON
oe read-workflow-visualization <id> > viz.html
```

A 4xx answer exits with status 4, and a 5xx with status 5; the JSON body is on stdout.

| Setting           | What it does                                                    |
| ----------------- | --------------------------------------------------------------- |
| `OE_TOKEN`        | A Personal Access Token to use instead of signing in            |
| `OE_URL`          | Another OE to talk to, such as a local development server       |
| `OE_MACHINE_NAME` | What this machine is called when it signs in; its host name if unset |

## Update and remove

```bash
brew upgrade oe      # the latest oe
oe logout            # end this machine's sign-in
brew uninstall oe
```

## About this repository

This is a [Homebrew tap](https://docs.brew.sh/Taps). OE's release pipeline publishes each new `oe` here, as a release and as `Formula/oe.rb`, once it has passed OE's tests. Please don't edit the formula by hand; the next release replaces it.

Copyright © 2026 Dawid Dahl and Prabhat Ramesh. All rights reserved.
