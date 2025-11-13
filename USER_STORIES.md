# Resource Management Application - User Stories

**Document Version**: 1.0
**Last Updated**: 2025-11-13
**Technology Stack**: Neon DB (Serverless Postgres) + Vercel

---

## Table of Contents

1. [Epic 1: Resource Management](#epic-1-resource-management)
2. [Epic 2: Project & Activity Management](#epic-2-project--activity-management)
3. [Epic 3: Resource Booking & Allocation](#epic-3-resource-booking--allocation)
4. [Epic 4: Time-Off Management](#epic-4-time-off-management)
5. [Epic 5: Financial Management](#epic-5-financial-management)
6. [Epic 6: AI-Powered Recommendations](#epic-6-ai-powered-recommendations)
7. [Epic 7: Scenario Planning](#epic-7-scenario-planning)
8. [Epic 8: Workload Analysis & Reporting](#epic-8-workload-analysis--reporting)
9. [Epic 9: User Management & Authentication](#epic-9-user-management--authentication)

---

## Epic 1: Resource Management

### US-101: View All Team Resources
**As a** Manager
**I want to** view a list of all team members with their skills, capacity, and current allocation
**So that** I can understand my team's composition and availability at a glance

**Acceptance Criteria**:
- Display list/grid view of all resources in my department
- Show: name, title, skills, employment status, current capacity %
- Filter by: department, skills, employment status (FTE/Contractor), availability
- Search by name or skill
- Color-code capacity: 🟩 <80%, 🟨 80-100%, 🟥 >100%
- Show time-off periods as gray/unavailable
- Click resource to view detailed profile

**Technical Notes**:
- Query Neon DB Resources table with filters
- Use server-side rendering on Vercel for initial load
- Client-side filtering for real-time experience

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

### US-102: Add New Resource
**As an** Administrator
**I want to** add a new team member to the system
**So that** they can be allocated to projects

**Acceptance Criteria**:
- Form fields: name, email, title, department, manager, employment status
- Required fields: name, email, title, employment status
- Multi-select skills with autocomplete
- Set weekly capacity hours (default 40 for FTE)
- Set billable rate and cost rate
- Set start date (and end date for contractors)
- Validate email uniqueness
- Send welcome email to new resource

**Technical Notes**:
- Insert into Neon DB Resources table
- Create associated User account record
- Trigger welcome email via Vercel serverless function

**Priority**: P0 (Critical - MVP)
**Story Points**: 3

---

### US-103: Update Resource Skills
**As a** User
**I want to** update my own skills and proficiency levels
**So that** I can be matched to appropriate projects

**Acceptance Criteria**:
- View current skills with proficiency levels
- Add new skills from autocomplete list
- Create new skill if not in system
- Set proficiency: Beginner, Intermediate, Advanced, Expert
- Remove skills no longer relevant
- Changes visible immediately in resource profile

**Technical Notes**:
- Update Resource_Skills junction table in Neon DB
- Auto-suggest from existing Skills table
- Real-time updates via API route

**Priority**: P1 (High)
**Story Points**: 3

---

### US-104: View Organizational Hierarchy
**As a** Manager
**I want to** view the organizational hierarchy showing reporting relationships
**So that** I can understand team structure and request resources appropriately

**Acceptance Criteria**:
- Display org chart visualization
- Show manager-resource relationships
- Filter by department
- Click resource to view details
- Highlight my direct reports
- Show resource capacity on org chart

**Technical Notes**:
- Query Neon DB with recursive CTE for hierarchy
- Use React library for org chart visualization (e.g., react-organizational-chart)
- Cache hierarchy data for performance

**Priority**: P2 (Medium)
**Story Points**: 5

---

## Epic 2: Project & Activity Management

### US-201: Create New Project
**As a** Manager
**I want to** create a new project with budget and timeline
**So that** I can start allocating resources

**Acceptance Criteria**:
- Form fields: name, description, start date, end date
- Set budget amount and currency
- Mark as billable or non-billable
- Add client name (if billable)
- Set estimated effort in hours
- Assign project owner
- Save as draft or publish

**Technical Notes**:
- Insert into Neon DB Projects table
- Validate date ranges
- Store currency as ISO code (USD, EUR, etc.)

**Priority**: P0 (Critical - MVP)
**Story Points**: 3

---

### US-202: Add Activities to Project
**As a** Manager
**I want to** break down a project into activities/tasks
**So that** I can allocate resources to specific work items

**Acceptance Criteria**:
- Add activity name, description, dates
- Estimate hours for activity
- Specify required skills
- Create sub-activities (hierarchical)
- Reorder activities
- Activities inherit project dates by default

**Technical Notes**:
- Insert into Neon DB Activities table
- Support parent_activity_id for hierarchy
- Validate activity dates within project timeline

**Priority**: P1 (High)
**Story Points**: 3

---

### US-203: View Project Financial Summary
**As a** Manager
**I want to** see the financial summary of my project
**So that** I can track budget vs. actual spend

**Acceptance Criteria**:
- Display: budget, total cost, total revenue, margin %
- Show budget burn rate
- Compare planned vs. actual costs
- Display cost by resource
- Show billable vs. non-billable breakdown
- Alert when approaching budget limit (>90%)

**Technical Notes**:
- Aggregate from Resource_Allocations in Neon DB
- Calculate: SUM(calculated_cost), SUM(calculated_revenue)
- Real-time calculation via Vercel serverless function
- Cache results for 5 minutes

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

## Epic 3: Resource Booking & Allocation

### US-301: Drag-and-Drop Resource Allocation
**As a** Manager
**I want to** drag resources onto a project timeline
**So that** I can quickly allocate them to work

**Acceptance Criteria**:
- Drag resource card from left panel onto project timeline
- Show visual feedback: green (valid), yellow (warning), red (over-capacity)
- Display real-time capacity calculation during drag
- Drop opens modal to confirm allocation details
- Modal pre-fills: resource, project, dates
- Set allocation percentage or hours per week
- Mark as tentative or confirmed
- Show warning if resource has time-off during period

**Technical Notes**:
- Use @dnd-kit/core for drag-and-drop on Vercel-hosted React app
- Real-time capacity calculation via client-side logic
- WebSocket for multi-user conflict detection
- Insert allocation into Neon DB with rate snapshots

**Priority**: P0 (Critical - MVP)
**Story Points**: 8

---

### US-302: View My Assignments
**As a** User
**I want to** view all projects I'm currently allocated to
**So that** I know what work I'm expected to do

**Acceptance Criteria**:
- List all current and upcoming assignments
- Show: project name, allocation %, dates, activity
- Display weekly breakdown of allocations
- Show total capacity utilization
- Filter by date range
- Export to calendar (iCal format)

**Technical Notes**:
- Query Neon DB Resource_Allocations by resource_id
- Filter where week_start_date >= today
- Join with Projects and Activities tables
- Generate iCal file via Vercel function

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

### US-303: Modify Resource Allocation
**As a** Manager
**I want to** modify an existing resource allocation
**So that** I can adjust to changing project needs

**Acceptance Criteria**:
- Edit allocation percentage or hours
- Change start/end dates
- Convert tentative to confirmed
- Add notes/comments
- View allocation history
- Notify resource of changes
- Prevent modification of completed allocations

**Technical Notes**:
- Update Resource_Allocations in Neon DB
- Log changes to Audit_Log table
- Recalculate project costs
- Send notification via email (Vercel email function)

**Priority**: P1 (High)
**Story Points**: 3

---

### US-304: Bulk Allocate Team
**As a** Manager
**I want to** allocate multiple resources to a project at once
**So that** I can quickly staff up a new project

**Acceptance Criteria**:
- Select multiple resources (checkboxes)
- Set common allocation: percentage, dates, project
- Set individual allocation percentages in bulk modal
- Preview capacity impact before confirming
- Warning for any over-allocations
- Apply all allocations atomically (all or nothing)

**Technical Notes**:
- Batch insert into Neon DB using transaction
- Use Postgres transactions for atomicity
- Validate all allocations before committing

**Priority**: P2 (Medium)
**Story Points**: 5

---

## Epic 4: Time-Off Management

### US-401: Request Time-Off
**As a** User
**I want to** request time-off (vacation, sick leave, etc.)
**So that** my manager knows I'll be unavailable

**Acceptance Criteria**:
- Select type: Vacation, Sick Leave, Holiday, Personal, Other
- Choose start and end dates
- Option for half-day (4 hours)
- Add notes/reason
- Show potential conflicts with existing allocations
- Display time-off balance (days remaining)
- Submit for manager approval

**Technical Notes**:
- Insert into Neon DB TimeOff table with status="Pending"
- Query Resource_Allocations to detect conflicts
- Calculate balance from previous time-off records
- Send notification to manager via Vercel function

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

### US-402: Approve Time-Off Request
**As a** Manager
**I want to** approve or reject time-off requests
**So that** team capacity is managed appropriately

**Acceptance Criteria**:
- View list of pending time-off requests
- See impact analysis: affected projects, team capacity
- AI suggestions for handling conflicts
- Approve, reject, or request alternate dates
- Add comment when rejecting
- Automatic capacity recalculation on approval
- Send notification to resource

**Technical Notes**:
- Update TimeOff.status in Neon DB
- Recalculate capacity for affected weeks
- Trigger notification via Vercel function
- Update approved_by and approved_date fields

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

### US-403: View Team Time-Off Calendar
**As a** Manager
**I want to** see a calendar view of my team's time-off
**So that** I can plan resource allocation accordingly

**Acceptance Criteria**:
- Calendar showing all approved time-off
- Filter by team member, type, date range
- Color-code by time-off type
- Show pending requests differently (dashed)
- Identify periods with low team capacity
- Export to PDF or iCal

**Technical Notes**:
- Query TimeOff table filtered by department/team
- Use calendar component (FullCalendar)
- Server-side render on Vercel for initial load
- Calculate team capacity % per day

**Priority**: P1 (High)
**Story Points**: 5

---

## Epic 5: Financial Management

### US-501: Set Resource Rates
**As an** Administrator
**I want to** set billable and cost rates for resources
**So that** I can track project profitability

**Acceptance Criteria**:
- Set billable rate (hourly or weekly)
- Set cost rate (internal cost)
- Select currency
- Support different rates for FTE vs. Contractor
- View rate history
- Rates apply to future allocations only (not retroactive)

**Technical Notes**:
- Store rates in Neon DB Resources table
- Snapshot rates in Resource_Allocations on creation
- Support rate history via separate RateHistory table (future)

**Priority**: P0 (Critical - MVP)
**Story Points**: 3

---

### US-502: View Project Profitability
**As a** Manager
**I want to** see real-time profitability for my projects
**So that** I can make data-driven staffing decisions

**Acceptance Criteria**:
- Display: total revenue, total cost, profit, margin %
- Show by project, resource, time period
- Color-code: 🟩 >20% margin, 🟨 10-20%, 🟥 <10%
- Drill down into cost breakdown by resource
- Compare planned vs. actual
- Export to Excel

**Technical Notes**:
- Query Neon DB Resource_Allocations
- Aggregate: SUM(calculated_revenue), SUM(calculated_cost)
- Calculate margin: (revenue - cost) / revenue * 100
- Cache calculation results for 5 minutes
- Use Vercel edge functions for fast response

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

### US-503: Track Budget Variance
**As a** Manager
**I want to** track budget vs. actual spend
**So that** I can stay within project budget

**Acceptance Criteria**:
- Display budget, actual cost, variance
- Show variance as $ amount and %
- Alert when >90% of budget used
- Project final cost based on current burn rate
- Show trend chart over time
- Identify top cost contributors

**Technical Notes**:
- Compare Projects.budget vs. SUM(allocations.calculated_cost)
- Calculate burn rate: cost per week
- Forecast: current_cost + (burn_rate * weeks_remaining)
- Real-time updates via WebSocket

**Priority**: P1 (High)
**Story Points**: 5

---

### US-504: Generate Financial Reports
**As an** Administrator
**I want to** generate financial reports across all projects
**So that** I can report to leadership

**Acceptance Criteria**:
- Reports: profitability by project, by department, by resource
- Billable vs. non-billable utilization
- Revenue trends over time
- Budget variance summary
- Export to PDF and Excel
- Schedule automated email delivery

**Technical Notes**:
- Complex aggregation queries on Neon DB
- Use Postgres materialized views for performance
- Generate PDF via puppeteer on Vercel
- Excel export via exceljs library
- Schedule via Vercel cron jobs

**Priority**: P1 (High)
**Story Points**: 8

---

## Epic 6: AI-Powered Recommendations

### US-601: Get Resource Recommendations
**As a** Manager
**I want to** receive AI suggestions for resources to allocate
**So that** I can quickly find the best matches for my project

**Acceptance Criteria**:
- Click "Suggest Resources" button on project
- Display top 5 recommended resources
- Show match score (0-100%)
- Explain reasoning: skills match, availability, past success
- Display: capacity, rate, skills
- One-click to allocate recommended resource
- Option to view more recommendations

**Technical Notes**:
- AI service deployed on Vercel serverless function
- Simple version: rule-based matching (skills + availability)
- Advanced version: ML model (TensorFlow.js or Python service)
- Query Neon DB for resource skills and capacity
- Calculate score based on: skill match (40%), availability (30%), past performance (20%), cost (10%)

**Priority**: P1 (High - differentiator)
**Story Points**: 8

---

### US-602: Provide Feedback on Recommendations
**As a** Manager
**I want to** rate AI recommendations
**So that** the system learns my preferences

**Acceptance Criteria**:
- Rate recommendation 1-5 stars after accepting/rejecting
- Provide optional text feedback
- Feedback stored for future training
- See "Why we recommended this" explanation
- Option to report bad recommendations

**Technical Notes**:
- Store feedback in Neon DB RecommendationFeedback table
- Include: recommendation_id, user_id, rating, accepted (boolean)
- Use feedback to adjust algorithm weights
- Batch process feedback for model retraining (future)

**Priority**: P2 (Medium)
**Story Points**: 3

---

### US-603: Identify Workload Imbalances
**As a** Manager
**I want to** receive AI alerts about workload imbalances
**So that** I can proactively rebalance my team

**Acceptance Criteria**:
- Alert when resources are over-allocated (>100%)
- Alert when team is under-utilized (<70%)
- Suggest reallocation to balance workload
- Show impact of suggested changes
- One-click to apply suggestion
- Dismiss or snooze alerts

**Technical Notes**:
- Background job on Vercel cron (daily)
- Analyze capacity data from Neon DB
- Calculate team average utilization
- Identify outliers (>2 std dev from mean)
- Generate rebalancing suggestions via algorithm

**Priority**: P2 (Medium)
**Story Points**: 8

---

## Epic 7: Scenario Planning

### US-701: Create Resource Allocation Scenario
**As a** Manager
**I want to** create a "what-if" scenario for resource allocation
**So that** I can plan different staffing options

**Acceptance Criteria**:
- Create new scenario with name and description
- Clone from existing scenario or baseline
- Make allocation changes within scenario
- Changes don't affect baseline/real allocations
- Save scenario for later review
- Delete scenarios I created

**Technical Notes**:
- Insert into Neon DB Scenarios table
- Clone Resource_Allocations with scenario_id
- Use database views to filter by scenario
- Mark one scenario as baseline (is_baseline=true)

**Priority**: P1 (High)
**Story Points**: 5

---

### US-702: Compare Scenarios Side-by-Side
**As a** Manager
**I want to** compare two scenarios side-by-side
**So that** I can choose the best staffing approach

**Acceptance Criteria**:
- Select two scenarios to compare
- Show differences: resource allocations, costs, utilization
- Highlight what changed (added, removed, modified)
- Display financial impact: cost difference, margin difference
- Show timeline comparison with visual diff
- Identify which scenario is better (AI suggestion)

**Technical Notes**:
- Query Neon DB for both scenario allocations
- Use SQL EXCEPT to find differences
- Calculate financial metrics for each
- Render side-by-side comparison in UI
- Use diff algorithm to highlight changes

**Priority**: P1 (High)
**Story Points**: 8

---

### US-703: Publish Scenario as Baseline
**As a** Manager
**I want to** publish a scenario as the new baseline plan
**So that** my team sees the updated allocation

**Acceptance Criteria**:
- Select scenario to publish
- Preview impact of publishing
- Confirm action (cannot undo)
- Set selected scenario as baseline
- Old baseline archived
- Notifications sent to affected resources
- Real allocations updated

**Technical Notes**:
- Update Scenarios.is_baseline in Neon DB
- Copy scenario allocations to baseline (scenario_id=NULL)
- Archive previous baseline
- Trigger notifications via Vercel function
- Use database transaction for atomicity

**Priority**: P1 (High)
**Story Points**: 5

---

## Epic 8: Workload Analysis & Reporting

### US-801: View Capacity Heatmap
**As a** Manager
**I want to** see a heatmap of team capacity over time
**So that** I can identify bottlenecks and gaps

**Acceptance Criteria**:
- Display 8-week rolling view by default
- Show each resource as row, weeks as columns
- Color-code: 🟩 <80%, 🟨 80-100%, 🟥 >100%, ⬜ time-off
- Click cell to see allocation details
- Filter by department, skills, project
- Export as image or PDF

**Technical Notes**:
- Query Neon DB Resource_Allocations by week
- Aggregate allocation % per resource per week
- Render as HTML grid with CSS colors
- Use canvas or SVG for export

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

### US-802: Generate Utilization Report
**As a** Manager
**I want to** generate utilization reports for my team
**So that** I can report on team productivity

**Acceptance Criteria**:
- Report by resource, project, department, time period
- Show: total hours, billable hours, non-billable hours
- Calculate utilization %: allocated hours / capacity hours
- Display average utilization for team
- Identify under-utilized resources (<70%)
- Export to Excel and PDF

**Technical Notes**:
- Complex aggregation query on Neon DB
- Group by resource, SUM(allocated_hours)
- Join with Resources for capacity
- Calculate: (SUM(allocated_hours) / (capacity * weeks)) * 100
- Generate Excel via exceljs on Vercel

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

### US-803: View Dashboard with Key Metrics
**As a** Manager
**I want to** see a dashboard with key metrics at a glance
**So that** I can quickly assess team status

**Acceptance Criteria**:
- Display: team utilization %, over-allocated count, upcoming time-off
- Show financial summary: budget, cost, revenue, margin
- Active projects list with progress
- Alerts: over-allocations, budget warnings
- AI recommendations panel
- 8-week capacity heatmap
- Customizable widgets

**Technical Notes**:
- Server-side render on Vercel for fast load
- Query multiple metrics from Neon DB in parallel
- Cache dashboard data for 5 minutes
- Real-time updates via WebSocket for alerts

**Priority**: P0 (Critical - MVP)
**Story Points**: 8

---

## Epic 9: User Management & Authentication

### US-901: Sign Up / Sign In
**As a** User
**I want to** sign up and sign in securely
**So that** I can access the application

**Acceptance Criteria**:
- Email + password authentication
- Password requirements: 8+ chars, uppercase, lowercase, number
- Email verification required
- "Forgot password" flow
- "Remember me" option
- SSO support (Google, Microsoft) - future

**Technical Notes**:
- Use NextAuth.js on Vercel for authentication
- Store users in Neon DB Users table
- Hash passwords with bcrypt
- Send verification email via Vercel email function
- JWT tokens with 7-day expiry

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

### US-902: Manage User Roles
**As an** Administrator
**I want to** assign roles to users (Admin, Manager, User)
**So that** they have appropriate access

**Acceptance Criteria**:
- View list of all users
- Edit user role: Admin, Manager, User
- Assign manager scope (departments they manage)
- Deactivate/reactivate users
- View audit log of role changes
- Cannot demote own admin role

**Technical Notes**:
- Update Users.role in Neon DB
- Update Users.managed_departments for managers
- Middleware checks role on each API request
- Row-level security based on scope

**Priority**: P0 (Critical - MVP)
**Story Points**: 5

---

### US-903: Audit Trail
**As an** Administrator
**I want to** view an audit trail of all changes
**So that** I can ensure accountability

**Acceptance Criteria**:
- Log: user, action, resource type, resource ID, timestamp, IP
- View logs filtered by: user, date, action type
- Search audit logs
- Export to CSV
- Logs immutable (cannot be edited/deleted)
- Retention: 2 years minimum

**Technical Notes**:
- Insert into Neon DB Audit_Log table on every mutation
- Use database triggers for automatic logging
- Index on user_id, timestamp for fast queries
- Archive old logs to cold storage (S3) after 1 year

**Priority**: P1 (High)
**Story Points**: 5

---

## Story Sizing Guide

**Story Points**:
- 1 point: Simple change, <4 hours
- 2 points: Small feature, 4-8 hours
- 3 points: Medium feature, 1-2 days
- 5 points: Large feature, 3-5 days
- 8 points: Complex feature, 1-2 weeks
- 13 points: Epic-level, break down further

**Priority Levels**:
- **P0 (Critical)**: Must-have for MVP, core functionality
- **P1 (High)**: Important differentiators, should be in MVP
- **P2 (Medium)**: Nice-to-have, can be in Phase 2
- **P3 (Low)**: Future enhancements

---

## MVP Recommendation (Phase 1)

**Core Features for MVP** (All P0 stories):
1. **Authentication**: US-901, US-902
2. **Resource Management**: US-101, US-102
3. **Project Management**: US-201, US-203
4. **Resource Booking**: US-301, US-302
5. **Time-Off**: US-401, US-402
6. **Financial**: US-501, US-502
7. **Reporting**: US-801, US-802, US-803

**Estimated MVP**: ~60 story points = 8-12 weeks with 2-3 developers

**Phase 2 Additions** (P1 stories):
- AI Recommendations (US-601, US-603)
- Scenario Planning (US-701, US-702, US-703)
- Advanced Reporting (US-504)
- Skills Management (US-103)

---

## Technical Architecture Notes

### Neon DB (Serverless Postgres)
- **Connection Pooling**: Use Neon's built-in pooling for Vercel serverless functions
- **Branching**: Use Neon branches for dev/staging/prod environments
- **Auto-scaling**: Neon scales automatically with workload
- **Backups**: Automatic daily backups, point-in-time recovery

### Vercel Deployment
- **Framework**: Next.js 14+ with App Router
- **API Routes**: Use Next.js API routes for backend logic
- **Serverless Functions**: Deploy AI/ML services as serverless functions
- **Edge Functions**: Use for real-time capacity calculations
- **Cron Jobs**: Vercel cron for scheduled tasks (reports, alerts)
- **WebSockets**: Use Vercel's WebSocket support for real-time updates

### Performance Optimization
- **Caching**: Redis (Upstash) for session and query caching
- **CDN**: Vercel Edge Network for static assets
- **Database Indexes**: Index on foreign keys, frequently queried fields
- **Materialized Views**: For complex aggregation queries
- **Pagination**: Limit queries to 25-50 records per page

---

**End of User Stories Document**

For detailed requirements, see `REQUIREMENTS.md`
For UI designs, see `UI_MOCKUPS.md`
