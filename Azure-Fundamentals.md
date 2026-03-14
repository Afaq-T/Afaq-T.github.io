# Azure Fundamentals – My Learning Journey

This page summarizes what I learned about Azure during Week 3 of my cloud and networking roadmap.
I covered AZ-900 level concepts including cloud computing, Azure hierarchy, core services, identity, governance, and pricing.

---

## ☁️ What is Cloud Computing?

Cloud computing means using someone else's computers (servers, storage, networking) over the internet instead of buying and maintaining your own physical hardware. You only pay for what you use.

### The Three Service Models

| Model | What the Provider Gives You | Example |
| --- | --- | --- |
| **IaaS** (Infrastructure as a Service) | Virtual machines and networking — you manage the OS and apps | Azure Virtual Machines |
| **PaaS** (Platform as a Service) | A complete platform — you just deploy your application code | Azure App Service |
| **SaaS** (Software as a Service) | A ready-to-use application — you just open and use it | Microsoft 365 |

---

## 🏗️ Azure Hierarchy — How Azure is Organized

Azure is organized in a four-level hierarchy from top to bottom:

```
Tenant
└── Subscription
    └── Resource Group A        Resource Group B
        ├── Virtual Machine         ├── Virtual Machine
        ├── Storage Account         └── VNet
        └── VNet
```

| Level | What it is |
| --- | --- |
| **Tenant** | Your organization's identity in Azure — sits at the very top |
| **Subscription** | Billing container — all costs inside are billed together |
| **Resource Group** | Logical folder for organizing related resources (e.g. by department) |
| **Resource** | The actual thing you create — VM, Storage Account, VNet, Database |

**Why this matters:**
- **Billing** is tracked at the Subscription level
- **Access control** (RBAC) can be assigned at any level and inherits downward

---

## 🗺️ Azure Regions and Availability Zones

- A **Region** is a geographic area with one or more data centers — examples: East US, West Europe, Southeast Asia
- An **Availability Zone** is a physically separate data center within the same region with independent power and cooling
- Deploying across zones protects against single data center failures

---

## ⚙️ The Six Core Azure Service Categories

| Category | Services |
| --- | --- |
| **Compute** | Virtual Machines, App Service, Azure Functions |
| **Storage** | Blob Storage, Disk Storage, File Storage |
| **Networking** | VNet, Load Balancer, NSG (Network Security Group) |
| **Identity** | Entra ID, RBAC, MFA |
| **Monitoring** | Azure Monitor, Log Analytics |
| **Security** | Defender for Cloud, Key Vault |

---

## 💰 Azure Pricing Models

**Consumption Model (Pay-as-you-go)**
You pay only for what you actually use. Stop a VM and you stop paying for compute.

**Free Tier**
- Always-free services with usage limits (example: 5GB Blob Storage per month)
- Services free for 12 months for new accounts (example: 750 hours of a B1S VM per month)
- $200 credit for new accounts for the first 30 days

**Azure for Students**
$100 in free credits valid for 12 months — no credit card required.

**SLA — Service Level Agreement**

| SLA % | Downtime per Month | Downtime per Year |
| --- | --- | --- |
| 99% | ~7.2 hours | ~3.65 days |
| 99.9% | ~43 minutes | ~8.7 hours |
| 99.95% | ~21 minutes | ~4.4 hours |
| 99.99% | ~4 minutes | ~52 minutes |

---

## 🔐 Entra ID — Identity and Access Management

**Entra ID** (formerly Azure Active Directory) is Microsoft's cloud identity service. Every organization using Azure or Microsoft 365 runs on Entra ID.

### Key Concepts

**Users** — Individual accounts in Entra ID with credentials and profile details.

**Groups** — Collections of users. Assign permissions to groups instead of individuals. When someone joins, add them to the group and they get all permissions automatically.

**MFA — Multi Factor Authentication**
Requires two or more verification factors:
- Something you **KNOW** — password or PIN
- Something you **HAVE** — phone app or SMS code
- Something you **ARE** — fingerprint or face scan

**RBAC — Role Based Access Control**

| Role | What it can do |
| --- | --- |
| **Owner** | Full access including managing other users' access |
| **Contributor** | Create and manage resources but cannot manage access |
| **Reader** | View resources only — cannot make any changes |
| **User Access Administrator** | Manage who has access but cannot touch resources |

> **Principle of Least Privilege** — Always assign the minimum access needed. If someone only needs to view resources, give them Reader — not Contributor or Owner.

---

## 🛡️ Azure Governance

**Azure Policy**
Enforces organizational rules across your entire Azure environment automatically.
- Example: All resources must be deployed only in East US region
- Example: All VMs must have a specific cost-tracking tag

**Resource Locks**
Protects important resources from accidental deletion or modification.

| Lock Type | What it does |
| --- | --- |
| **ReadOnly** | Nobody can modify or delete the resource |
| **Delete** | Nobody can delete the resource but it can still be modified |

**Cost Management**
Monitors and analyzes your Azure spending. Set budgets, create alerts, and identify unused resources that are wasting money.

---

## 🗂️ Azure Architecture Diagrams

### Azure Hierarchy Diagram
![Azure Hierarchy Diagram](/images/Azure-Heirarchy.drawio.png)

### Azure Service Map
![Azure Service Map](/images/6-Azure-Services.drawio.png)

---

## 🧪 Key Concepts Cheatsheet

- **IaaS** = Infrastructure as a Service → Virtual Machines (you manage the OS)
- **PaaS** = Platform as a Service → App Service (you manage only your app)
- **SaaS** = Software as a Service → Microsoft 365 (you manage nothing)
- **99.9% SLA** = ~43 minutes downtime per month, ~8.7 hours per year
- **Deny rule always overrides Allow** in NSGs and RBAC — always check for Deny assignments first
- **Tenant** is the top of the hierarchy — your organization's identity
- **Resource Group** = logical folder for organizing resources by department or project
- **Reader** = view only | **Contributor** = create/manage | **Owner** = full control
- **MFA factors**: something you KNOW + something you HAVE + something you ARE
- **Resource Lock** prevents accidental deletion of critical resources

---

## 📝 Week 3 Quiz Results

I tested my knowledge with 30 AZ-900-style questions covering all Week 3 topics.

**Score: 27/30 — 90%**

| Round | Topic | Score |
| --- | --- | --- |
| Round 1 | Cloud Basics | 4/5 |
| Round 2 | Azure Services | 5/5 |
| Round 3 | Governance & Security | 5/5 |
| Round 4 | MFA & Entra ID | 5/5 |
| Round 5 | Pricing & Regions | 4/5 |
| Round 6 | Mixed Hard | 4/5 |

---

## 💡 What I Learned

- Cloud computing removes the need to own physical hardware — you rent what you need and pay only for what you use
- The Azure hierarchy (Tenant → Subscription → Resource Group → Resource) controls both billing and access
- RBAC is the correct way to control who can do what — always assign to groups, not individuals
- MFA is non-negotiable in 2026 — every organization requires it and every support engineer must understand it
- Resource Locks and Azure Policy are how organizations prevent mistakes and enforce standards
- Deny always overrides Allow — this is the most important NSG and RBAC rule to remember

---

I now understand Azure fundamentals at AZ-900 level — enough to explain cloud concepts, navigate the Azure portal, and answer identity and governance questions in technical interviews.

This site is open source. [Improve this page](https://github.com/Afaq-T/Afaq-T.github.io/edit/main/azure-fundamentals.md).
