# Security Policies and Procedures

This document outlines the security procedures and general policies for the
Network Policy Visualizer extension for Visual Studio Code.

- [Disclosing a security issue](#disclosing-a-security-issue)
- [Vulnerability management](#vulnerability-management)
- [Suggesting changes](#suggesting-changes)

## Disclosing a security issue

The Network Policy Visualizer maintainers take all security issues in the
extension seriously. Thank you for improving its security. We appreciate your
dedication to responsible disclosure and will make every effort to acknowledge
your contributions.

**Do not report security vulnerabilities through public GitHub issues.**

Network Policy Visualizer uses GitHub's private vulnerability reporting. Submit
a report from the
[Security tab](https://github.com/isovalent/vscode-npv-extension/security/advisories/new)
of this repository. To learn more about this feature, review
[GitHub's documentation on private reporting](https://docs.github.com/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability).

Here are some helpful details to include in your report:

- a detailed description of the issue
- the steps required to reproduce the issue
- the versions of the extension and of VS Code that may be affected
- if known, any mitigations for the issue

A maintainer will acknowledge the report within three (3) business days, and
will send a more detailed response within an additional three (3) business days
indicating the next steps in handling your report.

If you have been unable to submit a report through GitHub or have not received a
response within that window, contact the Cisco Product Security Incident
Response Team (PSIRT) at [psirt@cisco.com](mailto:psirt@cisco.com), following
the
[Cisco Security Vulnerability Policy](https://sec.cloudapps.cisco.com/security/center/resources/security_vulnerability_policy.html).
Cisco PSIRT accepts messages encrypted with its
[PGP public key](https://cscrdr.cloudapps.cisco.com/cscrdr/security/center/files/Cisco_PSIRT_PGP_Public_Key.asc).

After the initial reply to your report, the maintainers will endeavor to keep
you informed of the progress towards a fix and full announcement, and may ask
for additional information or guidance.

## Vulnerability management

When the maintainers receive a disclosure report, they will assign it to a
primary handler.

This person will coordinate the fix and release process, which involves the
following steps:

- confirming the issue
- determining the affected versions of the extension
- auditing code to find any potential similar problems
- releasing a fixed version to the Visual Studio Marketplace and Open VSX

Fixes are released in a new version of the extension rather than backported to
earlier ones, so keep the extension up to date.

## Suggesting changes

If you have suggestions on how this process could be improved, please
[open an issue](https://github.com/isovalent/vscode-npv-extension/issues).
