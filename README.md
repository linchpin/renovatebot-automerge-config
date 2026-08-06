<table width="100%">
	<tr>
		<td align="left" width="70%">
			<strong>Linchpin Renovate Automerge Config</strong> — <em>deprecated</em><br />
			Moved to <a href="https://github.com/linchpin/renovatebot-config"><code>linchpin/renovatebot-config</code></a> as the <code>automerge</code> preset. This repository forwards to it and is kept only so projects that have not migrated yet keep working.
		</td>
		<td align="center" width="30%">
			<a href="https://github.com/linchpin/renovatebot-config"><img src="https://img.shields.io/badge/status-deprecated-critical.svg" alt="Status: deprecated" /></a>
			<a href="https://github.com/linchpin/renovatebot-config"><img src="https://img.shields.io/badge/moved%20to-renovatebot--config%3Aautomerge-1A1F6C?logo=renovate&logoColor=fff" alt="Moved to linchpin/renovatebot-config:automerge" /></a>
		</td>
	</tr>
	<tr>
		<td>
			A <strong><a href="https://linchpin.com">Linchpin</a></strong> preset · <em>Deprecated — do not add new consumers</em>
		</td>
		<td align="center" width="30%">
			<img src="https://assets.linchpin.com/linchpin-logo-primary.svg" width="100" alt="Linchpin" />
		</td>
	</tr>
</table>

> [!WARNING]
> **This repository is deprecated.** The automerge preset now lives in
> [`linchpin/renovatebot-config`](https://github.com/linchpin/renovatebot-config) alongside the
> base config it has always extended, so there is one repository to maintain instead of two.
>
> **Use `github>linchpin/renovatebot-config:automerge` instead.**

## Migrating

Change one line in the project's `renovate.json`:

```diff
   "extends": [
     "config:recommended",
-    "github>linchpin/renovatebot-automerge-config"
+    "github>linchpin/renovatebot-config:automerge"
   ],
```

Nothing else changes. The new preset is the same configuration in a new home — it extends
`github>linchpin/renovatebot-config` and overrides only the automerge behaviour, exactly as this
one did.

## Why this still exists

`default.json` here is now a forwarder that extends
`github>linchpin/renovatebot-config:automerge`, so projects that have not migrated resolve to
the identical configuration and keep automerging. The rules live in one place; this repository
holds no copy of them.

The repository will be sunset once nothing extends it. Until then it is fine to leave a project
pointed here, but **do not point anything new at it** and migrate opportunistically.

## What the preset does

The automerge behaviour, on top of everything inherited from
[`linchpin/renovatebot-config`](https://github.com/linchpin/renovatebot-config):

- Automerges non-major (`minor`, `patch`, `pin`, `digest`) npm and Composer updates.
- Never automerges majors — those still get a human review.
- Automerges non-major GitHub Actions updates before 6am on Monday.
- Automerges lockfile maintenance.
- Uses platform automerge (GitHub's own auto-merge) rather than Renovate merging directly.

> [!IMPORTANT]
> The GitHub repository MUST be configured to allow auto-merge or Renovate PRs will not be
> automatically merged: **Repo → Settings → General → "Allow auto-merge"**.

Everything else — grouping into `maintenance/MM-YYYY` base branches, commit prefixes, labels,
and package routing for npm, Composer, wp-packages, wpackagist and packagist.linchpin.com — is
documented in the
[`linchpin/renovatebot-config` README](https://github.com/linchpin/renovatebot-config#readme).

![Linchpin an award winning digital agency building immersive, high performing web experiences](https://assets.linchpin.com/github/linchpin-github-repo-banner.jpg)
