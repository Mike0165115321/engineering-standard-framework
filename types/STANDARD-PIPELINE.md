# STANDARD-PIPELINE

> สำหรับระบบ Pipeline-heavy: AI Agent workflow, job processing, data pipeline
> **Family:** Pipeline-heavy — Flow Orchestration > Data Integrity, Logic-first

## Architecture

### Layer Flow (บังคับ)
```
Workflow (Orchestrator) → Node (Step) → Tool (Atomic Action)
```

### Layer Rules
| Layer | หน้าที่ | ห้าม |
|-------|--------|------|
| Workflow | orchestrate nodes, manage state, routing | มี business logic per step |
| Node | execute single step, call tool(s) | จัดการ state workflow |
| Tool | atomic action (API call, DB write, file op) | มี workflow logic |

### Seam & Adapter Concept
- **Seam** = จุดที่ interface แทรกได้ (เปลี่ยน behavior ได้)
- **Adapter** = implementation ที่สอดเข้า seam
- 1 adapter = hypothetical seam (อาจเปลี่ยน)
- 2 adapters = real seam (ต้องมี interface)
- Rule of Three: มี 3 instance ก่อน abstract

### State Machine
- Pipeline ไม่ใช่ linear flow — ใช้ state machine
- แต่ละ node รับ state → process → return state
- Workflow ตัดสินใจ routing จาก state

### Tool Registration
- Tool ต้อง register กับ registry
- 1 tool = 1 atomic action
- Tool ห้ามรู้จักกันเอง

## Coming Soon

- [ ] Folder structure มาตรฐาน
- [ ] Workflow definition pattern
- [ ] Node patterns
- [ ] Tool registration + interface
- [ ] State management
