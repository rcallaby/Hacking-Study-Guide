# Guide to *building* vulnerable VMs

---

# Summary of the supplied resources (quick takeaways)

* **VulnHub resources & index** — VulnHub curates many community-built “boot2root” VMs and links to guides and resources for authors; it’s a good canonical starting place for community norms, examples, and download/packaging expectations. ([VulnHub][1])
* **FalconSpy — “Creating Boxes for Vulnhub”** — practical advice focused on the author’s workflow: set goals, pick an OS base, document intentionally vulnerable services, test thoroughly, produce a walkthrough only after publishing, and include checksums/packaging (OVA/zip). Good operational checklist for a first VulnHub box. ([FalconSpy][2])
* **Techorganic — “Creating a virtual machine hacking challenge”** — emphasis on designing a challenge (clear goal/flag), mapping difficulty progression, avoiding accidental breakage, and thinking about dependencies and reproducibility. Useful for challenge design and difficulty calibration. ([blog.techorganic.com][3])
* **Donavan (3-part series)** — deep, developer-oriented narrative across design, implementation, and lessons learned: Part 1 covers building an “easy, OSCP-like” machine (design choices and pitfalls); Part 2 walks through a machine that introduced less-common services and associated complexity; Part 3 argues for multi-machine ranges and modular design. Excellent for lessons learned and real-world examples. ([donavan.sg][4])
* **Hack The Box blog — “Building your first HTB machine”** — explains platform-specific expectations for HTB: quality bar, testing, avoiding accidental network exposure, good writeups policy, and submission process (community review); useful if you plan to publish on HTB. ([Hack The Box][5])


---

## Planning & design (before you touch a VM)

**a. Define the learning objective(s)**

* Decide exactly what a player should learn or demonstrate (e.g., “privilege escalation using misconfigured sudo”, “exploiting an outdated web app”, or “chaining information disclosure → remote code exec”). Keep each machine focused (one or two skills). See Techorganic and FalconSpy for guidance on goals and difficulty calibration. ([blog.techorganic.com][3])

**b. Decide a difficulty curve & target audience**

* Beginner: obvious vulnerability, lots of hints.
* Intermediate: requires enumeration, chaining issues.
* Advanced: bypassing mitigations, custom exploits. (Donavan’s series is useful for mapping real examples to difficulty levels.) ([donavan.sg][4])

**c. Threat model & safety**

* Ensure the VM is isolated (host-only or NAT in packaging), has no accidental exposure of your private data, and contains no active, malware-like tooling or live C2 servers. The HTB/VulnHub guides stress safe packaging and isolation. ([Hack The Box][5])

**d. High-level flow (player steps)**

* Entry → Enumeration → Initial compromise → Privilege escalation or capture of final flag. Map each step and the expected artifacts (files, services, logs).

---

## Build environment & tooling

**Recommended tools**

* Hypervisor: VirtualBox, VMware Workstation/Player (both widely used and supported by VulnHub/HTB). VulnHub OVA distribution is common. ([VulnHub][6])
* Base images: Minimal Debian/Ubuntu, or old distro purposely selected if you mean to demonstrate an historical vuln (but beware packaging/testing complexities).
* Automation: Use provisioning (shell scripts, Ansible) to apply the vulnerable configuration reproducibly. This also helps others reproduce/setup. FalconSpy recommends scripts and listing dependencies. ([FalconSpy][2])

**VM networking modes while developing**

* **Host-only** for safe offline testing.
* **NAT** when you want limited outbound access for the VM while preventing inbound exposure.
* Use snapshots to save clean states after each step.

---

## Implementation (what to put in the VM)

**a. OS & packages**

* Keep the base OS minimal. Install only the services needed for the challenge. Document exact package versions. Favored approach: start from a clean snapshot, automate installations with a provisioning script.

**b. Services to include (examples by learning goal)**

* **Web challenges:** HTTP server, vulnerable web app (document version), misconfigured file perms.
* **Auth problems:** Weak passwords, default credentials, flawed account lockout logic (safe to demonstrate with clearly fabricated users).
* **Network services:** Old FTP, SMTP, or custom daemons — but avoid including active malware/C2. Donavan’s Part 2 includes examples of lesser-known services (CUPS, IRC) to broaden exposure. ([donavan.sg][7])

**c. Flags & artifacts**

* Typical flags: user.txt and root.txt (or equivalent). Place them in plausible locations and ensure they’re consistent with the intended steps.
* Include breadcrumbs — logs, files, or misconfigurations that guide the player if they’re stuck (but don’t make it trivial).

**d. Persistence & resets**

* Avoid persistent backdoors that survive a snapshot revert unless intentionally part of the challenge. Keep the VM stateless between snapshots.

---

## Hardening the challenge design (avoid accidental hints/breakage)

* Avoid global wildcards in file names, temporary files left in home directories, or test accounts that leak the solution. Techorganic and FalconSpy emphasize reproducibility and avoiding accidental leaks. ([blog.techorganic.com][3])
* Use deliberate, documented misconfigurations rather than unpredictable race conditions or flaky timing issues.

---

## Testing checklist (before publishing)

Run the checklist yourself and with 1–2 independent testers:

* [ ] Rebuild from base using provisioning scripts (ensures reproducibility).
* [ ] Confirm intended exploit path works from scratch (without developer’s helpers).
* [ ] Check for noisy or unrelated services that could confuse players.
* [ ] Confirm network isolation: the VM cannot be used as an attack pivot to other hosts. HTB/VulnHub emphasize safe sandboxing. ([Hack The Box][5])
* [ ] Create checksums (MD5/SHA1) for the OVA/zip you plan to distribute. (VulnHub entries often include checksums.) ([VulnHub][6])

---

## Documentation & packaging

**Minimum documentation to include**

* Short description and learning objectives.
* Setup instructions (how to import OVA into VirtualBox/VMware).
* Network mode to use for safe operation.
* Hints policy (when you’ll publish walkthroughs — many authors recommend waiting a week or so). FalconSpy and VulnHub examples include these items. ([FalconSpy][2])

**Suggested file layout**

```
/my-vulnbox/
├─ build/                     # provisioning scripts (Ansible / shell)
├─ ova/                       # produced OVA image
├─ docs/
│  ├─ README.md               # setup + learning objectives
│  ├─ HINTS.md                # optional hints
│  └─ CHECKSUMS.txt
├─ media/                     # screenshots (optional)
└─ tests/                     # teardown / smoke tests
```

**Publishing**

* **VulnHub:** create an entry, include screenshots, checksums, and README; many authors also add a “walkthrough” after some time. VulnHub resource page lists community examples and expectations. ([VulnHub][1])
* **Hack The Box:** follow HTB’s submission guide and quality expectations in their blog post if you intend to submit an HTB machine (platform has higher QA and review standards). ([Hack The Box][5])

---

## Post-release: walkthroughs, hints, and ethics

* Many authors (FalconSpy, others) recommend **waiting** before posting a full walkthrough — let the community try first. When you do publish a walkthrough, separate it clearly from the challenge and tag spoilers. ([FalconSpy][2])
* Keep ethical usage in mind: remind users to only run these images in isolated/sandbox environments or on private labs.

---

## Common pitfalls & lessons learned (from the community)

* **Unreproducible environments** — fragile manual setups are common. Solution: automate provisioning. (FalconSpy.) ([FalconSpy][2])
* **Overly obscure dependency choices** — picking odd package versions often breaks reproducibility. (Techorganic.) ([blog.techorganic.com][3])
* **Not documenting the objective** — players shouldn’t have to guess the learning goal; label it. (Donavan’s posts explain the importance of clarity.) ([donavan.sg][4])

---

# Ready-to-use templates & checklists

## Minimal README template (copy/paste)

```
# <BoxName> - short tagline

## Learning objectives
- Objective 1
- Objective 2

## Setup
1. Import <BoxName>.ova into VirtualBox or VMware.
2. Use Host-Only or NAT network mode (recommended: Host-Only).
3. Snapshot after initial boot to return to a clean state.

## Flags
- user.txt - typical location: /home/username/user.txt
- root.txt - typical location: /root/root.txt

## Hints policy
- Hints available in HINTS.md
- Walkthrough will be published on <date> (optional).

## Reproducibility
- Build scripts: /build/provision.sh
- OVA checksum: SHA256:<...>
```

## Testing checklist (copyable)

* Rebuild from script (PASS/FAIL)
* Smoke test: HTTP responds on expected port (PASS/FAIL)
* Flag check: locate and read both flags from fresh snapshot (PASS/FAIL)
* Networking isolation verified (PASS/FAIL)
* Clean shutdown and snapshot restore (PASS/FAIL)

---

# Additional high-quality resources (beyond the supplied links)

* Medium guide — “Creating Vulnerable Machines: Beginner Guide” (practical walkthrough of the process). ([Medium][8])
* VulnHub examples and OVA checklist pages (to model packaging and README style). ([VulnHub][1])
* YouTube walkthroughs / “How to build a vulnerable machine” videos — good for visual learners and packaging steps. (Search results show relevant tutorials.) ([YouTube][9])
* FalconSpy’s Medium/Blog posts for practical step-by-step guidance on creating boxes and common author mistakes. ([Medium][10])

---

# Quick “starter recipe” (minimum viable vulnerable VM)

1. Base OS: Ubuntu 20.04 LTS minimal.
2. Install a simple vulnerable web app (deliberately configured older version) in `/var/www/html/challenge`. Document version & source.
3. Create a non-root user `alice` with an obvious-but-not-trivial password and place `user.txt` in `/home/alice`.
4. Add a misconfigured sudo entry for one specific binary that the player can abuse for privilege escalation (documented in your notes, not in README).
5. Provision via a `build/provision.sh` script that installs packages, copies files, and sets flags.
6. Export OVA, create `CHECKSUMS.txt`, write README, and perform the testing checklist.

(That recipe is conceptual — I’ve intentionally avoided giving exploit steps or commands for exploitation because the goal here is to teach how to *build* challenges, not to provide exploit recipes.)

---

# Legal & ethical reminder

Publishing intentionally vulnerable VMs is legitimate educational practice when done responsibly — but **never** include real malware, live C2, or tools/configurations that let the VM be used as a pivot to attack other systems. Always include safe network settings and clear documentation. HTB and VulnHub both expect authors to respect these boundaries. ([Hack The Box][5])

[1]: https://www.vulnhub.com/resources/ "Resources"
[2]: https://falconspy.org/posts/Creating-Vulnhub-Boxes/ "Creating Boxes for Vulnhub"
[3]: https://blog.techorganic.com/2013/12/10/creating-a-virtual-machine-hacking-challenge/ "Creating a virtual machine hacking challenge"
[4]: https://donavan.sg/blog/index.php/2019/03/28/building-vulnerable-machines-part-1-an-easy-oscp-like-machine/ "Building Vulnerable Machines: Part 1 — An Easy OSCP-like ..."
[5]: https://www.hackthebox.com/blog/building-your-first-htb-machine "Building your first HTB Machine: A beginner's guide"
[6]: https://www.vulnhub.com/entry/brainpan-3%2C121/ "Brainpan: 3"
[7]: https://donavan.sg/blog/index.php/2019/04/06/building-vulnerable-machines-part-2-a-torment-of-a-journey/ "Building Vulnerable Machines: Part 2 — A TORMENT of a ..."
[8]: https://kavigihan.medium.com/creating-vulnerable-machines-beginner-guide-fbddc835949d "Creating Vulnerable Machines: Beginner Guide"
[9]: https://www.youtube.com/watch?v=1VDA2-W2d40 "How to Build a Vulnerable Machine"
[10]: https://falconspy.medium.com/ "FalconSpy – Medium"
