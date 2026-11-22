# Parts manifest

Every part of the master template (version 1.0), with a fixed ID. Setup maps each ID to the copy's page or database in the Template page's parts map (S1), removes what was not chosen (B1), and template updates address parts by these IDs.

Contents: business types; how to read the conditions; structure; Home hubs and wiki pages; Management; databases; personal space; parts inside other parts.

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

"Where it sits" is the place in the master. Names are the master's English titles.

## Structure

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `handover` | Knowledge base template | Template teamspace (the page the owner duplicates) | All | Always; trashed once empty after A1 | - |
| `part-company` | Company teamspace | Under `handover` | All | Always; its contents move to the company teamspace in A1, then it is trashed | - |
| `part-management` | Management teamspace | Under `handover` | All | Always; its contents move to the Management teamspace in A1, then it is trashed | - |
| `part-personal` | Personal space | Under `handover` | All | Always; parked under the Template page as everyone's personal space template (B12) | - |
| `wiki-home` | Home (wiki) | `part-company` | All | Always | - |
| `agent-instructions` | Agent Instructions | `part-company` | All | Always | - |
| `template-page` | Template page | Under `agent-instructions` | All | Always | - |

## Home hubs and wiki pages

Hubs are the top-level pages of `wiki-home`; wiki pages are children of their hub. "(approval)" marks pages ticked "Requires edit approval".

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `hub-company` | 🏢 Company | `wiki-home` | All | Always | - |
| `hub-customers` | 🤝 Customers and offer | `wiki-home` | All | Always | - |
| `hub-how-we-work` | ⚙️ How we work | `wiki-home` | All | Always | - |
| `hub-people` | 👥 People | `wiki-home` | All | Always | - |
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
| `db-contracts` | 📜 Contracts | `part-management` | All | Always | - |
| `db-hiring` | 🙋 Hiring | `part-management` | - | Optional | - |

## Databases

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `db-projects` | 🚀 Projects | `part-company` | All | Always | - |
| `db-meetings` | 📅 Meetings | `part-company` | All | Always | - |
| `db-clients` | 💼 Clients | `part-company` | All | Always | - |
| `db-people` | 👤 People | `part-company` | All | Always | - |
| `db-processes` | 🔁 Processes | `part-company` | All | Always | - |
| `db-partners` | 🧩 Partners | `part-company` | All | Always | - |
| `db-decisions` | ⚖️ Decisions | `part-company` | All | Always | - |
| `db-ideas` | 💡 Ideas | `part-company` | All | Always | - |
| `db-issues` | 📋 Issues | `part-company` | All | Project management chosen | Project management |
| `db-cycle-board` | 🏃 Cycle board | `part-company` | All | Project management chosen | Project management |
| `db-cycles` | ⏱️ Cycles | `part-company` | All | Project management chosen | Project management |
| `db-milestones` | 🏁 Milestones | `part-company` | All | Project management chosen | Project management |
| `db-deals` | 📈 Deals | `part-company` | All | CRM module chosen | CRM |
| `db-proof` | ⭐ Proof | `part-company` | Service firms | Kept for service firms; optional otherwise | - |
| `db-equipment` | 💻 Equipment | `part-company` | - | Optional | - |
| `db-events` | 🎟️ Events | `part-company` | - | Optional | - |
| `db-goals` | 🎯 Goals | `part-company` | - | Optional | - |

## Personal space

Children of `part-personal`. Each person's copy keeps what they use (per-person steps, P3).

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `ps-agent-instructions` | Agent Instructions - \<Name> | `part-personal` | Everyone | Always | - |
| `ps-notes` | 📝 Notes | `part-personal` | Everyone | Always | - |
| `ps-projects` | 🎯 Projects | `part-personal` | Owners | Kept for owners; optional for others | - |
| `ps-my-wiki` | 📚 My wiki | `part-personal` | Everyone | Always | - |
| `ps-one-to-one` | 1:1 - \<Name> | `part-personal` | Managers | Kept for people who manage others; removed otherwise | - |
| `ps-reading` | 📖 Reading | `part-personal` | - | Optional | - |
| `ps-people` | 🫂 People | `part-personal` | - | Optional | - |
| `ps-tasks` | ✅ Tasks | `part-personal` | - | Optional | - |

## Parts inside other parts

Properties, views, template sections and text that belong to a module or business type. B1 removes them with their part.

| Part ID | Name in the master | Where it sits | Default for | Condition | Module |
|---|---|---|---|---|---|
| `props-projects-pm` | Issues, Milestones, Progress, Health, Priority properties; Issues layout tab | `db-projects` | All | Project management chosen | Project management |
| `rec-issues` | Issues line under Records | `hub-how-we-work` | All | Project management chosen | Project management |
| `ai-pm` | "Project management" section; Issues, Cycles, Milestones table rows; "with project management, each piece of work is an Issue in its Project" in Where things go | `agent-instructions` | All | Project management chosen | Project management |
| `props-clients-crm` | Do not contact, Health, Deals, Open deal value, Open renewal properties; Watch and Renewals views; Deals layout tab | `db-clients` | All | CRM module chosen | CRM |
| `props-people-crm` | Warmth and Do not contact properties; Roles option Connector; By warmth, Connectors and Do not contact views | `db-people` | All | CRM module chosen | CRM |
| `props-meetings-crm` | Deal property | `db-meetings` | All | CRM module chosen | CRM |
| `rec-deals` | Deals line under Records | `hub-customers` | All | CRM module chosen | CRM |
| `ai-sales` | "Sales" section; Deals table row; Clients' Watch and Renewals links; "A sales ask, upsell or renewal" row in Where things go | `agent-instructions` | All | CRM module chosen | CRM |
| `prop-crm-record` | CRM record property | `db-clients`, `db-people` | All | CRM module not chosen | CRM |
| `rec-proof` | Proof line under Records | `hub-customers` | Service firms | With `db-proof` | - |
| `mgmt-open-hiring` | "Open hiring" heading and its linked view | `wiki-management` | - | With `db-hiring` | - |
| `tpl-client-billing` | "Billing" under What we do for them, in the Client template | `db-clients` | Service firms | Kept for service firms; optional otherwise | - |
| `tpl-client-confidentiality` | "Constraints > Confidentiality and reuse", in the Client template | `db-clients` | `expertise` | Kept for `expertise`; removed otherwise | - |
| `tpl-client-environments` | "Environments and access" under Where things live, in the Client template | `db-clients` | `software`, `erp`, `product` | Kept for those; optional otherwise | - |
| `tpl-client-ads` | "Ad accounts" and "Analytics and dashboards" under Where things live, in the Client template | `db-clients` | `agency` | Kept for `agency`; optional otherwise | - |
| `tpl-partner-vendor` | "Vendor details" under Terms, in the Partner template | `db-partners` | `erp` | Kept for `erp`; removed otherwise | - |
