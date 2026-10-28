# Network Policy Visualizer

Visualize Cilium, Isovalent and Kubernetes network policies side by side with
their YAML in VS Code, using the PolicyMap from Isovalent Hubble Timescape.

## Features

- **Side-by-side visualization**: Opens a panel next to your YAML editor showing the PolicyMap
- **Live updates**: The visualization updates as you edit the YAML
- **Automatic detection**: Recognizes supported network policy YAML files by `apiVersion` and `kind`
- **Timescape flows**: Optionally lists the flows Hubble Timescape recorded for the workloads the policy selects

## Supported Policy Types

| Kind                                | apiVersion               |
| ----------------------------------- | ------------------------ |
| `CiliumNetworkPolicy`               | `cilium.io/v2`           |
| `CiliumClusterwideNetworkPolicy`    | `cilium.io/v2`           |
| `NetworkPolicy`                     | `networking.k8s.io/v1`   |
| `IsovalentNetworkPolicy`            | `isovalent.com/v1`       |
| `IsovalentClusterwideNetworkPolicy` | `isovalent.com/v1`       |
| `TetragonNetworkPolicy`             | `cilium.io/v1alpha1`     |
| `TetragonNetworkPolicyNamespaced`   | `cilium.io/v1alpha1`     |
| `SmartSwitchNetworkPolicy`          | `isovalent.com/v1alpha1` |

## Installation

The extension is published as `isovalent.vscode-npv-extension`:

- **VS Code**: install **Network Policy Visualizer** from the
  [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=isovalent.vscode-npv-extension).
- **Cursor, VSCodium and other editors using Open VSX**: install it from
  [Open VSX](https://open-vsx.org/extension/isovalent/vscode-npv-extension).
- **Offline**: download the `.vsix` of a release from the
  [releases page](https://github.com/isovalent/vscode-npv-extension/releases) and
  run `code --install-extension vscode-npv-extension-<version>.vsix`, or use
  **Extensions: Install from VSIX...** from the command palette.

The extension is released together with Isovalent Hubble Timescape and shares
its version numbers.

## Usage

1. Open a YAML file containing a supported network policy
2. Click the graph icon in the editor title bar, or run **Visualize Network Policy** from the command palette
3. The PolicyMap visualization opens in a side panel

### Timescape flows

**Unlock real-time flow visibility**, at the top right of the panel, opens a
short introduction to Timescape; **Unlock** then moves on to the connection
form (once connected, the button reads **Timescape connected** and opens the
form directly). The form takes the base URL of the Hubble Timescape public REST
API plus an optional bearer token. Once connected, the flows recorded for the
workloads the policy selects are listed below the map.

The time range and refresh rate pickers in the flow panel's top bar default to
the last hour, refreshed every 10s.

The URL is kept in the extension's global state; the token is kept in VS
Code's [SecretStorage](https://code.visualstudio.com/api/references/vscode-api#SecretStorage),
so it is neither written to plaintext extension state nor carried by settings
sync. Requests are sent by the extension host, so the token is never exposed to
the visualization panel.

## Reporting Issues

Open an issue in the
[issue tracker](https://github.com/isovalent/vscode-npv-extension/issues) and
include:

- the extension version, shown in the Extensions view;
- the VS Code version, from **Help: About**;
- a policy that reproduces the problem, with any sensitive names or addresses
  removed;
- any errors from **Developer: Open Webview Developer Tools**, if the panel
  stays empty or shows an error.

Report security vulnerabilities privately through your Isovalent support
channel instead of opening a public issue.

## License

The extension is released under the MIT License, see `LICENSE`. The notices of
the third-party software included in the extension are in
`ThirdPartyNotices.txt`, which is shipped in the extension package and attached
to each release.
