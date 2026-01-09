# FC Project Control - BEC Design Department

A comprehensive Next.js application for managing the BEC Design Department workflow, implementing the Design Overhaul SOP v2.0 specifications including task management, QAQC processes, category code lifecycle, and KPI dashboards.

## 🎯 Features

### Dashboard
- Real-time overview of tasks, projects, and activity
- Upcoming due dates with progress tracking
- Recent activity feed
- Project status overview with budget utilization

### Task Queue
- **My Queue / Team Queue** views for personalized workflow management
- **Priority System** (-20 to 20):
  - Negative priorities (-20 to -1): Revisions requiring 2-day turnaround
  - Positive priorities (1-20): Standard work with 1 being highest priority
- Progress tracking (0%, 20%, 40%, 60%, 80%, 100%)
- Task status workflow: New → In Production → Review → Approved/Denied
- Search and filter capabilities
- Add new tasks with all required fields per SOP

### Projects
- Project cards with Job.Phase identification
- Category code lifecycle visualization (E → EQ/EC → E1 → E1Q/E1C → etc.)
- Budget utilization tracking
- Panel type indicators (New Panel / TI)
- QAQC requirement status
- File storage links (J-Drive / I-Drive)

### Review Queue
- Tasks at 100% awaiting approval
- **Approval Actions**:
  - Approve for Submission
  - Approve for Comments
  - Approve and Close
  - Deny (with required reason and attachment)
- Denial workflow with automatic priority assignment
- Prior denial count tracking

### Activity Log
- Comprehensive audit trail
- Action types tracked:
  - TASK_CREATED, TASK_DENIED, TASK_100_PERCENT
  - CODE_CREATED, QAQC_BYPASSED, QAQC_COMPLETED
  - AE_RELEASED, SUBMITTED_APPROVAL
- Filterable by action type
- Exportable log data

### Designer KPIs
- On-Time Task Completion Rate
- Average Days Early/Late
- Budget Adherence (E hours vs budget)
- Denial Rate & Average Denials per Task
- Revision Turnaround Time
- Weekly Throughput Charts
- Queue Depth Visualization

### PM KPIs
- First-Time Approval Rate (with 80% threshold warning)
- Bypass Frequency (90-day rolling)
- Bypass Cost Ratio (Q hrs ÷ base hrs)
- Correction Cycle Count
- Submission & Approval Turnaround Times
- DRFC Frequency
- Active Projects Breakdown

### Operations Dashboard
- Department-wide queue health
- On-Time Delivery Rate
- Budget Performance
- QAQC Compliance Rate
- Cost Attribution (Q Code vs C Code vs Revisions)
- Resource Utilization by Designer
- Material Overages (>15% threshold)

## 📋 Category Code System (per SOP)

| Code | Name | Purpose | Has Budget |
|------|------|---------|------------|
| E | ENGINEERING LABOR | Base design | ✓ |
| EQ | ENGINEERING QSKIPPED | E corrections (QAQC bypassed) | ✗ |
| EC | ENGINEERING CORRECTION | E corrections (QAQC performed) | ✗ |
| E1 | R1 ENGR LABOR | Revision cycle 1 | ✓ |
| E1Q | R1 ENGR QSKIPPED | E1 corrections (QAQC bypassed) | ✗ |
| E1C | R1 ENGR CORRECTION | E1 corrections (QAQC performed) | ✗ |
| E2 | R2 ENGR LABOR | Revision cycle 2 | ✓ |
| AE | AS-BUILT ENGR LABOR | As-built engineering | ✓ |
| AEQ | AS-BUILT ENGR QSKIPPED | AE corrections (QAQC bypassed) | ✗ |
| AEC | AS-BUILT ENGR CORRECTION | AE corrections (QAQC performed) | ✗ |

**Key Rules:**
- Q and C codes are mutually exclusive per cycle
- Only one base code (E, E1, E2) can be open at a time
- Q/C codes can remain open while next base code is active

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- npm or yarn

### Installation

```bash
npm install
```

### Development

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Build

```bash
npm run build
```

### Production

```bash
npm start
```

## 🛠 Tech Stack

- **Framework**: Next.js 14
- **Styling**: Tailwind CSS
- **Charts**: Recharts
- **Icons**: Lucide React
- **Fonts**: Inter (Google Fonts)

## 📁 Project Structure

```
fc-pc-app/
├── app/
│   ├── globals.css      # Tailwind imports & custom styles
│   ├── layout.jsx       # Root layout with metadata
│   └── page.jsx         # Main application (all views)
├── package.json
├── tailwind.config.js   # Tailwind configuration
├── postcss.config.js
├── next.config.js
├── jsconfig.json
└── README.md
```

## 📊 SOP Compliance

This application implements the following SOP sections:

- **Section 10**: Task Management SOP (Add Task, Priority System, Review Workflow)
- **Section 12**: QAQC and Submission Process
- **Section 14**: Activity Logging
- **Section 17**: Key Performance Indicators
- **Section 17.4**: KPI Dashboards

## 🔐 Role-Based Access

| Role | Dashboard Access |
|------|-----------------|
| Designer | Own metrics (with team comparison) |
| PM | Own metrics + managed projects |
| JCA | All Designer and PM dashboards |
| Design Manager | All Designer dashboards + Operations |
| Operations/VP/FC | Full access to all dashboards |

## 📝 Task Status Flow

```
New → In Production → Review → Approved
                         ↓
                       Denied → In Production (at 80%)
```

## 🎨 Design System

- **Colors**: Slate-based neutral palette with blue primary accent
- **Typography**: Inter font family
- **Spacing**: Consistent 4px grid system
- **Components**: Cards, badges, progress bars, modals, tables
- **Animations**: Subtle transitions and hover effects

## 🚢 Deployment

### Vercel (Recommended)
1. Push to GitHub
2. Import project in Vercel
3. Deploy automatically

### Netlify
1. Push to GitHub
2. Import project in Netlify
3. Set build command: `npm run build`
4. Set publish directory: `.next`

### Docker
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

## 📞 Support

For questions about the SOP or application features, contact the Design Department.

---

**Version**: 2.0.0  
**Effective Date**: January 9, 2026  
**System of Record**: FieldConnection – Project Control (FC-PC)
