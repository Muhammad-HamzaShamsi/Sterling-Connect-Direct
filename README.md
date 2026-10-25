# 🔁 IBM Sterling Connect:Direct

![IBM Sterling](https://img.shields.io/badge/IBM-Sterling_Connect:Direct-052FAD?logo=ibm&logoColor=white)
![MFT](https://img.shields.io/badge/Managed-File_Transfer-success)

An installation guide and overview presentation for **IBM Sterling Connect:Direct**, IBM's secure, high-volume, peer-to-peer file transfer solution.

| Document | Contents |
|----------|----------|
| 📄 [Installation Procedure (PDF)](Stering%20Connect%20Direct%20Installation%20Procedure.pdf) | Step-by-step installation |
| 📊 [IBM Sterling Connect:Direct (PPTX)](IBM%20Sterling%20ConnectDirect.pptx) | Overview presentation: architecture, features, use cases |

## What is Connect:Direct?

Formerly **NDM (Network Data Mover)**, Connect:Direct moves large batch files reliably between organisations and systems. It is far more secure and controllable than FTP.

### Key features

- ⚡ **High performance** with **checkpoint/restart**, so interrupted transfers resume
- 🔐 **Security & compliance:** TLS, Secure+ and strong authentication, aligned with PCI DSS, HIPAA and GDPR
- ⏰ **Automation:** built-in scheduling and *Process* scripts
- 🖥️ **Cross-platform:** Windows, Linux, UNIX and z/OS mainframes
- ♻️ **Error handling:** automatic retries, notifications and detailed statistics logs
- 🧩 **IBM ecosystem:** integrates with Sterling File Gateway and Sterling Control Center

### Architecture

- **Peer-to-peer nodes:** files go directly between nodes, with no intermediary server
- **Separate control and data channels** for efficiency and security
- **Netmap** defines the partner nodes; **user proxies** map remote users to local IDs

### Use cases

Banking (payment and statement files) · Retail (orders, inventory, shipping) · Telecoms (billing and usage logs) · Manufacturing (supply-chain data)

## Quick reference (UNIX CLI)

```bash
direct                                  # open the CLI
submit file=copy.cdp;                   # submit a Process
select process;                         # running / queued processes
select statistics pnumber=<n>;          # result of a transfer
```

Sample Process (`copy.cdp`):

```text
COPYFILE PROCESS SNODE=PARTNER_NODE
STEP1 COPY FROM (FILE=/data/out/report.csv PNODE)
           TO   (FILE=/data/in/report.csv  SNODE DISP=RPL)
PEND
```
