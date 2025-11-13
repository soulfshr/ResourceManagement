# Resource Management Application - UI Mockups & Wireframes

**Document Version**: 1.0
**Last Updated**: 2025-11-13
**Purpose**: Visual representation of key user interface screens

---

## Table of Contents

1. [Dashboard](#1-dashboard)
2. [Resource Booking Interface (Drag & Drop)](#2-resource-booking-interface-drag--drop)
3. [Resource View](#3-resource-view)
4. [Project View](#4-project-view)
5. [Calendar/Timeline View](#5-calendartimeline-view)
6. [Time-Off Management](#6-time-off-management)
7. [Financial Dashboard](#7-financial-dashboard)
8. [Scenario Planner](#8-scenario-planner)
9. [AI Resource Recommendations](#9-ai-resource-recommendations)

---

## 1. Dashboard

**Purpose**: Executive overview with key metrics, alerts, and quick actions
**User Role**: Manager, Administrator

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Resource Management ▼        🔔(3)  👤 John Smith (Manager)               │
├────────────────────────────────────────────────────────────────────────────┤
│  Dashboard  |  Resources  |  Projects  |  Calendar  |  Reports  |  Settings │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─ Team Utilization ──────────────────┐  ┌─ Alerts ───────────────────┐ │
│  │                                      │  │ ⚠ Over-Allocated (3)       │ │
│  │  Engineering Team      ████░ 82%    │  │   • Sarah Chen - 120%      │ │
│  │  Design Team          ███░░ 65%    │  │   • Mike Johnson - 105%    │ │
│  │  Marketing Team       █████ 95%    │  │   • Alex Rivera - 110%     │ │
│  │                                      │  │                             │ │
│  │  Overall Utilization:  ████░ 81%    │  │ 🔵 Upcoming Time-Off (5)   │ │
│  │  Green: <80%  Yellow: 80-100%       │  │   • Emma Liu (Nov 18-22)   │ │
│  │  Red: >100%                          │  │   • Carlos Martinez (Nov)  │ │
│  └──────────────────────────────────────┘  └────────────────────────────┘ │
│                                                                             │
│  ┌─ Financial Summary ──────────────────┐  ┌─ AI Recommendations ──────┐ │
│  │                                      │  │ 🤖 Suggested Actions       │ │
│  │  Budget:      $450,000               │  │                             │ │
│  │  Actual Cost: $378,500 (84%)         │  │ • Consider allocating      │ │
│  │  Revenue:     $520,000               │  │   Sarah Chen to Project X  │ │
│  │  Margin:      27.2% ▲                │  │   Match: 92%               │ │
│  │                                      │  │                             │ │
│  │  [View Full Financial Report]        │  │ • Design team under-       │ │
│  │                                      │  │   utilized (65%)           │ │
│  └──────────────────────────────────────┘  └────────────────────────────┘ │
│                                                                             │
│  ┌─ Active Projects ────────────────────────────────────────────────────┐ │
│  │                                                                       │ │
│  │  Project Alpha        ████████░ 85%     Budget: 90%    [View]       │ │
│  │  Website Redesign     ███████░░ 75%     Budget: 82%    [View]       │ │
│  │  Mobile App v2        ██████░░░ 60%     Budget: 55%    [View]       │ │
│  │                                                                       │ │
│  │  [+ New Project]                                     [View All (12)] │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                             │
│  ┌─ Capacity Heatmap (Next 8 Weeks) ────────────────────────────────────┐ │
│  │         W46   W47   W48   W49   W50   W51   W52   W01                │ │
│  │  Sarah  🟥   🟥   🟩   🟩   ⬜   🟩   🟩   🟩  (⬜ = time-off)       │ │
│  │  Mike   🟥   🟨   🟨   🟩   🟩   🟩   🟩   🟩                       │ │
│  │  Emma   🟨   🟨   🟩   🟩   🟩   ⬜   ⬜   🟩                       │ │
│  │  Alex   🟥   🟥   🟨   🟨   🟩   🟩   🟩   🟩                       │ │
│  │                                                                       │ │
│  │  [View Full Calendar]                                                 │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────────────────┘
```

**Key Features**:
- Real-time utilization metrics with color coding
- Alert panel for over-allocation and upcoming time-off
- Financial summary with margin calculations
- AI-powered recommendations
- Capacity heatmap with weekly view
- Quick access to active projects

---

## 2. Resource Booking Interface (Drag & Drop)

**Purpose**: Interactive drag-and-drop interface for allocating resources to projects
**User Role**: Manager

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Resource Booking - Project Alpha                          [Save] [Cancel] │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─ Available Resources ─────┐  ┌─ Project Timeline ───────────────────┐ │
│  │                            │  │                                       │ │
│  │  🔍 Search...  🔽 Filter   │  │  Week:  Nov 13  Nov 20  Nov 27  Dec 4│ │
│  │  ☑ Skills  ☑ Dept  ☑ Avail│  │                                       │ │
│  │                            │  │  Backend Development                  │ │
│  │  ┌──────────────────────┐ │  │  ┌─────────────────────────────────┐ │ │
│  │  │ 👤 Sarah Chen        │ │  │  │  [████████░░] 80%               │ │ │
│  │  │ Senior Developer     │ │  │  │  Sarah (20h/wk) - Confirmed     │ │ │
│  │  │ React, Node.js       │ │  │  └─────────────────────────────────┘ │ │
│  │  │ Capacity: ████░ 80%  │ │  │                                       │ │
│  │  │ $150/hr  💰          │ │  │  Frontend Design                      │ │
│  │  └──────────────────────┘ │  │  ┌─────────┐ [Drop Zone - Valid]    │ │
│  │         ⬇ DRAG ME          │  │  │         │                         │ │
│  │  ┌──────────────────────┐ │  │  └─────────┘                         │ │
│  │  │ 👤 Mike Johnson      │ │  │                                       │ │
│  │  │ UI/UX Designer       │ │  │  QA Testing                           │ │
│  │  │ Figma, Sketch        │ │  │  ┌─────────────────┐                 │ │
│  │  │ Capacity: ███░░ 60%  │ │  │  │  [█████] 50%    │ [Over-capacity] │ │
│  │  │ $120/hr  💰          │ │  │  │  Alex (40h/wk)  │  🟥 Warning!   │ │
│  │  └──────────────────────┘ │  │  └─────────────────┘                 │ │
│  │                            │  │                                       │ │
│  │  ┌──────────────────────┐ │  │  [+ Add Activity]                     │ │
│  │  │ 👤 Emma Liu          │ │  │                                       │ │
│  │  │ QA Engineer          │ │  └───────────────────────────────────────┘ │
│  │  │ Selenium, Jest       │  │                                           │
│  │  │ Capacity: ███░░ 65%  │  │  ┌─ AI Suggestions ─────────────────┐  │ │
│  │  │ ⬜ Time-Off Nov 18-22│  │  │ 🤖 Recommended Resources          │  │ │
│  │  │ $95/hr  💰           │  │  │                                    │  │ │
│  │  └──────────────────────┘ │  │  │ ⭐ Mike Johnson (92% match)    │  │ │
│  │                            │  │  │    Skills: Figma, Sketch       │  │ │
│  │  ┌──────────────────────┐ │  │  │    Availability: 40% free      │  │ │
│  │  │ 👤 Alex Rivera       │ │  │  │    [+ Allocate]                │  │ │
│  │  │ QA Lead              │ │  │  │                                    │  │ │
│  │  │ Python, Automation   │  │  │  │ ⭐ Carlos Martinez (88% match)│  │ │
│  │  │ Capacity: 🟥 110%   │  │  │  │    Skills: React, TypeScript   │  │ │
│  │  │ $105/hr  💰          │  │  │  │    Availability: 30% free      │  │ │
│  │  └──────────────────────┘ │  │  │    [+ Allocate]                │  │ │
│  │                            │  │  └────────────────────────────────┘  │ │
│  └────────────────────────────┘  │                                       │ │
│                                   │                                       │ │
└────────────────────────────────────────────────────────────────────────────┘
```

**Drag & Drop Behavior**:
- **Dragging**: Resource card follows cursor with ghost image
- **Valid Drop Zone**: Green border, shows "Drop to allocate"
- **Invalid Drop Zone**: Red border with reason (e.g., "Resource on time-off")
- **Over-capacity Warning**: Yellow/red warning if allocation exceeds 100%
- **Drop Action**: Opens modal to confirm allocation details (hours, %, dates)

**Visual Feedback**:
```
While Dragging:
┌──────────────────────┐
│ 👤 Sarah Chen        │ ← Ghost image
│ Senior Developer     │
│ Capacity: 20% free   │ ← Real-time capacity
└──────────────────────┘

Drop Zone States:
🟩 Valid Drop:    [████████░░] Capacity OK
🟨 Warning:       [█████████░] Near capacity (90-100%)
🟥 Over-capacity: [██████████] Exceeds 100%
⬜ Time-Off:      [▒▒▒▒▒▒▒▒▒▒] Resource unavailable
```

---

## 3. Resource View

**Purpose**: List/grid view of all resources with filtering and quick allocation
**User Role**: Manager, Administrator

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Resources                                                                  │
├────────────────────────────────────────────────────────────────────────────┤
│  🔍 Search by name, skills...    [🔽 Department] [🔽 Employment] [🔽 Skills]│
│                                                                             │
│  [+ Add Resource]  [📥 Import]  [📤 Export]          View: [Grid] [List]  │
│                                                                             │
│  Showing 24 resources  •  Engineering Department                           │
│                                                                             │
├────┬──────────────────┬───────────┬─────────────┬──────────┬──────────────┤
│    │ Name             │ Title     │ Skills      │ Capacity │ This Week    │
├────┼──────────────────┼───────────┼─────────────┼──────────┼──────────────┤
│ 👤 │ Sarah Chen       │ Sr Dev    │ React       │ 🟥 120% │ Project A 80%│
│ FTE│ Engineering Dept │ $150/hr   │ Node.js     │ 40h/40h  │ Project B 40%│
│    │ Manager: J.Smith │           │ TypeScript  │          │ [View Cal]   │
├────┼──────────────────┼───────────┼─────────────┼──────────┼──────────────┤
│ 👤 │ Mike Johnson     │ Designer  │ Figma       │ 🟩 60%  │ Project A 50%│
│ FTE│ Design Dept      │ $120/hr   │ Sketch      │ 24h/40h  │ Unallocated  │
│    │ Manager: A.Davis │           │ Adobe XD    │          │ [View Cal]   │
├────┼──────────────────┼───────────┼─────────────┼──────────┼──────────────┤
│ 👤 │ Emma Liu         │ QA Engr   │ Selenium    │ ⬜ 0%   │ ⬜ Time-Off  │
│ FTE│ Engineering Dept │ $95/hr    │ Jest        │ 0h/40h   │ Nov 18-22    │
│    │ Manager: J.Smith │           │ Cypress     │          │ [View Cal]   │
├────┼──────────────────┼───────────┼─────────────┼──────────┼──────────────┤
│ 👤 │ Alex Rivera      │ QA Lead   │ Python      │ 🟥 110% │ Project C 70%│
│ CON│ Engineering Dept │ $105/hr   │ Automation  │ 44h/40h  │ Project D 40%│
│    │ Manager: J.Smith │ End: 12/31│ CI/CD       │          │ [View Cal]   │
├────┼──────────────────┼───────────┼─────────────┼──────────┼──────────────┤
│ 👤 │ Carlos Martinez  │ Full Stack│ React       │ 🟨 85%  │ Project B 85%│
│ FTE│ Engineering Dept │ $140/hr   │ Python      │ 34h/40h  │              │
│    │ Manager: J.Smith │           │ PostgreSQL  │          │ [View Cal]   │
└────┴──────────────────┴───────────┴─────────────┴──────────┴──────────────┘

  ← Prev   1 2 3 4 5   Next →                       Rows per page: [25 ▼]

Legend: FTE=Full-time  CON=Contractor  🟥>100%  🟨80-100%  🟩<80%  ⬜Time-off
```

**Inline Actions** (on hover/click):
- Click row to view resource details
- Drag row to quick-allocate to project
- Right-click for context menu (Edit, View Calendar, Delete)
- Filter by clicking skill tags

**Grid View Alternative**:
```
┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│ 👤 Sarah Chen  │ │ 👤 Mike Johnson│ │ 👤 Emma Liu    │
│ Senior Dev     │ │ UI/UX Designer │ │ QA Engineer    │
│ Engineering    │ │ Design         │ │ Engineering    │
│                │ │                │ │                │
│ Capacity: 🟥  │ │ Capacity: 🟩  │ │ ⬜ Time-Off    │
│ ████████████   │ │ ██████░░░░     │ │ Nov 18-22      │
│ 120% (48h/40h) │ │ 60% (24h/40h)  │ │                │
│                │ │                │ │                │
│ React, Node.js │ │ Figma, Sketch  │ │ Selenium, Jest │
│ TypeScript     │ │ Adobe XD       │ │ Cypress        │
│                │ │                │ │                │
│ $150/hr  💰    │ │ $120/hr  💰    │ │ $95/hr  💰     │
└────────────────┘ └────────────────┘ └────────────────┘
```

---

## 4. Project View

**Purpose**: List of projects with financial summary and resource allocation
**User Role**: Manager

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Projects                                                                   │
├────────────────────────────────────────────────────────────────────────────┤
│  🔍 Search projects...    [🔽 Status] [🔽 Owner] [🔽 Client]               │
│                                                                             │
│  [+ New Project]  [📊 Portfolio View]              View: [List] [Kanban]  │
│                                                                             │
│  ┌─ Project Alpha ─────────────────────────────────────────────────────┐  │
│  │  Status: In Progress  •  Owner: John Smith  •  Client: Acme Corp    │  │
│  │  Timeline: Nov 1 - Dec 31 (8 weeks) ████████░░ 75% complete         │  │
│  │                                                                       │  │
│  │  Financial Summary:                                                   │  │
│  │  Budget: $120,000  •  Spent: $90,000 (75%)  •  Margin: 28.5%  ▲     │  │
│  │  Revenue: $150,000  •  Cost: $107,250  •  Projected: $142,000       │  │
│  │                                                                       │  │
│  │  Resource Allocation:                         [🤖 Suggest Resources] │  │
│  │  ┌────────────────┬────────┬──────────┬────────┬──────────────────┐ │  │
│  │  │ Resource       │ Role   │ Alloc %  │ Cost   │ Timeline          │ │  │
│  │  ├────────────────┼────────┼──────────┼────────┼──────────────────┤ │  │
│  │  │ Sarah Chen     │ Backend│ 50%      │$48,000 │ ████████████████ │ │  │
│  │  │ Carlos Martinez│ FullStk│ 70%      │$39,200 │ ██████████░░░░░░ │ │  │
│  │  │ Mike Johnson   │ Design │ 40%      │$19,200 │ ████████░░░░░░░░ │ │  │
│  │  └────────────────┴────────┴──────────┴────────┴──────────────────┘ │  │
│  │                                                                       │  │
│  │  [View Details] [Edit] [📊 Reports]                     [⋮ More]    │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
│  ┌─ Website Redesign ──────────────────────────────────────────────────┐  │
│  │  Status: Planning  •  Owner: Anna Davis  •  Client: TechStart Inc   │  │
│  │  Timeline: Dec 1 - Jan 31 (8 weeks) ███░░░░░░░ 30% complete         │  │
│  │                                                                       │  │
│  │  Financial Summary:                                                   │  │
│  │  Budget: $85,000  •  Spent: $12,500 (15%)  •  Margin: 32.1%  ▲      │  │
│  │  Revenue: $105,000  •  Cost: $71,250  •  Projected: $102,000        │  │
│  │                                                                       │  │
│  │  Resource Allocation:                         [🤖 Suggest Resources] │  │
│  │  ┌────────────────┬────────┬──────────┬────────┬──────────────────┐ │  │
│  │  │ Resource       │ Role   │ Alloc %  │ Cost   │ Timeline          │ │  │
│  │  ├────────────────┼────────┼──────────┼────────┼──────────────────┤ │  │
│  │  │ Mike Johnson   │ Lead   │ 60%      │$28,800 │ ████████████████ │ │  │
│  │  │ (Need designer)│ -      │ -        │ -      │ [+ Allocate]     │ │  │
│  │  └────────────────┴────────┴──────────┴────────┴──────────────────┘ │  │
│  │                                                                       │  │
│  │  [View Details] [Edit] [📊 Reports]                     [⋮ More]    │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
│  ← Prev   1 2 3   Next →                                                   │
└────────────────────────────────────────────────────────────────────────────┘
```

**AI Suggestion Panel** (when clicked):
```
┌─ AI Resource Recommendations ───────────────────────────┐
│                                                          │
│  Based on project requirements and team availability:   │
│                                                          │
│  ⭐ Emma Liu (94% match)                                │
│  │  QA Engineer  •  Available: Dec 1                    │
│  │  Skills: Selenium, Jest, Cypress                     │
│  │  Match reasons:                                      │
│  │  • Has required QA skills (95% match)               │
│  │  • Available during project timeline                 │
│  │  • Successfully completed similar projects           │
│  │  • Currently under-utilized (65%)                    │
│  │  Cost: $95/hr  •  Capacity: 35% free                │
│  │  [✓ Allocate 30%] [View Profile]                    │
│  │                                                       │
│  ⭐ David Park (87% match)                              │
│  │  Full Stack Developer  •  Available: Dec 5           │
│  │  Skills: React, Node.js, TypeScript                  │
│  │  Match reasons:                                      │
│  │  • Strong skills alignment (88%)                    │
│  │  • Works well with Mike Johnson (past project)      │
│  │  • Currently under-utilized (55%)                    │
│  │  Cost: $135/hr  •  Capacity: 45% free               │
│  │  [✓ Allocate 40%] [View Profile]                    │
│                                                          │
│  [View All Recommendations (8)]              [✕ Close]  │
└──────────────────────────────────────────────────────────┘
```

---

## 5. Calendar/Timeline View

**Purpose**: Weekly grid showing resource bookings and time-off
**User Role**: Manager, User (own calendar)

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Calendar View                                          [Week] [Month] [Q] │
├────────────────────────────────────────────────────────────────────────────┤
│  ← Nov 2025 →     Week 46: Nov 11 - Nov 17                                │
│                                                                             │
│  Resources ▼          Mon 11  Tue 12  Wed 13  Thu 14  Fri 15  Total       │
│                                                                             │
│  Sarah Chen           ┌──────┬──────┬──────┬──────┬──────┐                │
│  Capacity: 40h/wk     │ ████ │ ████ │ ████ │ ████ │ ████ │ 🟥 48h (120%) │
│  FTE • Engineering    │ Proj │ Proj │ Proj │ Proj │ Proj │                │
│                       │  A   │  A   │  A   │  B   │  B   │                │
│                       │ 8h   │ 8h   │ 8h   │ 8h   │ 8h   │ Project A: 24h │
│                       │ ████ │ ████ │ ████ │ ████ │ ████ │ Project B: 24h │
│                       │ Proj │ Proj │ Proj │ Proj │ Proj │                │
│                       │  B   │  B   │  B   │  C   │  C   │                │
│                       └──────┴──────┴──────┴──────┴──────┘                │
│  [Drag & drop to allocate] ▲ Over-allocated!                              │
│                                                                             │
│  Mike Johnson         ┌──────┬──────┬──────┬──────┬──────┐                │
│  Capacity: 40h/wk     │ ███░ │ ███░ │ ███░ │ ███░ │ ███░ │ 🟩 24h (60%)  │
│  FTE • Design         │ Proj │ Proj │ Proj │ Proj │ Proj │                │
│                       │  A   │  A   │  A   │  A   │  A   │                │
│                       │ 5h   │ 5h   │ 5h   │ 5h   │ 4h   │ Project A: 24h │
│                       └──────┴──────┴──────┴──────┴──────┘                │
│  [+ Add Allocation]                                                        │
│                                                                             │
│  Emma Liu             ┌──────┬──────┬──────┬──────┬──────┐                │
│  Capacity: 40h/wk     │ ▒▒▒▒ │ ▒▒▒▒ │ ▒▒▒▒ │ ▒▒▒▒ │ ▒▒▒▒ │ ⬜ Time-Off    │
│  FTE • Engineering    │ PTO  │ PTO  │ PTO  │ PTO  │ PTO  │ (Vacation)     │
│                       │      │      │      │      │      │ 40h            │
│                       └──────┴──────┴──────┴──────┴──────┘                │
│  Vacation: Nov 11-15 (Approved by J.Smith)                                │
│                                                                             │
│  Alex Rivera          ┌──────┬──────┬──────┬──────┬──────┐                │
│  Capacity: 40h/wk     │ ████ │ ████ │ ████ │ ████ │ ████ │ 🟥 44h (110%) │
│  Contractor • QA      │ Proj │ Proj │ Proj │ Proj │ Proj │                │
│                       │  C   │  C   │  C   │  C   │  C   │                │
│                       │ 6h   │ 6h   │ 6h   │ 6h   │ 4h   │ Project C: 28h │
│                       │ ████ │ ████ │ ████ │ ████ │ ████ │ Project D: 16h │
│                       │ Proj │ Proj │ Proj │ Proj │      │                │
│                       │  D   │  D   │  D   │  D   │      │                │
│                       └──────┴──────┴──────┴──────┴──────┘                │
│  ⚠ Over-allocated! Consider reducing allocation.                          │
│                                                                             │
│  Carlos Martinez      ┌──────┬──────┬──────┬──────┬──────┐                │
│  Capacity: 40h/wk     │ ████ │ ████ │ ████ │ ████ │ ███░ │ 🟨 34h (85%)  │
│  FTE • Engineering    │ Proj │ Proj │ Proj │ Proj │ Proj │                │
│                       │  B   │  B   │  B   │  B   │  B   │                │
│                       │ 7h   │ 7h   │ 7h   │ 7h   │ 6h   │ Project B: 34h │
│                       └──────┴──────┴──────┴──────┴──────┘                │
│                                                                             │
└────────────────────────────────────────────────────────────────────────────┘

Legend:  ████ Allocation  ▒▒▒▒ Time-Off  🟥 >100%  🟨 80-100%  🟩 <80%
```

**Color Coding**:
- 🔵 Blue bars: Regular allocations
- ⬜ Gray striped: Time-off (vacation, sick leave)
- 🟥 Red highlight: Over-allocated (>100%)
- 🟨 Yellow highlight: Near capacity (80-100%)
- 🟩 Green: Under-utilized (<80%)

**Interaction**:
- Click cell to view allocation details
- Drag resource name onto timeline to create allocation
- Drag allocation bar to move/extend
- Right-click for context menu (Edit, Delete, Mark Tentative)

---

## 6. Time-Off Management

**Purpose**: Submit and approve time-off requests
**User Role**: User (submit), Manager (approve)

**User View (Submit Request)**:
```
┌────────────────────────────────────────────────────────────────────────────┐
│  My Time-Off                                                                │
├────────────────────────────────────────────────────────────────────────────┤
│  [+ Request Time-Off]                                    [Calendar] [List] │
│                                                                             │
│  ┌─ Time-Off Balance ──────────────────────────────────────────────────┐  │
│  │  Vacation Days:  15 available  •  5 used  •  10 remaining           │  │
│  │  Sick Leave:     10 available  •  2 used  •  8 remaining            │  │
│  │  Personal Days:  5 available   •  0 used  •  5 remaining            │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
│  ┌─ November 2025 Calendar ──────────────────────────────────────────┐    │
│  │  Sun  Mon  Tue  Wed  Thu  Fri  Sat                                │    │
│  │                              1    2    3                           │    │
│  │   4    5    6    7    8    9   10                                 │    │
│  │  11   12   13   14   15   16   17  ← Week 46                      │    │
│  │ [▒▒] [▒▒] [▒▒] [▒▒] [▒▒]                                          │    │
│  │  Vacation - Approved                                               │    │
│  │  18   19   20   21   22   23   24  ← Week 47                      │    │
│  │  25   26   27   28   29   30                                       │    │
│  └────────────────────────────────────────────────────────────────────┘    │
│                                                                             │
│  ┌─ My Time-Off Requests ────────────────────────────────────────────┐    │
│  │                                                                     │    │
│  │  ✅ Vacation - Nov 11-15 (5 days)                                 │    │
│  │     Status: Approved by John Smith on Nov 1                        │    │
│  │     Conflicts: None                                                │    │
│  │     [View] [Cancel Request]                                        │    │
│  │                                                                     │    │
│  │  ⏳ Sick Leave - Dec 20 (1 day)                                   │    │
│  │     Status: Pending approval                                       │    │
│  │     Conflicts: Allocated to Project B (8h)                         │    │
│  │     [View] [Edit] [Cancel]                                         │    │
│  │                                                                     │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
└────────────────────────────────────────────────────────────────────────────┘
```

**Request Time-Off Modal**:
```
┌─ Request Time-Off ──────────────────────────────────────┐
│                                                          │
│  Type: [Vacation ▼]                                     │
│                                                          │
│  Start Date:  [Nov 20, 2025  📅]                        │
│  End Date:    [Nov 22, 2025  📅]                        │
│  Duration:    3 days                                     │
│                                                          │
│  ☐ Half day (4 hours)                                   │
│  ☐ Recurring (every week/month)                         │
│                                                          │
│  Notes:                                                  │
│  ┌────────────────────────────────────────────────────┐ │
│  │ Family vacation - Thanksgiving week                │ │
│  └────────────────────────────────────────────────────┘ │
│                                                          │
│  ⚠ Potential Conflicts:                                 │
│  • Project Alpha: 24h allocated (Nov 20-22)            │
│  • Weekly standup meeting: Nov 21 10am                  │
│                                                          │
│                               [Cancel]  [Submit Request] │
└──────────────────────────────────────────────────────────┘
```

**Manager View (Approve Requests)**:
```
┌────────────────────────────────────────────────────────────────────────────┐
│  Team Time-Off Requests                                    🔔 3 Pending    │
├────────────────────────────────────────────────────────────────────────────┤
│  [Team Calendar] [Pending (3)] [Approved] [All]                           │
│                                                                             │
│  ┌─ Pending Approval ────────────────────────────────────────────────────┐ │
│  │                                                                         │ │
│  │  👤 Emma Liu - Vacation                                                │ │
│  │     Nov 20-22 (3 days)  •  Submitted: Nov 10                          │ │
│  │     Notes: Family vacation - Thanksgiving week                         │ │
│  │                                                                         │ │
│  │     ⚠ Impact Analysis:                                                 │ │
│  │     • Project Alpha: 24h allocated → needs reassignment                │ │
│  │     • Team capacity drops to 75% during this period                    │ │
│  │     • 2 other team members already off (Mike, Sarah)                   │ │
│  │                                                                         │ │
│  │     🤖 AI Suggestion: Consider asking Emma to reschedule or           │ │
│  │        reassigning work to Carlos (currently 60% utilized)             │ │
│  │                                                                         │ │
│  │     [✅ Approve] [❌ Reject] [💬 Comment] [📅 Suggest Alternate Dates]│ │
│  │                                                                         │ │
│  ├─────────────────────────────────────────────────────────────────────────┤ │
│  │                                                                         │ │
│  │  👤 Alex Rivera - Sick Leave                                           │ │
│  │     Nov 15 (1 day)  •  Submitted: Nov 14                              │ │
│  │     Notes: Medical appointment                                         │ │
│  │                                                                         │ │
│  │     ℹ️ Impact Analysis:                                                │ │
│  │     • Project C: 8h allocated → minimal impact                         │ │
│  │     • Team capacity: 95% (no concerns)                                 │ │
│  │                                                                         │ │
│  │     [✅ Approve] [❌ Reject] [💬 Comment]                             │ │
│  │                                                                         │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## 7. Financial Dashboard

**Purpose**: Track profitability, costs, and revenue across projects
**User Role**: Manager, Administrator

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Financial Dashboard                           Period: Q4 2025 [▼]         │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─ Key Metrics ────────────────────────────────────────────────────────┐ │
│  │                                                                       │ │
│  │  Total Revenue:    $520,000  ▲ 12% vs Q3                            │ │
│  │  Total Cost:       $378,500  ▲ 8% vs Q3                             │ │
│  │  Profit Margin:    27.2%     ▲ 3.2% vs Q3                           │ │
│  │  Budget Variance:  +$15,500  (3.4% under budget) ✅                 │ │
│  │                                                                       │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                             │
│  ┌─ Revenue vs Cost Trend ──────────────────────────────────────────────┐ │
│  │                                                                       │ │
│  │  $600K │                                          ▲ Revenue           │ │
│  │        │                                    ┌───●                    │ │
│  │  $500K │                              ┌───●─┘                        │ │
│  │        │                        ┌───●─┘                              │ │
│  │  $400K │                  ┌───●─┘                                    │ │
│  │        │            ┌───●─┘   ■─────■─────■───── ▼ Cost             │ │
│  │  $300K │      ┌───●─┘   ■─────┘                                     │ │
│  │        │ ●──●─┘   ■─────┘                                           │ │
│  │  $200K │■─────────┘                                                  │ │
│  │        └─────────────────────────────────────────────────────────────│ │
│  │         Jan  Feb  Mar  Apr  May  Jun  Jul  Aug  Sep  Oct  Nov  Dec  │ │
│  │                                                                       │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                             │
│  ┌─ Project Profitability Matrix ───────────────────────────────────────┐ │
│  │                     Revenue    Cost     Margin   Status              │ │
│  │                                                                       │ │
│  │  Project Alpha      $150,000   $107,250  28.5%  🟩 On track         │ │
│  │  Website Redesign   $105,000   $71,250   32.1%  🟩 On track         │ │
│  │  Mobile App v2      $185,000   $152,500  17.6%  🟨 At risk          │ │
│  │  Marketing Campaign $80,000    $47,500   40.6%  🟩 Ahead            │ │
│  │                                                                       │ │
│  │  🟩 Profitable   🟨 Low margin (<20%)   🟥 Loss                     │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                             │
│  ┌─ Resource Utilization (Billable vs Non-Billable) ───────────────────┐ │
│  │                                                                       │ │
│  │  Billable Hours:      3,240h  (72%)  ████████████░░░░░              │ │
│  │  Non-Billable Hours:  1,260h  (28%)  ████░░░░░░░░░░░░               │ │
│  │  Bench Time:          420h    (9%)   ██░░░░░░░░░░░░░░               │ │
│  │                                                                       │ │
│  │  Top Earners (by revenue generated):                                 │ │
│  │  1. Sarah Chen       $72,000  (480h × $150/hr)                      │ │
│  │  2. Carlos Martinez  $56,000  (400h × $140/hr)                      │ │
│  │  3. Mike Johnson     $43,200  (360h × $120/hr)                      │ │
│  │                                                                       │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                             │
│  ┌─ Budget vs Actual by Department ─────────────────────────────────────┐ │
│  │                      Budget      Actual      Variance                │ │
│  │                                                                       │ │
│  │  Engineering         $250,000    $235,600    -$14,400  ✅ (5.8%)    │ │
│  │  Design              $80,000     $78,900     -$1,100   ✅ (1.4%)    │ │
│  │  QA                  $65,000     $64,000     -$1,000   ✅ (1.5%)    │ │
│  │                                                                       │ │
│  │  [Download Report] [Export to Excel]                                 │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                             │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## 8. Scenario Planner

**Purpose**: Create and compare "what-if" resource allocation scenarios
**User Role**: Manager

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Scenario Planner                                                           │
├────────────────────────────────────────────────────────────────────────────┤
│  Current Scenario: [Baseline Plan ▼]  vs  [Q4 Optimization ▼]             │
│  [+ New Scenario] [Clone] [Save] [Delete]                                 │
│                                                                             │
│  ┌─ Financial Impact Comparison ────────────────────────────────────────┐ │
│  │                      Baseline         Q4 Optimization    Difference  │ │
│  │                                                                       │ │
│  │  Total Cost:         $378,500         $365,200          -$13,300 ▼  │ │
│  │  Total Revenue:      $520,000         $535,000          +$15,000 ▲  │ │
│  │  Profit Margin:      27.2%            31.7%             +4.5% ▲     │ │
│  │  Team Utilization:   78%              85%               +7% ▲       │ │
│  │                                                                       │ │
│  │  💡 Recommendation: Q4 Optimization shows improved margins           │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                             │
│  ┌─ Resource Allocation Differences ────────────────────────────────────┐ │
│  │                                                                       │ │
│  │  Resource        Baseline              Q4 Optimization               │ │
│  │                                                                       │ │
│  │  Sarah Chen      Project A: 50%        Project A: 40%  ← Changed    │ │
│  │                  Project B: 40%        Project B: 40%                │ │
│  │                  Total: 90%            Project C: 20%  ← New         │ │
│  │                                         Total: 100%                   │ │
│  │                                                                       │ │
│  │  Mike Johnson    Project A: 40%        Project A: 60%  ← Changed    │ │
│  │                  Total: 40%            Total: 60%                     │ │
│  │                                                                       │ │
│  │  Emma Liu        ⬜ Unallocated       Project D: 70%  ← New         │ │
│  │                  Total: 0%             Total: 70%                     │ │
│  │                                                                       │ │
│  │  Alex Rivera     Project C: 70%        Project C: 80%  ← Changed    │ │
│  │                  Project D: 40%        Removed  ← Removed            │ │
│  │                  Total: 110% 🟥       Total: 80% 🟨                 │ │
│  │                                                                       │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                             │
│  ┌─ Timeline Comparison (Week 46-50) ───────────────────────────────────┐ │
│  │                                                                       │ │
│  │  Baseline Plan:                                                       │ │
│  │  Sarah  │████████│████████│████████│████████│ 90% avg              │ │
│  │  Mike   │████░░░░│████░░░░│████░░░░│████░░░░│ 40% avg              │ │
│  │  Emma   │░░░░░░░░│░░░░░░░░│░░░░░░░░│░░░░░░░░│  0% avg              │ │
│  │  Alex   │████████│████████│████████│████████│ 110% avg 🟥          │ │
│  │                                                                       │ │
│  │  Q4 Optimization:                                                     │ │
│  │  Sarah  │████████│████████│████████│████████│ 100% avg 🟩          │ │
│  │  Mike   │████████│████████│████████│████████│ 60% avg              │ │
│  │  Emma   │████████│████████│████████│████████│ 70% avg              │ │
│  │  Alex   │████████│████████│████████│████████│ 80% avg 🟨           │ │
│  │                                                                       │ │
│  │  ✅ Better resource balance  •  No over-allocations                 │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                             │
│  [💾 Save Scenario] [📤 Publish as Baseline] [✕ Discard Changes]         │
│                                                                             │
└────────────────────────────────────────────────────────────────────────────┘
```

**Key Features**:
- Side-by-side scenario comparison
- Financial impact analysis
- Resource allocation changes highlighted
- Timeline comparison
- Ability to publish scenario as new baseline

---

## 9. AI Resource Recommendations

**Purpose**: AI-powered suggestions for optimal resource allocation
**Integration**: Appears in multiple views (Dashboard, Project View, Booking Interface)

**Recommendation Card Design**:
```
┌─ AI Resource Recommendations ────────────────────────────────────┐
│  🤖 For Project: Website Redesign                                │
│                                                                   │
│  ⭐⭐⭐⭐⭐ 94% Match                                             │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │ 👤 Emma Liu                                                  ││
│  │ QA Engineer  •  Engineering Dept                             ││
│  │                                                               ││
│  │ Skills: Selenium, Jest, Cypress, API Testing                 ││
│  │ Availability: 100% free (0h allocated)                       ││
│  │ Rate: $95/hr  •  FTE                                         ││
│  │                                                               ││
│  │ Why this match?                                              ││
│  │ ✓ Has 3/3 required skills (Selenium, Jest, Cypress)         ││
│  │ ✓ Available for entire project timeline (Dec 1 - Jan 31)    ││
│  │ ✓ Successfully completed 4 similar QA projects               ││
│  │ ✓ Currently under-utilized (0% allocated)                    ││
│  │ ✓ Works well with Mike Johnson (past collaboration)         ││
│  │                                                               ││
│  │ Suggested Allocation: 60% (24h/week)                         ││
│  │ Estimated Cost: $22,800                                      ││
│  │                                                               ││
│  │ [✓ Accept & Allocate] [👁 View Profile] [✕ Dismiss]        ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                   │
│  ⭐⭐⭐⭐☆ 87% Match                                              │
│  ┌──────────────────────────────────────────────────────────────┐│
│  │ 👤 David Park                                                ││
│  │ Full Stack Developer  •  Engineering Dept                    ││
│  │                                                               ││
│  │ Skills: React, Node.js, TypeScript, Testing                  ││
│  │ Availability: 45% free (18h available)                       ││
│  │ Rate: $135/hr  •  FTE                                        ││
│  │                                                               ││
│  │ Why this match?                                              ││
│  │ ✓ Strong technical skills alignment (88% match)             ││
│  │ ✓ Has worked successfully with Mike Johnson (Project B)     ││
│  │ ✓ Currently under-utilized (55% allocated)                   ││
│  │ ~ Available capacity may be insufficient for full project    ││
│  │                                                               ││
│  │ Suggested Allocation: 40% (16h/week)                         ││
│  │ Estimated Cost: $34,560                                      ││
│  │                                                               ││
│  │ [✓ Accept & Allocate] [👁 View Profile] [✕ Dismiss]        ││
│  └──────────────────────────────────────────────────────────────┘│
│                                                                   │
│  [Show All Recommendations (8)]  [Refine Search]  [✕ Close]     │
└───────────────────────────────────────────────────────────────────┘
```

**Feedback Loop**:
```
After user accepts/rejects recommendation:

┌─ Feedback ─────────────────────────────────────┐
│                                                 │
│  You accepted Emma Liu for Website Redesign    │
│                                                 │
│  Help improve our recommendations:              │
│                                                 │
│  How accurate was this match?                   │
│  ☆☆☆☆☆ (Rate 1-5 stars)                       │
│                                                 │
│  Any additional comments? (optional)            │
│  ┌─────────────────────────────────────────┐   │
│  │                                         │   │
│  └─────────────────────────────────────────┘   │
│                                                 │
│  [Submit Feedback] [Skip]                       │
└─────────────────────────────────────────────────┘
```

---

## Design System & Components

### Color Palette
```
Primary Colors:
- Primary Blue:    #2563EB (actions, links)
- Success Green:   #10B981 (under-utilized, approved)
- Warning Yellow:  #F59E0B (near capacity, pending)
- Danger Red:      #EF4444 (over-allocated, errors)
- Gray Neutral:    #6B7280 (time-off, disabled)

Background:
- White:           #FFFFFF
- Light Gray:      #F3F4F6
- Dark Gray:       #1F2937 (text)

Capacity Indicators:
🟩 Green:   0-79% (under-utilized)
🟨 Yellow:  80-100% (optimal range)
🟥 Red:     101%+ (over-allocated)
⬜ Gray:    Time-off / unavailable
```

### Typography
```
Headings:
- H1: 24px, Bold (Page titles)
- H2: 20px, Bold (Section headers)
- H3: 16px, Semi-bold (Subsections)

Body:
- Regular: 14px (Main text)
- Small: 12px (Captions, metadata)
- Tiny: 10px (Labels, badges)

Font: System font stack (SF Pro, Segoe UI, Roboto)
```

### UI Patterns

**Capacity Bar**:
```
Under-utilized (60%):
████████░░░░░░░░░░░░ 60% (24h/40h) 🟩

Optimal (85%):
█████████████████░░░ 85% (34h/40h) 🟨

Over-allocated (120%):
████████████████████████ 120% (48h/40h) 🟥

With time-off:
████████▒▒▒▒░░░░░░░░ 40% + PTO 🟩
```

**Status Badges**:
```
[Confirmed]  [Tentative]  [Pending]  [Approved]  [Rejected]
```

**Action Buttons**:
```
Primary:   [Save Changes]
Secondary: [Cancel]
Danger:    [Delete]
Icon:      [+ Add]  [✕ Close]  [⋮ More]
```

---

## Responsive Design Notes

### Desktop (1920x1080)
- Full multi-column layouts
- Side-by-side comparisons
- Detailed data tables
- Drag-and-drop enabled

### Tablet (768x1024)
- Simplified 2-column layouts
- Collapsible sidebars
- Touch-optimized buttons (larger targets)
- Drag-and-drop still functional

### Mobile (375x667)
- Single column stacked layout
- Bottom navigation bar
- Simplified views (essential data only)
- Swipe gestures for actions
- Tap to allocate (no drag-and-drop)

---

## Accessibility Considerations

- **Keyboard Navigation**: All drag-and-drop operations have keyboard alternatives
- **Screen Readers**: Proper ARIA labels for all interactive elements
- **Color Contrast**: WCAG AA compliance (4.5:1 minimum)
- **Focus Indicators**: Visible focus states for all interactive elements
- **Alt Text**: All icons and images have descriptive alt text
- **Tooltips**: Contextual help available on hover/focus

---

**End of UI Mockups Document**

For technical implementation details, refer to `REQUIREMENTS.md`
