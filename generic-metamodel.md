# Generic Metamodel

![Generic Metamodel Hierarchy](/images/generic-metamodel.png)

## Overview

The **Generic Metamodel** provides a common way to organize architecture concepts. It can be understood through three fundamental questions:

- **Who or what exists?** → Structure
- **What do they do?** → Behavior
- **What triggers or influences them?** → Events

The model provides generic building blocks that can be used across architecture layers, including the Business, Application, Technology, and Physical layers.

---

## 1. Element: The Root Concept

**Element:** Any concept that can be represented in an architecture model.

An Element is the parent category from which all other metamodel concepts are derived.

**Simple question:** *What kind of thing am I modeling?*

**Examples:**

- Customer
- Application
- Server
- Business Process
- API Service
- Order

---

## 2. Structure Elements: The Things That Exist

**Structure Elements:** The entities that exist within the enterprise architecture. Structure Elements represent things that can perform behavior or be affected by behavior.

**Simple question:** *What exists?*

**Examples:**

- Employee
- Customer
- CRM Application
- Database
- Server
- Business Object

Structure Elements are divided into the following categories:

```text
Structure Element
├── Active Structure Element
└── Passive Structure Element
```

---

## 3. Active Structure Elements: The Actors

**Active Structure Elements:** The subjects that perform behavior, provide services, or initiate actions. Active Structure Elements represent the **who or what acts**.

**Simple question:** *Who or what performs the work?*

**Examples:**

- Business Actor
- Business Role
- Application Component
- Device
- Node

### Real-life examples

| Situation | Active Structure Element |
|---|---|
| A sales employee performs sales activities | Business Actor |
| An SAP system processes information | Application Component |
| An Azure virtual machine runs software | Node |
| A network device transports traffic | Device |

> **Easy memory aid:** Active Structure = the doer.

### 3.1 External Active Structure Elements

**External Active Structure Elements:** Active elements that expose an externally visible point of interaction to their environment.

**Simple question:** *How can other elements interact with the actor?*

Depending on the architecture layer, examples can include:

- Business Interface
- Application Interface
- Technology Interface

**Example:**

A customer may access an organization through a customer-service interface instead of interacting directly with the employees, applications, or devices behind that interface.

> **Easy memory aid:** External Active Structure = the accessible face or interaction point.

### 3.2 Internal Active Structure Elements

**Internal Active Structure Elements:** Active elements that perform or are responsible for the actual work inside the architecture.

**Simple question:** *What is internally doing the work?*

Depending on the architecture layer, examples can include:

- Business Actor
- Business Role
- Business Collaboration
- Application Component
- Application Collaboration
- Node
- Device
- System Software
- Technology Collaboration

**Example:**

Behind a customer-service interface, employees, application components, and infrastructure nodes may work together to handle customer requests.

> **Easy memory aid:** Internal Active Structure = the internal doer or implementation.

---

## 4. Passive Structure Elements: The Things Being Worked On

**Passive Structure Elements:** Objects on which behavior is performed. Passive Structure Elements can be created, used, changed, stored, transported, or consumed by active elements.

**Simple question:** *What is the work performed on?*

**Examples:**

- Business Object
- Data Object
- Artifact
- Material

### Real-life examples

| Activity | Passive Structure Element |
|---|---|
| Process an order | Order |
| Update customer information | Customer Record |
| Read or modify a document | Document |
| Deploy a software package | Artifact |
| Move physical goods | Material |

> **Easy memory aid:** Passive Structure = the thing being acted upon.

---

## 5. Behavior Elements: The Things That Happen

**Behavior Elements:** Units of activity performed by active structure elements. Behavior Elements describe the **what happens** in the architecture.

**Simple question:** *What work is happening?*

**Examples:**

- Business Process
- Business Function
- Application Function
- Technology Process
- Service

### Real-life examples

| Active Structure Element | Behavior Element |
|---|---|
| Sales employee | Sell Product |
| CRM application | Validate Customer |
| Server or node | Execute Request |

> **Easy memory aid:** Behavior = the action or work.

Behavior Elements are divided into the following categories:

```text
Behavior Element
├── External Behavior Element
├── Internal Behavior Element
└── Event
```

---

## 6. External Behavior Elements: The Exposed Services

**External Behavior Elements:** Behavior that is externally visible and can be used or consumed by other elements.

In ArchiMate, externally visible behavior is generally represented by a **service**.

**Simple question:** *What useful behavior is offered to others?*

**Examples:**

- Business Service
- Application Service
- Technology Service

### Examples

| Internal Behavior | External Behavior |
|---|---|
| Order-processing process | Order Processing Service |
| Authentication function | Authentication Service |
| Data-management function | Data Service |
| Infrastructure monitoring | Monitoring Service |

> **Easy memory aid:** External Behavior = what others can use or experience.

---

## 7. Internal Behavior Elements: How the Work Is Performed

**Internal Behavior Elements:** Activities performed inside an organization, application, or technology environment. Internal Behavior Elements realize or implement externally visible services.

**Simple question:** *How is the work actually performed?*

**Examples:**

- Business Process
- Business Function
- Business Interaction
- Application Function
- Application Process
- Application Interaction
- Technology Function
- Technology Process
- Technology Interaction

**Example:**

An externally visible **Order Processing Service** may be realized through several internal behaviors:

1. Validate Customer
2. Validate Order
3. Check Inventory
4. Create Order
5. Generate Invoice
6. Send Confirmation

> **Easy memory aid:** Internal Behavior = the implementation of the work.

---

## 8. Events: The Triggers

**Event:** Something that happens at a particular moment and may trigger, interrupt, or influence behavior.

An Event is classified as a Behavior Element because it represents an occurrence rather than a person, system, object, or other structural thing.

**Simple question:** *What causes something to start, stop, or change?*

**Examples:**

- Customer places an order
- Invoice received
- User login requested
- System failure detected
- Payment completed

### Trigger examples

| Event | Behavior Triggered or Influenced |
|---|---|
| Order Received | Order Processing Process |
| Login Requested | Authentication Function |
| Incident Raised | Support Process |
| Payment Received | Order Fulfilment Process |

> **Easy memory aid:** Event = the trigger or occurrence.

---

## Complete Generic Metamodel Hierarchy

```text
Element
├── Structure Element: What exists?
│   ├── Active Structure Element: Who or what performs behavior?
│   │   ├── External Active Structure Element
│   │   │   └── How can others access or interact with the active element?
│   │   └── Internal Active Structure Element
│   │       └── What internally performs or is responsible for the behavior?
│   └── Passive Structure Element
│       └── What is used, created, changed, stored, or consumed?
└── Behavior Element: What happens?
    ├── External Behavior Element
    │   └── What service is offered to others?
    ├── Internal Behavior Element
    │   └── How is the behavior performed internally?
    └── Event
        └── What occurrence triggers or influences behavior?
```

---

## Complete Example: Online Order Management

### Active Structure Elements: Who or what acts?

- Customer Service Agent
- Order Management Application
- Database Server

### External Active Structure Elements: Where does interaction occur?

- Customer Portal Interface
- Order API

### Internal Active Structure Elements: What performs the work internally?

- Customer Service Role
- Order Management Application Component
- Database Node

### Passive Structure Elements: What is acted upon?

- Order
- Customer Record
- Invoice
- Payment Record

### Internal Behavior Elements: How is the work performed?

- Validate Order
- Check Inventory
- Create Order
- Generate Invoice
- Update Customer Record

### External Behavior Elements: What is offered?

- Order Processing Service
- Payment Service
- Order Status Service

### Events: What triggers or influences the work?

- Customer Submits Order
- Payment Received
- Inventory Becomes Unavailable
- Order Shipped

---

## How the Elements Work Together

A typical architecture flow can be read as follows:

1. An **Event** occurs.
2. The Event triggers an **Internal Behavior Element**.
3. An **Internal Active Structure Element** performs the behavior.
4. The behavior reads, creates, changes, or uses a **Passive Structure Element**.
5. The internal behavior realizes an **External Behavior Element**, such as a service.
6. Other actors or systems access the architecture through an **External Active Structure Element**, such as an interface.

### In one sentence

> **Active Structure Elements perform Behavior Elements on Passive Structure Elements, often triggered by Events. External elements describe what is exposed or accessible, while internal elements describe how the architecture is implemented.**

---

## Quick Reference

| Element Type | Simple Meaning | Guiding Question |
|---|---|---|
| Element | Any concept in the model | What kind of thing am I modeling? |
| Structure Element | Something that exists | What exists? |
| Active Structure Element | A performer of behavior | Who or what acts? |
| External Active Structure Element | An externally accessible interaction point | Where can others interact? |
| Internal Active Structure Element | An internal performer or responsible entity | What internally performs the work? |
| Passive Structure Element | An object affected or used by behavior | What is acted upon? |
| Behavior Element | An action or occurrence | What happens? |
| External Behavior Element | A service exposed to others | What is offered? |
| Internal Behavior Element | Work performed internally | How is the work performed? |
| Event | A trigger or significant occurrence | What causes something to happen? |
