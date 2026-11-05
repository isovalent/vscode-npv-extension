# Network Policy Visualizer

See what a Cilium, Isovalent or Kubernetes network policy allows and denies as
you write it. The extension draws the policy as an interactive map next to its
YAML in VS Code, and can show the traffic the policy applies to in your
clusters.

<!-- Served from networkpolicy.io while isovalent/vscode-npv-extension, where the
registries load relative images from, is private. Point it back at
images/screenshot.png once that repository is public. -->

![A CiliumNetworkPolicy open in the editor, with its map in the Policy Visualizer panel](https://networkpolicy.io/images/vscode-npv-extension-screenshot.png)

## Features

- **Side-by-side visualization**: Opens a panel next to your YAML editor showing the policy map
- **Live updates**: The map updates as you edit the YAML
- **Automatic detection**: Recognizes supported network policy YAML files by `apiVersion` and `kind`
- **Real-time flow visibility**: Connect to Hubble Timescape to see the flows of the workloads the policy selects

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

Its versions follow the releases of Hubble Timescape.

## Usage

1. Open a YAML file containing a supported network policy
2. Click the graph icon in the editor title bar, or run **Visualize Network Policy** from the command palette
3. The policy map opens in a side panel

## Real-time flow visibility

The map shows what a policy allows on paper. Connected to Hubble Timescape, the
extension also shows the traffic the policy actually applies to.

Isovalent, the creators of Cilium, the eBPF-based networking, security and
observability layer for Kubernetes, build its enterprise distribution, the
[Isovalent Enterprise Platform](https://isovalent.com/products/kubernetes-networking/).
Its Hubble component observes the network flows between your workloads, and
Hubble Timescape, part of the platform, records them so they can be searched
and analyzed, as they happen and long after.

To connect the extension to Timescape:

1. Click **Unlock real-time flow visibility** at the top right of the panel,
   then **Unlock**.
2. Enter the URL of your Timescape public REST API and, if it requires one, a
   bearer token. Your Timescape administrator can provide both.
3. The flows Timescape recorded for the workloads the policy selects are listed
   below the map. They cover the last hour and refresh every 10 seconds; use
   the time range and refresh rate pickers above the flows to change this.

Once connected, the button reads **Timescape connected** and reopens the
connection form.

The token is kept in VS Code's
[SecretStorage](https://code.visualstudio.com/api/references/vscode-api#SecretStorage),
so it is neither written to plaintext extension state nor carried by settings
sync. Requests to Timescape are sent by the extension itself, never by the
visualization panel, so the token is not exposed to it.

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
