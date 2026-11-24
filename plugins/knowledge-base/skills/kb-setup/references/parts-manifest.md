# Parts manifest

Every part of the master template (version 1.5), with a fixed ID; a renamed part keeps its ID. Setup maps each ID to the copy's page or database in the Template page's parts map (S1), removes what was not chosen (B1), and template updates address parts by these IDs.

Contents: business types; how to read the conditions; structure; hubs and wiki pages; Management; databases; personal space; parts inside other parts.

## Business types

| Code | Type |
|---|---|
| `agency` | Agency (marketing, creative, digital) |
| `software` | Software house |
| `erp` | ERP and CRM partner |
| `product` | Product company |
| `ecom` | E-commerce |
| `expertise` | Expertise firm (accounting, tax, legal, consulting) |

Service firms are `agency`, `software`, `erp` and `expertise`. A company that fits none gets the defaults for every business and is offered the optional parts.

## How to read the conditions

- **Always:** part of every base; setup keeps it.
- **Kept for <types>; optional otherwise:** kept for those types, offered to the rest.
- **Kept for <types>; removed otherwise:** kept for those types only, not offered to the rest.
- **Optional:** offered to every company, kept only on a yes.
- **<Module> chosen / not chosen:** follows the S5 answer.

"Where it sits" is the place in the master: for a company database, its module page under the Databases page. Names are the master's English titles.

## Structure

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `handover` | Knowledge base template | Template teamspace (the page the owner duplicates) | All | Always; trashed once empty after A1 | - |
| `part-company` | Company teamspace | Under `handover` | All | Always; its three children move to the company teamspace's top level in A1, then it is trashed | - |
| `part-management` | Management teamspace | Under `handover` | All | Always; the Management wiki moves to the Management teamspace's top level in A1, then it is trashed | - |
| `part-personal` | Personal space | Under `handover` | All | Always; parked under the Template page as everyone's personal space template (B12) | - |
| `wiki-home` | 🏠 Home - \<Company> (wiki; "Home" before 1.4) | `part-company`, first | All | Always | - |
| `pg-databases` | 🗂️ Databases (plain page) | `part-company`, second | All | Always | - |
| `pg-pm` | 📌 Project management (module page: one line, tabs, its databases) | `pg-databases`, first | All | Project management chosen; without it, Projects moves to `pg-shared` and the page goes | Project management |
| `pg-crm` | 📇 CRM (module page: one line, tabs, its databases) | `pg-databases`, second | All | CRM module chosen; without it, Clients, People, Partners and Proof move to `pg-shared` and the page goes | CRM |
| `pg-shared` | 📚 Shared (plain page) | `pg-databases`, third | All | Always | - |
| `agent-instructions` | 🧭 Agent Instructions | `part-company`, third | All | Always | - |
| `template-page` | Template page | Under `agent-instructions` | All | Always | - |

## Hubs and wiki pages

Hubs are the top-level pages of `wiki-home`; wiki pages are children of their hub. "(approval)" marks pages ticked "Requires edit approval".

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `hub-company` | 🏢 Company | `wiki-home` | All | Always | - |
| `hub-customers` | 🤝 Customers and offer | `wiki-home` | All | Always | - |
| `hub-how-we-work` | ⚙️ How we work | `wiki-home` | All | Always | - |
| `hub-people` | 👥 Team ("People" before 1.5) | `wiki-home` | All | Always | - |
| `hub-money` | 💰 Money | `wiki-home` | All | Always | - |
| `hub-systems` | 🧰 Systems | `wiki-home` | All | Always | - |
| `hub-ai` | 🤖 AI | `wiki-home` | All | Always | - |
| `pg-direction` | Direction (approval) | `hub-company` | All | Always | - |
| `pg-company-card` | Company card | `hub-company` | All | Always | - |
| `pg-story` | Story | `hub-company` | All | Always | - |
| `pg-glossary` | Glossary | `hub-company` | All | Always | - |
| `pg-legal-admin` | Legal and admin duties | `hub-company` | All | Always | - |
| `pg-company-map` | Company map | `hub-company` | All | Always | - |
| `pg-professional-duties` | Professional duties | `hub-company` | `expertise` | Kept for `expertise`; removed otherwise | - |
| `pg-offer-pricing` | Offer and pricing (approval) | `hub-customers` | All | Always | - |
| `pg-customers-market` | Customers and market | `hub-customers` | All | Always | - |
| `pg-brand-voice` | Brand and voice | `hub-customers` | All | Always | - |
| `pg-marketing-channels` | Marketing channels | `hub-customers` | All | Always | - |
| `pg-support-sla` | Support and SLA | `hub-customers` | `software`, `erp`, `product` | Kept for those; optional otherwise | - |
| `pg-modules-catalogue` | Modules catalogue | `hub-customers` | `erp` | Kept for `erp`; removed otherwise | - |
| `pg-demo-scripts` | Demo scripts | `hub-customers` | `erp` | Kept for `erp`; removed otherwise | - |
| `pg-product-strategy` | Product strategy and principles | `hub-customers` | `product` | Kept for `product`; optional for `ecom`; removed otherwise | - |
| `pg-pricing-packaging` | Pricing and packaging | `hub-customers` | `product` | Kept for `product`; optional for `ecom`; removed otherwise | - |
| `pg-feedback-synthesis` | Feedback synthesis | `hub-customers` | `product` | Kept for `product`; optional for `ecom`; removed otherwise | - |
| `pg-channel-rules` | Channel rules | `hub-customers` | `ecom` | Kept for `ecom`; removed otherwise | - |
| `pg-returns` | Returns and reklamace | `hub-customers` | `ecom` | Kept for `ecom`; removed otherwise | - |
| `pg-customer-service` | Customer service playbook | `hub-customers` | `ecom` | Kept for `ecom`; removed otherwise | - |
| `pg-pricing-promotions` | Pricing and promotions | `hub-customers` | `ecom` | Kept for `ecom`; removed otherwise | - |
| `pg-seasonal-playbooks` | Seasonal playbooks | `hub-customers` | `ecom` | Kept for `ecom`; removed otherwise | - |
| `pg-operating-principles` | Operating principles (approval) | `hub-how-we-work` | All | Always | - |
| `pg-service-overviews` | Service overviews | `hub-how-we-work` | Service firms | Kept for service firms; optional otherwise | - |
| `pg-delivery-methodology` | Delivery methodology | `hub-how-we-work` | `software`, `erp`, `product` | Kept for those; optional otherwise | - |
| `pg-tech-standards` | Tech standards | `hub-how-we-work` | `software`, `erp`, `product` | Kept for those; optional otherwise | - |
| `pg-version-notes` | Version and upgrade notes | `hub-how-we-work` | `erp` | Kept for `erp`; removed otherwise | - |
| `pg-client-approval` | Client approval rules | `hub-how-we-work` | `agency` | Kept for `agency`; optional otherwise | - |
| `pg-suppliers-logistics` | Suppliers and logistics | `hub-how-we-work` | `ecom` | Kept for `ecom`; removed otherwise | - |
| `pg-catalogue-standards` | Catalogue standards | `hub-how-we-work` | `ecom` | Kept for `ecom`; removed otherwise | - |
| `pg-confidentiality-reuse` | Confidentiality and reuse | `hub-how-we-work` | `expertise` | Kept for `expertise`; removed otherwise | - |
| `pg-clauses-templates` | Clauses and templates | `hub-how-we-work` | `expertise` | Kept for `expertise`; removed otherwise | - |
| `pg-people-handbook` | People handbook | `hub-people` | All | Always | - |
| `pg-learning` | Learning | `hub-people` | - | Optional | - |
| `pg-facilities` | Facilities | `hub-people` | - | Optional | - |
| `pg-finance-rules` | Finance rules (approval) | `hub-money` | All | Always | - |
| `pg-how-money-moves` | How money moves | `hub-money` | All | Always | - |
| `pg-kpi-definitions` | KPI definitions | `hub-money` | All | Always | - |
| `pg-tools` | How we use our tools | `hub-systems` | All | Always | - |
| `pg-accounts-access` | Accounts and access | `hub-systems` | All | Always | - |
| `pg-ai-setup` | AI setup | `hub-ai` | All | Always | - |
| `pg-getting-more` | Getting more | `hub-ai` | All | Always | - |
| `pg-factories` | Factories | `hub-ai` | All | Always | - |

## Management

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `wiki-management` | 🏛️ Management (wiki) | `part-management` | All | Always | - |
| `mg-plans-numbers` | Plans and numbers | `wiki-management` | All | Always | - |
| `mg-pay` | Pay | `wiki-management` | All | Always | - |
| `mg-banking` | Banking and financing | `wiki-management` | All | Always | - |
| `mg-people-matters` | People matters | `wiki-management` | All | Always | - |
| `db-contracts` | 📜 Contracts | `wiki-management` (Records) | All | Always | - |
| `db-hiring` | 🙋 Hiring | `wiki-management` (Records) | - | Optional | - |

## Databases

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `db-projects` | 🚀 Projects | `pg-pm` | All | Always | - |
| `db-issues` | 📋 Issues | `pg-pm` | All | Project management chosen | Project management |
| `db-cycle-board` | 🏃 Cycle board | `pg-pm` | All | Project management chosen | Project management |
| `db-cycles` | ⏱️ Cycles | `pg-pm` | All | Project management chosen | Project management |
| `db-milestones` | 🏁 Milestones | `pg-pm` | All | Project management chosen | Project management |
| `db-goals` | 🎯 Goals | `pg-pm` | - | Optional | - |
| `db-clients` | 💼 Clients | `pg-crm` | All | Always | - |
| `db-deals` | 📈 Deals | `pg-crm` | All | CRM module chosen | CRM |
| `db-people` | 👤 People | `pg-crm` | All | Always | - |
| `db-partners` | 🧩 Partners | `pg-crm` | All | Always | - |
| `db-proof` | ⭐ Proof | `pg-crm` | Service firms | Kept for service firms; optional otherwise | - |
| `db-meetings` | 📅 Meetings | `pg-shared` | All | Always | - |
| `db-decisions` | ⚖️ Decisions | `pg-shared` | All | Always | - |
| `db-ideas` | 💡 Ideas | `pg-shared` | All | Always | - |
| `db-processes` | 🔁 Processes | `pg-shared` | All | Always | - |
| `db-equipment` | 💻 Equipment | `pg-shared` | - | Optional | - |
| `db-events` | 🎟️ Events | `pg-shared` | - | Optional | - |

## Personal space

Under `part-personal`, whose three children are Home - \<Name>, Agent Instructions - \<Name> and Databases, in that order. Each person's copy keeps what they use (per-person steps, P3).

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `ps-my-wiki` | 🏠 Home - \<Name> (wiki; "My wiki" before 1.4) | `part-personal`, first | Everyone | Always | - |
| `ps-agent-instructions` | Agent Instructions - \<Name> | `part-personal`, second | Everyone | Always | - |
| `ps-databases` | 🗂️ Databases (plain page) | `part-personal`, third | Everyone | Always | - |
| `ps-notes` | 📝 Notes | `ps-databases` | Everyone | Always | - |
| `ps-projects` | 🎯 Projects | `ps-databases` | Owners | Kept for owners; optional for others | - |
| `ps-reading` | 📖 Reading | `ps-databases` | - | Optional | - |
| `ps-people` | 🫂 People | `ps-databases` | - | Optional | - |
| `ps-tasks` | ✅ Tasks | `ps-databases` | - | Optional | - |
| `ps-area-ai` | 🤖 AI (starter area) | `ps-my-wiki`, first area | Everyone | Always; the person may rename it to one of their own areas | - |
| `ps-factories` | Factories (the person's scheduled jobs) | `ps-area-ai` | Everyone | Always | - |
| `ps-one-to-one` | 1:1 - \<Name> | `ps-my-wiki` | Managers | Kept for people who manage others; removed otherwise | - |

## Parts inside other parts

Properties, views, template sections and text that belong to a module or business type. B1 removes them with their part.

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `home-db-links` | A database's mention in the Databases columns of Home - \<Company> | `wiki-home` | All | With its database | - |
| `home-modules` | The Modules row of Home - \<Company>: one column per module page | `wiki-home` | All | A module's column goes with its module page | - |
| `home-now-cycle` | "Current cycle" tab in the At a glance tabs | `wiki-home` | All | Project management chosen | Project management |
| `home-now-deals` | "Deals today" tab in the At a glance tabs | `wiki-home` | All | CRM module chosen | CRM |
| `ps-home-reading` | "Reading" tab in the My records tabs | `ps-my-wiki` | - | With `ps-reading` | - |
| `props-projects-pm` | Issues, Milestones, Progress, Health, Priority properties; Issues layout tab | `db-projects` | All | Project management chosen | Project management |
| `rec-issues` | "Open issues" tab in the Records tabs | `hub-how-we-work` | All | Project management chosen | Project management |
| `ai-pm` | "Project management for agents" subpage of Agent Instructions and its line under "Specific work"; Issues, Cycles, Milestones table rows; "with project management, each piece of work is an Issue in its Project" in Where things go | `agent-instructions` | All | Project management chosen | Project management |
| `props-clients-crm` | Do not contact, Health, Deals, Open deal value, Open renewal properties; Watch and Renewals views; Deals layout tab | `db-clients` | All | CRM module chosen | CRM |
| `props-people-crm` | Warmth and Do not contact properties; Roles option Connector; By warmth, Reach out and Connectors views | `db-people` | All | CRM module chosen | CRM |
| `props-meetings-crm` | Deal property | `db-meetings` | All | CRM module chosen | CRM |
| `rec-deals` | "Open deals" tab in the Records tabs | `hub-customers` | All | CRM module chosen | CRM |
| `ai-sales` | "Sales for agents" subpage of Agent Instructions and its line under "Specific work"; Deals table row; Clients' Watch and Renewals links; People's By warmth and Connectors links; "A sales ask, upsell or renewal" row in Where things go | `agent-instructions` | All | CRM module chosen | CRM |
| `prop-crm-record` | CRM record property | `db-clients`, `db-people` | All | CRM module not chosen | CRM |
| `rec-proof` | "Public proof" tab in the Records tabs | `hub-customers` | Service firms | With `db-proof` | - |
| `mgmt-open-hiring` | "Open hiring" heading and its linked view | `wiki-management` | - | With `db-hiring` | - |
| `tpl-client-billing` | "Billing" under What we do for them, in the Client template | `db-clients` | Service firms | Kept for service firms; optional otherwise | - |
| `tpl-client-confidentiality` | "Constraints > Confidentiality and reuse", in the Client template | `db-clients` | `expertise` | Kept for `expertise`; removed otherwise | - |
| `tpl-client-environments` | "Environments and access" under Where things live, in the Client template | `db-clients` | `software`, `erp`, `product` | Kept for those; optional otherwise | - |
| `tpl-client-ads` | "Ad accounts" and "Analytics and dashboards" under Where things live, in the Client template | `db-clients` | `agency` | Kept for `agency`; optional otherwise | - |
| `tpl-partner-vendor` | "Vendor details" under Terms, in the Partner template | `db-partners` | `erp` | Kept for `erp`; removed otherwise | - |
