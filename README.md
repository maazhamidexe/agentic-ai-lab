# PRD.md — Agentic Boundary Lab  
## Project: Swarm-Based Doctor Appointment Scheduler (LangGraph Agents)

---

## 1. Problem Statement

### Industry Vertical
**Healthcare**

### Background
In an industrial healthcare setting, appointment scheduling is a multi-step operational workflow, not a simple conversational task. Clinics receive appointment requests from multiple channels (mobile apps, admin dashboards, emails, and messaging platforms). Traditional chatbots fail because scheduling requires validation, policy checks, conflict resolution, and database updates.

### Core Bottleneck
- Manual scheduling causes double bookings and delays  
- Basic chatbots lack access control and deterministic workflows  
- Sensitive medical data requires strict execution boundaries  

### Problem to Solve
Design an **agentic system** that can:
- Perceive information from multiple sources
- Reason through scheduling constraints
- Execute safe, auditable actions via tools  

This problem cannot be solved with a single LLM response.

---

## 2. Selected Agent Pattern

### Swarm of Agents
This lab uses a **Swarm of Specialized Agents** coordinated using **LangGraph**, where each agent has a narrow responsibility and operates within strict boundaries.

---

## 3. Perceive — Data & Knowledge Sources

### Knowledge Sources
- Hospital appointment policy PDFs
- Doctor schedules (SQL database)
- Patient records database
- Internal clinic wiki (insurance rules)
- Scheduling and notification APIs

### Perception Capabilities
- Extract patient intent and preferred time
- Retrieve doctor availability
- Load policy constraints for appointment rules

---

## 4. Reason — LangGraph-Based Planning

### LangGraph Role
LangGraph orchestrates multi-step reasoning using explicit state transitions and conditional logic.

### Reasoning Nodes
- Input Parsing Node
- Patient Validation Node
- Doctor Availability Node
- Constraint Evaluation Node
- Conflict Resolution Node
- Approval & Escalation Node

### Reasoning Flow
1. Parse appointment request  
2. Validate patient information  
3. Retrieve doctor schedules  
4. Evaluate constraints (specialty, insurance, time)  
5. Generate structured execution plan  
6. Route to execution or human escalation  

LangGraph ensures deterministic control and prevents uncontrolled LLM behavior.

---

## 5. Execute — Tool & Action Inventory

### Action Tools (Python Functions)

#### Scheduling Tools
- `query_doctor_availability(doctor_id)`
- `create_appointment(patient_id, slot)`
- `cancel_appointment(appointment_id)`

#### Data Tools
- `query_sql(query)`
- `fetch_patient_record(patient_id)`
- `log_event(event_data)`

#### Communication Tools
- `send_sms_notification()`
- `send_email_confirmation()`

> The LLM never directly accesses databases or APIs.  
> All external interactions are performed through verified tools.

---

## 6. Swarm Agent Roles

### 1. Patient Intake Agent
- Extracts patient details
- Validates required fields

### 2. Availability Reasoning Agent
- Analyzes doctor schedules
- Proposes valid time slots

### 3. Compliance & Validation Agent
- Enforces appointment policies
- Checks insurance constraints

### 4. Execution Agent
- Calls external tools
- Writes to scheduling systems

### 5. Supervisor Agent
- Maintains global state
- Handles retries and escalation

---

## 7. User Personas

### Primary Persona — Hospital Reception Manager
- Needs reduced manual workload
- Requires reliable scheduling
- Values auditability

### Secondary Persona — Patient
- Wants fast, accurate booking
- Needs confirmations
- Expects privacy and compliance

### Technical Persona — DevOps Engineer
- Maintains LangGraph workflows
- Monitors execution logs
- Controls tool boundaries

---

## 8. Success Metrics

### Operational Metrics
- 40% reduction in manual scheduling
- Less than 2% booking conflicts
- Average booking time under 20 seconds

### Technical Metrics
- >95% successful tool execution
- Zero unauthorized database access
- Clear LangGraph state logs

### User Experience Metrics
- >98% confirmation delivery rate
- Reduced human intervention cases

---

## 9. Agentic Boundary Definition

- LLMs reason, tools execute
- LangGraph enforces flow control
- No direct DB or API access by LLMs
- All actions are auditable
- Human escalation for uncertain cases

---

## 10. Architecture Diagram Description

### Components
- Patient Interface (Web/Mobile/Admin)
- LangGraph Orchestrator
- Swarm Agent Layer
- Python Tool Execution Layer
- Knowledge Sources (Docs, DBs, APIs)
- Notification Services

### Data Flow
User Request → Intake Agent → LangGraph Planner → Validation Agent → Execution Agent → External Systems → Confirmation

---

## 11. Future Enhancements
- Emergency triage agent
- Voice-based appointment scheduling
- Predictive slot recommendations
- Multi-clinic routing logic

---

**End of PRD**
# PRD.md — Agentic Boundary Lab  
## Project: Swarm-Based Doctor Appointment Scheduler (LangGraph Agents)

---

## 1. Problem Statement

### Industry Vertical
**Healthcare**

### Background
In an industrial healthcare setting, appointment scheduling is a multi-step operational workflow, not a simple conversational task. Clinics receive appointment requests from multiple channels (mobile apps, admin dashboards, emails, and messaging platforms). Traditional chatbots fail because scheduling requires validation, policy checks, conflict resolution, and database updates.

### Core Bottleneck
- Manual scheduling causes double bookings and delays  
- Basic chatbots lack access control and deterministic workflows  
- Sensitive medical data requires strict execution boundaries  

### Problem to Solve
Design an **agentic system** that can:
- Perceive information from multiple sources
- Reason through scheduling constraints
- Execute safe, auditable actions via tools  

This problem cannot be solved with a single LLM response.

---

## 2. Selected Agent Pattern

### Swarm of Agents
This lab uses a **Swarm of Specialized Agents** coordinated using **LangGraph**, where each agent has a narrow responsibility and operates within strict boundaries.

---

## 3. Perceive — Data & Knowledge Sources

### Knowledge Sources
- Hospital appointment policy PDFs
- Doctor schedules (SQL database)
- Patient records database
- Internal clinic wiki (insurance rules)
- Scheduling and notification APIs

### Perception Capabilities
- Extract patient intent and preferred time
- Retrieve doctor availability
- Load policy constraints for appointment rules

---

## 4. Reason — LangGraph-Based Planning

### LangGraph Role
LangGraph orchestrates multi-step reasoning using explicit state transitions and conditional logic.

### Reasoning Nodes
- Input Parsing Node
- Patient Validation Node
- Doctor Availability Node
- Constraint Evaluation Node
- Conflict Resolution Node
- Approval & Escalation Node

### Reasoning Flow
1. Parse appointment request  
2. Validate patient information  
3. Retrieve doctor schedules  
4. Evaluate constraints (specialty, insurance, time)  
5. Generate structured execution plan  
6. Route to execution or human escalation  

LangGraph ensures deterministic control and prevents uncontrolled LLM behavior.

---

## 5. Execute — Tool & Action Inventory

### Action Tools (Python Functions)

#### Scheduling Tools
- `query_doctor_availability(doctor_id)`
- `create_appointment(patient_id, slot)`
- `cancel_appointment(appointment_id)`

#### Data Tools
- `query_sql(query)`
- `fetch_patient_record(patient_id)`
- `log_event(event_data)`

#### Communication Tools
- `send_sms_notification()`
- `send_email_confirmation()`

> The LLM never directly accesses databases or APIs.  
> All external interactions are performed through verified tools.

---

## 6. Swarm Agent Roles

### 1. Patient Intake Agent
- Extracts patient details
- Validates required fields

### 2. Availability Reasoning Agent
- Analyzes doctor schedules
- Proposes valid time slots

### 3. Compliance & Validation Agent
- Enforces appointment policies
- Checks insurance constraints

### 4. Execution Agent
- Calls external tools
- Writes to scheduling systems

### 5. Supervisor Agent
- Maintains global state
- Handles retries and escalation

---

## 7. User Personas

### Primary Persona — Hospital Reception Manager
- Needs reduced manual workload
- Requires reliable scheduling
- Values auditability

### Secondary Persona — Patient
- Wants fast, accurate booking
- Needs confirmations
- Expects privacy and compliance

### Technical Persona — DevOps Engineer
- Maintains LangGraph workflows
- Monitors execution logs
- Controls tool boundaries

---

## 8. Success Metrics

### Operational Metrics
- 40% reduction in manual scheduling
- Less than 2% booking conflicts
- Average booking time under 20 seconds

### Technical Metrics
- >95% successful tool execution
- Zero unauthorized database access
- Clear LangGraph state logs

### User Experience Metrics
- >98% confirmation delivery rate
- Reduced human intervention cases

---

## 9. Agentic Boundary Definition

- LLMs reason, tools execute
- LangGraph enforces flow control
- No direct DB or API access by LLMs
- All actions are auditable
- Human escalation for uncertain cases

---

## 10. Architecture Diagram Description

### Components
- Patient Interface (Web/Mobile/Admin)
- LangGraph Orchestrator
- Swarm Agent Layer
- Python Tool Execution Layer
- Knowledge Sources (Docs, DBs, APIs)
- Notification Services

### Data Flow
User Request → Intake Agent → LangGraph Planner → Validation Agent → Execution Agent → External Systems → Confirmation

---

## 11. Future Enhancements
- Emergency triage agent
- Voice-based appointment scheduling
- Predictive slot recommendations
- Multi-clinic routing logic

---

**End of PRD**
