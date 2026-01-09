"use client";

import React, { useState, useEffect } from 'react';
import { BarChart, Bar, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer, PieChart, Pie, Cell, LineChart, Line, Legend, Area, AreaChart } from 'recharts';
import { 
  CheckCircle, XCircle, Clock, AlertTriangle, Users, Briefcase, FileText, Plus, Search, Filter, Bell, Settings, Home, List, BarChart2, Calendar, Send, Eye, ArrowUp, ArrowDown, ChevronRight, ChevronDown, Upload, Download, Link2, FolderOpen, Edit3, Trash2, Save, X, RefreshCw, AlertCircle, CheckSquare, Square, MessageSquare, Paperclip, Activity, TrendingUp, TrendingDown, Target, Zap, Shield, FileCheck, Building, MapPin, Hash, Layers, GitBranch, ClipboardCheck, PlayCircle, PauseCircle, SkipForward, Flag, Archive, MoreVertical, ExternalLink, Copy, Info
} from 'lucide-react';

// ============================================
// MOCK DATA - Comprehensive data based on SOP
// ============================================

const mockSiteCodes = [
  { code: 'SG0481', name: '1950 AVENUE OF THE STARS', address: '1950 Avenue of the Stars, Los Angeles, CA 90067' },
  { code: 'SG0482', name: 'CENTURY PLAZA TOWER', address: '2049 Century Park E, Los Angeles, CA 90067' },
  { code: 'SG0480', name: 'WESTFIELD MALL', address: '10250 Santa Monica Blvd, Los Angeles, CA 90067' },
];

const mockDesigners = [
  { id: 1, name: 'John Smith', avatar: 'JS', email: 'john.smith@bec.com', utilization: 85 },
  { id: 2, name: 'Maria Garcia', avatar: 'MG', email: 'maria.garcia@bec.com', utilization: 72 },
  { id: 3, name: 'David Chen', avatar: 'DC', email: 'david.chen@bec.com', utilization: 91 },
  { id: 4, name: 'Sarah Kim', avatar: 'SK', email: 'sarah.kim@bec.com', utilization: 78 },
];

const mockPMs = [
  { id: 1, name: 'Sarah Johnson', avatar: 'SJ', email: 'sarah.johnson@bec.com' },
  { id: 2, name: 'Mike Williams', avatar: 'MW', email: 'mike.williams@bec.com' },
  { id: 3, name: 'Lisa Anderson', avatar: 'LA', email: 'lisa.anderson@bec.com' },
];

const mockProjects = [
  { 
    job: 'G22104', 
    phase: '00', 
    name: '1950 Avenue of the Stars', 
    site: 'SG0481', 
    pm: 'Sarah Johnson', 
    designer: 'John Smith', 
    status: 'In Production', 
    catCodes: ['E', 'EC'],
    openCatCodes: ['E'],
    panelType: 'New Panel',
    projectStart: '2025-12-01',
    projectEnd: '2026-03-15',
    designEnd: '2026-01-20',
    designStart: '2025-12-15',
    budgetHours: 80,
    actualHours: 52,
    qaqcRequired: true
  },
  { 
    job: 'G22105', 
    phase: '01', 
    name: 'Century Plaza Tower B', 
    site: 'SG0482', 
    pm: 'Mike Williams', 
    designer: 'Maria Garcia', 
    status: 'In Production', 
    catCodes: ['E', 'EQ', 'E1'],
    openCatCodes: ['E1'],
    panelType: 'TI',
    projectStart: '2025-11-15',
    projectEnd: '2026-04-01',
    designEnd: '2026-01-25',
    designStart: '2025-12-01',
    budgetHours: 120,
    actualHours: 95,
    qaqcRequired: false
  },
  { 
    job: 'G22103', 
    phase: '00', 
    name: 'Westfield Mall Expansion', 
    site: 'SG0480', 
    pm: 'Sarah Johnson', 
    designer: 'David Chen', 
    status: 'AE Released', 
    catCodes: ['E', 'EC', 'E1', 'E1C', 'AE'],
    openCatCodes: ['AE'],
    panelType: 'New Panel',
    projectStart: '2025-09-01',
    projectEnd: '2026-02-28',
    designEnd: '2025-12-15',
    designStart: '2025-10-01',
    budgetHours: 160,
    actualHours: 148,
    qaqcRequired: true
  },
  { 
    job: 'G22106', 
    phase: '00', 
    name: 'Beverly Center Renovation', 
    site: 'SG0483', 
    pm: 'Lisa Anderson', 
    designer: 'Sarah Kim', 
    status: 'QAQC', 
    catCodes: ['E'],
    openCatCodes: ['E'],
    panelType: 'TI',
    projectStart: '2025-12-10',
    projectEnd: '2026-05-01',
    designEnd: '2026-02-01',
    designStart: '2025-12-20',
    budgetHours: 64,
    actualHours: 58,
    qaqcRequired: false
  },
];

const mockTasks = [
  { 
    id: 1, 
    taskNum: '0001', 
    title: 'Panel Layout - Main Building', 
    description: 'Create panel schedule and layout for main electrical room',
    job: 'G22104', 
    phase: '00', 
    catCode: 'E', 
    status: 'In Production', 
    priority: 1, 
    progress: 60, 
    designer: 'John Smith', 
    pm: 'Sarah Johnson', 
    dueDate: '2026-01-15',
    originalDueDate: '2026-01-15',
    delta: '0',
    pcoNumber: '',
    denialCount: 0,
    createdAt: '2025-12-15',
    lastUpdated: '2026-01-08'
  },
  { 
    id: 2, 
    taskNum: '0002', 
    title: 'Riser Diagram', 
    description: 'Complete electrical riser diagram showing all vertical feeds',
    job: 'G22104', 
    phase: '00', 
    catCode: 'E', 
    status: 'Review', 
    priority: 2, 
    progress: 100, 
    designer: 'John Smith', 
    pm: 'Sarah Johnson', 
    dueDate: '2026-01-12',
    originalDueDate: '2026-01-12',
    delta: '0',
    pcoNumber: '',
    denialCount: 0,
    createdAt: '2025-12-15',
    lastUpdated: '2026-01-09'
  },
  { 
    id: 3, 
    taskNum: '0003', 
    title: 'Load Calculations', 
    description: 'Perform load calculations per NEC requirements',
    job: 'G22104', 
    phase: '00', 
    catCode: 'E', 
    status: 'In Production', 
    priority: -1, 
    progress: 80, 
    designer: 'John Smith', 
    pm: 'Sarah Johnson', 
    dueDate: '2026-01-10',
    originalDueDate: '2026-01-08',
    delta: '0',
    pcoNumber: '',
    denialCount: 1,
    denialReason: 'Verify breaker sizing per NEC 220.87',
    createdAt: '2025-12-15',
    lastUpdated: '2026-01-09'
  },
  { 
    id: 4, 
    taskNum: '0004', 
    title: 'One-Line Diagram', 
    description: 'Create single-line diagram for electrical distribution',
    job: 'G22105', 
    phase: '01', 
    catCode: 'E1', 
    status: 'New', 
    priority: 3, 
    progress: 0, 
    designer: 'Maria Garcia', 
    pm: 'Mike Williams', 
    dueDate: '2026-01-18',
    originalDueDate: '2026-01-18',
    delta: '1',
    pcoNumber: 'PCO-2024-001',
    denialCount: 0,
    createdAt: '2026-01-05',
    lastUpdated: '2026-01-05'
  },
  { 
    id: 5, 
    taskNum: '0005', 
    title: 'Arc Flash Study', 
    description: 'Perform arc flash hazard analysis and labeling requirements',
    job: 'G22105', 
    phase: '01', 
    catCode: 'E1', 
    status: 'In Production', 
    priority: 4, 
    progress: 40, 
    designer: 'Maria Garcia', 
    pm: 'Mike Williams', 
    dueDate: '2026-01-20',
    originalDueDate: '2026-01-20',
    delta: '1',
    pcoNumber: '',
    denialCount: 0,
    createdAt: '2026-01-05',
    lastUpdated: '2026-01-08'
  },
  { 
    id: 6, 
    taskNum: '0006', 
    title: 'As-Built Updates', 
    description: 'Update drawings to reflect field conditions',
    job: 'G22103', 
    phase: '00', 
    catCode: 'AE', 
    status: 'In Production', 
    priority: 5, 
    progress: 20, 
    designer: 'David Chen', 
    pm: 'Sarah Johnson', 
    dueDate: '2026-01-22',
    originalDueDate: '2026-01-22',
    delta: '0',
    pcoNumber: '',
    denialCount: 0,
    createdAt: '2026-01-02',
    lastUpdated: '2026-01-07'
  },
  { 
    id: 7, 
    taskNum: '0007', 
    title: 'Lighting Layout', 
    description: 'Design lighting layout for retail space',
    job: 'G22106', 
    phase: '00', 
    catCode: 'E', 
    status: 'Review', 
    priority: 6, 
    progress: 100, 
    designer: 'Sarah Kim', 
    pm: 'Lisa Anderson', 
    dueDate: '2026-01-14',
    originalDueDate: '2026-01-14',
    delta: '0',
    pcoNumber: '',
    denialCount: 0,
    createdAt: '2025-12-20',
    lastUpdated: '2026-01-09'
  },
  { 
    id: 8, 
    taskNum: '0008', 
    title: 'Emergency Power System', 
    description: 'Design emergency power distribution and transfer switch',
    job: 'G22104', 
    phase: '00', 
    catCode: 'E', 
    status: 'New', 
    priority: 7, 
    progress: 0, 
    designer: 'John Smith', 
    pm: 'Sarah Johnson', 
    dueDate: '2026-01-25',
    originalDueDate: '2026-01-25',
    delta: '0',
    pcoNumber: '',
    denialCount: 0,
    createdAt: '2026-01-08',
    lastUpdated: '2026-01-08'
  },
];

const mockActivityLog = [
  { id: 1, jobPhase: 'G22104.00', action: 'TASK_CREATED', user: 'Sarah Johnson', timestamp: '2026-01-08 09:15:00', notes: 'Created Emergency Power System task' },
  { id: 2, jobPhase: 'G22104.00', action: 'TASK_DENIED', catCode: 'E', user: 'Sarah Johnson', timestamp: '2026-01-09 08:30:00', notes: 'Load Calculations denied - Verify breaker sizing per NEC 220.87' },
  { id: 3, jobPhase: 'G22105.01', action: 'CODE_CREATED', catCode: 'E1', user: 'Mike Williams', timestamp: '2026-01-05 10:00:00', notes: 'Created E1 revision code after stakeholder comments' },
  { id: 4, jobPhase: 'G22105.01', action: 'QAQC_BYPASSED', catCode: 'E', user: 'Mike Williams', timestamp: '2026-01-04 14:30:00', notes: 'QAQC bypassed for TI project' },
  { id: 5, jobPhase: 'G22103.00', action: 'AE_RELEASED', catCode: 'AE', user: 'Sarah Johnson', timestamp: '2026-01-02 11:00:00', notes: 'Released to As-Built engineering' },
  { id: 6, jobPhase: 'G22106.00', action: 'TASK_100_PERCENT', catCode: 'E', user: 'Sarah Kim', timestamp: '2026-01-09 16:45:00', notes: 'Lighting Layout marked 100% complete' },
];

const mockDueDateChanges = [
  { id: 1, taskId: 3, jobPhase: 'G22104.00', taskTitle: 'Load Calculations', originalDue: '2026-01-08', requestedDue: '2026-01-10', reason: 'Additional NEC verification required after denial', requestedBy: 'John Smith', requestedAt: '2026-01-09', status: 'Pending' },
];

// Category Code definitions from SOP
const CATEGORY_CODES = {
  'E': { name: 'ENGINEERING LABOR', purpose: 'Base design', hasBudget: true },
  'EQ': { name: 'ENGINEERING QSKIPPED', purpose: 'E corrections (QAQC bypassed)', hasBudget: false },
  'EC': { name: 'ENGINEERING CORRECTION', purpose: 'E corrections (QAQC performed)', hasBudget: false },
  'E1': { name: 'R1 ENGR LABOR', purpose: 'Revision cycle 1', hasBudget: true },
  'E1Q': { name: 'R1 ENGR QSKIPPED', purpose: 'E1 corrections (QAQC bypassed)', hasBudget: false },
  'E1C': { name: 'R1 ENGR CORRECTION', purpose: 'E1 corrections (QAQC performed)', hasBudget: false },
  'E2': { name: 'R2 ENGR LABOR', purpose: 'Revision cycle 2', hasBudget: true },
  'E2Q': { name: 'R2 ENGR QSKIPPED', purpose: 'E2 corrections (QAQC bypassed)', hasBudget: false },
  'E2C': { name: 'R2 ENGR CORRECTION', purpose: 'E2 corrections (QAQC performed)', hasBudget: false },
  'AE': { name: 'AS-BUILT ENGR LABOR', purpose: 'As-built engineering', hasBudget: true },
  'AEQ': { name: 'AS-BUILT ENGR QSKIPPED', purpose: 'AE corrections (QAQC bypassed)', hasBudget: false },
  'AEC': { name: 'AS-BUILT ENGR CORRECTION', purpose: 'AE corrections (QAQC performed)', hasBudget: false },
};

// KPI Data
const designerKPIData = {
  'John Smith': {
    onTimeRate: 87,
    avgDaysEarlyLate: -1.2,
    budgetAdherence: 94,
    denialRate: 12,
    avgDenialsPerTask: 0.15,
    revisionTurnaround: 1.5,
    weeklyThroughput: [
      { week: 'W1', tasks: 8 },
      { week: 'W2', tasks: 12 },
      { week: 'W3', tasks: 10 },
      { week: 'W4', tasks: 14 },
    ],
    queueDepth: { revisions: 1, highPriority: 3, normal: 2 }
  },
  'Maria Garcia': {
    onTimeRate: 92,
    avgDaysEarlyLate: -0.5,
    budgetAdherence: 89,
    denialRate: 8,
    avgDenialsPerTask: 0.10,
    revisionTurnaround: 1.2,
    weeklyThroughput: [
      { week: 'W1', tasks: 6 },
      { week: 'W2', tasks: 9 },
      { week: 'W3', tasks: 11 },
      { week: 'W4', tasks: 8 },
    ],
    queueDepth: { revisions: 0, highPriority: 2, normal: 3 }
  },
  'David Chen': {
    onTimeRate: 95,
    avgDaysEarlyLate: -2.1,
    budgetAdherence: 98,
    denialRate: 5,
    avgDenialsPerTask: 0.05,
    revisionTurnaround: 1.0,
    weeklyThroughput: [
      { week: 'W1', tasks: 10 },
      { week: 'W2', tasks: 14 },
      { week: 'W3', tasks: 12 },
      { week: 'W4', tasks: 16 },
    ],
    queueDepth: { revisions: 0, highPriority: 1, normal: 1 }
  },
  'Sarah Kim': {
    onTimeRate: 84,
    avgDaysEarlyLate: 0.8,
    budgetAdherence: 91,
    denialRate: 15,
    avgDenialsPerTask: 0.18,
    revisionTurnaround: 1.8,
    weeklyThroughput: [
      { week: 'W1', tasks: 5 },
      { week: 'W2', tasks: 7 },
      { week: 'W3', tasks: 8 },
      { week: 'W4', tasks: 6 },
    ],
    queueDepth: { revisions: 0, highPriority: 1, normal: 2 }
  }
};

const pmKPIData = {
  'Sarah Johnson': {
    bypassFrequency: 1,
    bypassCostRatio: 4.2,
    firstTimeApprovalRate: 88,
    correctionCycleCount: 1.1,
    submissionTurnaround: 1.8,
    approvalTurnaround: 3.5,
    drfcFrequency: 2,
    taskReclassificationRate: 0.5,
    activeProjects: 5,
    projectBreakdown: { inProduction: 3, review: 1, ae: 1 }
  },
  'Mike Williams': {
    bypassFrequency: 3,
    bypassCostRatio: 12.5,
    firstTimeApprovalRate: 72,
    correctionCycleCount: 1.8,
    submissionTurnaround: 2.5,
    approvalTurnaround: 5.2,
    drfcFrequency: 4,
    taskReclassificationRate: 1.2,
    activeProjects: 4,
    projectBreakdown: { inProduction: 3, review: 0, ae: 1 }
  },
  'Lisa Anderson': {
    bypassFrequency: 0,
    bypassCostRatio: 0,
    firstTimeApprovalRate: 95,
    correctionCycleCount: 0.8,
    submissionTurnaround: 1.5,
    approvalTurnaround: 2.8,
    drfcFrequency: 1,
    taskReclassificationRate: 0.2,
    activeProjects: 3,
    projectBreakdown: { inProduction: 2, review: 1, ae: 0 }
  }
};

const operationsData = {
  queueHealth: { new: 12, inProduction: 28, review: 5 },
  onTimeDelivery: 85,
  budgetPerformance: 92,
  qaqcCompliance: 78,
  bypassCostImpact: 156,
  correctionLoad: 89,
  revisionVolume: 234,
  overdueCount: 4,
};

// ============================================
// UTILITY FUNCTIONS
// ============================================

const STATUS_COLORS = {
  'New': 'bg-blue-100 text-blue-800 border-blue-200',
  'In Production': 'bg-amber-100 text-amber-800 border-amber-200',
  'Review': 'bg-violet-100 text-violet-800 border-violet-200',
  'Approved': 'bg-emerald-100 text-emerald-800 border-emerald-200',
  'Denied': 'bg-rose-100 text-rose-800 border-rose-200',
  'QAQC': 'bg-indigo-100 text-indigo-800 border-indigo-200',
  'Submitted': 'bg-cyan-100 text-cyan-800 border-cyan-200',
  'AE Released': 'bg-teal-100 text-teal-800 border-teal-200',
  'Closed': 'bg-slate-100 text-slate-800 border-slate-200',
  'Released': 'bg-sky-100 text-sky-800 border-sky-200',
};

const PHASE_STATUS_COLORS = {
  'Released': 'bg-sky-500',
  'In Production': 'bg-amber-500',
  'QAQC': 'bg-indigo-500',
  'Submitted': 'bg-cyan-500',
  'AE Released': 'bg-teal-500',
  'Closed': 'bg-slate-500',
};

const formatDate = (dateStr) => {
  if (!dateStr) return '-';
  const date = new Date(dateStr);
  return date.toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' });
};

const getDaysUntilDue = (dueDate) => {
  const today = new Date();
  const due = new Date(dueDate);
  const diff = Math.ceil((due - today) / (1000 * 60 * 60 * 24));
  return diff;
};

// ============================================
// COMPONENTS
// ============================================

// Sidebar Component
const Sidebar = ({ activeView, setActiveView, currentUser }) => {
  const menuItems = [
    { id: 'dashboard', label: 'Dashboard', icon: Home },
    { id: 'tasks', label: 'Task Queue', icon: List },
    { id: 'projects', label: 'Projects', icon: Briefcase },
    { id: 'review', label: 'Review Queue', icon: CheckCircle, badge: 2 },
    { id: 'activity', label: 'Activity Log', icon: Activity },
    { id: 'designer-kpi', label: 'Designer KPIs', icon: BarChart2 },
    { id: 'pm-kpi', label: 'PM KPIs', icon: Target },
    { id: 'operations', label: 'Operations', icon: Users },
  ];

  return (
    <div className="w-60 bg-gradient-to-b from-slate-900 via-slate-900 to-slate-800 text-white flex flex-col shadow-xl">
      <div className="p-4 border-b border-slate-700/50">
        <div className="flex items-center gap-2">
          <div className="w-9 h-9 bg-gradient-to-br from-blue-500 to-blue-600 rounded-lg flex items-center justify-center shadow-lg">
            <Zap size={20} className="text-white" />
          </div>
          <div>
            <h1 className="text-base font-bold tracking-tight">FC Project Control</h1>
            <p className="text-slate-400 text-[10px] uppercase tracking-wider">BEC Design Department</p>
          </div>
        </div>
      </div>
      
      <nav className="flex-1 p-3 space-y-1">
        {menuItems.map(item => (
          <button
            key={item.id}
            onClick={() => setActiveView(item.id)}
            className={`w-full flex items-center justify-between px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 ${
              activeView === item.id 
                ? 'bg-blue-600 text-white shadow-lg shadow-blue-600/30' 
                : 'text-slate-300 hover:bg-slate-800/80 hover:text-white'
            }`}
          >
            <div className="flex items-center gap-3">
              <item.icon size={18} className={activeView === item.id ? 'text-blue-200' : ''} />
              {item.label}
            </div>
            {item.badge && (
              <span className={`px-2 py-0.5 rounded-full text-xs font-bold ${
                activeView === item.id ? 'bg-white/20 text-white' : 'bg-rose-500 text-white'
              }`}>
                {item.badge}
              </span>
            )}
          </button>
        ))}
      </nav>
      
      <div className="p-3 border-t border-slate-700/50">
        <div className="flex items-center gap-3 px-3 py-2 rounded-lg bg-slate-800/50">
          <div className="w-9 h-9 bg-gradient-to-br from-emerald-500 to-emerald-600 rounded-full flex items-center justify-center text-sm font-bold shadow-lg">
            {currentUser.avatar}
          </div>
          <div className="flex-1 min-w-0">
            <p className="text-sm font-medium truncate">{currentUser.name}</p>
            <p className="text-slate-400 text-xs">{currentUser.role}</p>
          </div>
        </div>
      </div>
    </div>
  );
};

// Header Component
const Header = ({ title, subtitle, actions }) => (
  <div className="bg-white border-b border-slate-200 px-6 py-4 flex items-center justify-between">
    <div>
      <h2 className="text-xl font-bold text-slate-800">{title}</h2>
      {subtitle && <p className="text-slate-500 text-sm mt-0.5">{subtitle}</p>}
    </div>
    <div className="flex items-center gap-3">
      {actions}
      <button className="p-2 hover:bg-slate-100 rounded-lg relative transition-colors">
        <Bell size={20} className="text-slate-600" />
        <span className="absolute top-1 right-1 w-2 h-2 bg-rose-500 rounded-full"></span>
      </button>
      <button className="p-2 hover:bg-slate-100 rounded-lg transition-colors">
        <Settings size={20} className="text-slate-600" />
      </button>
    </div>
  </div>
);

// Stat Card Component
const StatCard = ({ title, value, subtitle, icon: Icon, trend, trendLabel, color = 'blue', className = '' }) => {
  const colorClasses = {
    blue: 'from-blue-500 to-blue-600',
    green: 'from-emerald-500 to-emerald-600',
    amber: 'from-amber-500 to-amber-600',
    rose: 'from-rose-500 to-rose-600',
    violet: 'from-violet-500 to-violet-600',
    cyan: 'from-cyan-500 to-cyan-600',
  };

  return (
    <div className={`bg-white rounded-xl shadow-sm border border-slate-200 p-5 ${className}`}>
      <div className="flex items-start justify-between">
        <div className="flex-1">
          <p className="text-slate-500 text-xs font-medium uppercase tracking-wide">{title}</p>
          <p className="text-2xl font-bold mt-2 text-slate-900">{value}</p>
          {subtitle && <p className="text-slate-400 text-xs mt-1">{subtitle}</p>}
          {trend !== undefined && (
            <div className={`flex items-center gap-1 mt-2 text-xs font-medium ${trend >= 0 ? 'text-emerald-600' : 'text-rose-600'}`}>
              {trend >= 0 ? <TrendingUp size={14} /> : <TrendingDown size={14} />}
              {Math.abs(trend)}% {trendLabel || 'vs last period'}
            </div>
          )}
        </div>
        <div className={`p-3 rounded-xl bg-gradient-to-br ${colorClasses[color]} shadow-lg`}>
          <Icon size={22} className="text-white" />
        </div>
      </div>
    </div>
  );
};

// Progress Bar Component
const ProgressBar = ({ value, size = 'md', showLabel = true, color = 'blue' }) => {
  const heights = { sm: 'h-1.5', md: 'h-2', lg: 'h-3' };
  const colors = {
    blue: 'bg-blue-500',
    green: 'bg-emerald-500',
    amber: 'bg-amber-500',
    rose: 'bg-rose-500',
  };
  const bgColors = {
    blue: 'bg-blue-100',
    green: 'bg-emerald-100',
    amber: 'bg-amber-100',
    rose: 'bg-rose-100',
  };

  const progressColor = value === 100 ? 'green' : value >= 80 ? 'blue' : color;

  return (
    <div className="flex items-center gap-2">
      <div className={`flex-1 ${bgColors[progressColor]} rounded-full ${heights[size]}`}>
        <div 
          className={`${heights[size]} ${colors[progressColor]} rounded-full transition-all duration-300`}
          style={{ width: `${Math.min(value, 100)}%` }}
        />
      </div>
      {showLabel && <span className="text-xs font-medium text-slate-500 w-8">{value}%</span>}
    </div>
  );
};

// Badge Component
const Badge = ({ children, variant = 'default', size = 'md' }) => {
  const variants = {
    default: 'bg-slate-100 text-slate-700',
    primary: 'bg-blue-100 text-blue-700',
    success: 'bg-emerald-100 text-emerald-700',
    warning: 'bg-amber-100 text-amber-700',
    danger: 'bg-rose-100 text-rose-700',
    info: 'bg-cyan-100 text-cyan-700',
  };
  const sizes = {
    sm: 'px-1.5 py-0.5 text-[10px]',
    md: 'px-2 py-1 text-xs',
    lg: 'px-3 py-1.5 text-sm',
  };

  return (
    <span className={`inline-flex items-center font-medium rounded-full ${variants[variant]} ${sizes[size]}`}>
      {children}
    </span>
  );
};

// Modal Component
const Modal = ({ isOpen, onClose, title, children, size = 'md' }) => {
  if (!isOpen) return null;
  
  const sizes = {
    sm: 'max-w-md',
    md: 'max-w-lg',
    lg: 'max-w-2xl',
    xl: 'max-w-4xl',
  };

  return (
    <div className="fixed inset-0 z-50 overflow-y-auto">
      <div className="fixed inset-0 bg-black/50 backdrop-blur-sm" onClick={onClose} />
      <div className="relative min-h-full flex items-center justify-center p-4">
        <div className={`relative bg-white rounded-2xl shadow-2xl w-full ${sizes[size]} transform transition-all`}>
          <div className="flex items-center justify-between p-5 border-b border-slate-200">
            <h3 className="text-lg font-bold text-slate-900">{title}</h3>
            <button onClick={onClose} className="p-2 hover:bg-slate-100 rounded-lg transition-colors">
              <X size={20} className="text-slate-500" />
            </button>
          </div>
          <div className="p-5">{children}</div>
        </div>
      </div>
    </div>
  );
};

// ============================================
// VIEW COMPONENTS
// ============================================

// Dashboard View
const DashboardView = ({ tasks, projects }) => {
  const reviewTasks = tasks.filter(t => t.status === 'Review');
  const overdueTasks = tasks.filter(t => getDaysUntilDue(t.dueDate) < 0 && t.status !== 'Approved');
  const completedThisWeek = 18; // Mock data
  
  const recentActivity = [
    { action: 'Task approved', task: 'Load Calculations', user: 'Sarah Johnson', time: '10 min ago', icon: CheckCircle, color: 'emerald' },
    { action: 'Task denied', task: 'Panel Layout', user: 'Mike Williams', time: '25 min ago', icon: XCircle, color: 'rose' },
    { action: 'QAQC bypassed', task: 'G22105.01', user: 'Mike Williams', time: '1 hr ago', icon: AlertTriangle, color: 'amber' },
    { action: 'New task created', task: 'Arc Flash Study', user: 'Sarah Johnson', time: '2 hrs ago', icon: Plus, color: 'blue' },
    { action: 'Task marked 100%', task: 'Lighting Layout', user: 'Sarah Kim', time: '3 hrs ago', icon: CheckSquare, color: 'violet' },
  ];

  const upcomingTasks = tasks.filter(t => t.status !== 'Approved').sort((a, b) => new Date(a.dueDate) - new Date(b.dueDate)).slice(0, 5);

  return (
    <div className="p-6 space-y-6">
      {/* Stats Grid */}
      <div className="grid grid-cols-4 gap-4">
        <StatCard 
          title="Tasks in Queue" 
          value={tasks.filter(t => t.status !== 'Approved').length} 
          subtitle="12 new this week" 
          icon={List} 
          color="blue"
        />
        <StatCard 
          title="Awaiting Review" 
          value={reviewTasks.length} 
          subtitle="Ready for approval" 
          icon={Eye} 
          color="violet"
        />
        <StatCard 
          title="Overdue Tasks" 
          value={overdueTasks.length} 
          subtitle="Needs attention" 
          icon={AlertTriangle} 
          color="rose"
        />
        <StatCard 
          title="Completed This Week" 
          value={completedThisWeek} 
          subtitle="+23% vs last week" 
          icon={CheckCircle} 
          trend={23}
          color="green"
        />
      </div>

      {/* Main Content Grid */}
      <div className="grid grid-cols-3 gap-6">
        {/* Recent Activity */}
        <div className="col-span-2 bg-white rounded-xl shadow-sm border border-slate-200">
          <div className="p-5 border-b border-slate-100">
            <div className="flex items-center justify-between">
              <h3 className="font-bold text-slate-900">Recent Activity</h3>
              <button className="text-sm text-blue-600 hover:text-blue-700 font-medium">View All</button>
            </div>
          </div>
          <div className="divide-y divide-slate-100">
            {recentActivity.map((item, i) => (
              <div key={i} className="p-4 flex items-start gap-4 hover:bg-slate-50 transition-colors">
                <div className={`p-2 rounded-lg bg-${item.color}-100`}>
                  <item.icon size={16} className={`text-${item.color}-600`} />
                </div>
                <div className="flex-1 min-w-0">
                  <p className="font-medium text-slate-900">{item.action}</p>
                  <p className="text-slate-500 text-sm">{item.task} • {item.user}</p>
                </div>
                <span className="text-slate-400 text-xs whitespace-nowrap">{item.time}</span>
              </div>
            ))}
          </div>
        </div>

        {/* Upcoming Due Dates */}
        <div className="bg-white rounded-xl shadow-sm border border-slate-200">
          <div className="p-5 border-b border-slate-100">
            <h3 className="font-bold text-slate-900">Upcoming Due Dates</h3>
          </div>
          <div className="divide-y divide-slate-100">
            {upcomingTasks.map(task => {
              const daysUntil = getDaysUntilDue(task.dueDate);
              const isOverdue = daysUntil < 0;
              const isUrgent = daysUntil >= 0 && daysUntil <= 2;
              
              return (
                <div key={task.id} className="p-4 hover:bg-slate-50 transition-colors">
                  <div className="flex items-start justify-between gap-3">
                    <div className="flex-1 min-w-0">
                      <p className="font-medium text-slate-900 truncate">{task.title}</p>
                      <p className="text-slate-500 text-xs mt-0.5">{task.job}.{task.phase} • {task.designer}</p>
                    </div>
                    <div className="text-right shrink-0">
                      <p className={`text-sm font-medium ${isOverdue ? 'text-rose-600' : isUrgent ? 'text-amber-600' : 'text-slate-700'}`}>
                        {formatDate(task.dueDate)}
                      </p>
                      <ProgressBar value={task.progress} size="sm" showLabel={false} />
                    </div>
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      </div>

      {/* Project Status Overview */}
      <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
        <h3 className="font-bold text-slate-900 mb-4">Project Status Overview</h3>
        <div className="grid grid-cols-4 gap-4">
          {projects.slice(0, 4).map(project => (
            <div key={`${project.job}-${project.phase}`} className="p-4 bg-slate-50 rounded-xl border border-slate-200">
              <div className="flex items-center justify-between mb-3">
                <span className="font-bold text-slate-900">{project.job}.{project.phase}</span>
                <span className={`px-2 py-0.5 rounded-full text-xs font-medium ${STATUS_COLORS[project.status]}`}>
                  {project.status}
                </span>
              </div>
              <p className="text-sm text-slate-600 truncate mb-2">{project.name}</p>
              <div className="flex items-center gap-2 text-xs text-slate-500">
                <span>{project.designer}</span>
                <span>•</span>
                <span>{Math.round((project.actualHours / project.budgetHours) * 100)}% budget</span>
              </div>
              <div className="mt-3">
                <ProgressBar value={Math.round((project.actualHours / project.budgetHours) * 100)} size="sm" />
              </div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
};

// Task Queue View
const TaskQueueView = ({ tasks, setTasks, currentUser, projects }) => {
  const [viewMode, setViewMode] = useState(currentUser.permissions?.isAdmin ? 'team' : 'my');
  const [filterDesigner, setFilterDesigner] = useState('all');
  const [filterStatus, setFilterStatus] = useState('all');
  const [showAddTask, setShowAddTask] = useState(false);
  const [selectedTask, setSelectedTask] = useState(null);
  const [searchQuery, setSearchQuery] = useState('');
  
  const filteredTasks = tasks.filter(t => {
    if (viewMode === 'my' && t.designer !== currentUser.name) return false;
    if (filterDesigner !== 'all' && t.designer !== filterDesigner) return false;
    if (filterStatus !== 'all' && t.status !== filterStatus) return false;
    if (searchQuery) {
      const query = searchQuery.toLowerCase();
      return t.title.toLowerCase().includes(query) || 
             t.job.toLowerCase().includes(query) ||
             t.taskNum.includes(query);
    }
    return true;
  }).sort((a, b) => {
    // Priority sort: negative first (revisions), then positive ascending
    if (a.priority < 0 && b.priority >= 0) return -1;
    if (a.priority >= 0 && b.priority < 0) return 1;
    if (a.priority < 0 && b.priority < 0) return a.priority - b.priority;
    return a.priority - b.priority;
  });

  const handleProgressUpdate = (taskId, newProgress) => {
    setTasks(prev => prev.map(t => {
      if (t.id === taskId) {
        const newStatus = newProgress === 100 ? 'Review' : t.status === 'New' ? 'In Production' : t.status;
        return { ...t, progress: newProgress, status: newStatus, lastUpdated: new Date().toISOString().split('T')[0] };
      }
      return t;
    }));
  };

  // Generate next task number for a job.phase
  const getNextTaskNum = (job, phase) => {
    const existingTasks = tasks.filter(t => t.job === job && t.phase === phase);
    const maxNum = existingTasks.reduce((max, t) => {
      const num = parseInt(t.taskNum);
      return num > max ? num : max;
    }, 0);
    return String(maxNum + 1).padStart(4, '0');
  };

  // Get most recent delta for a job.phase
  const getMostRecentDelta = (job, phase) => {
    const phaseTasks = tasks.filter(t => t.job === job && t.phase === phase);
    if (phaseTasks.length === 0) return '0';
    const sorted = [...phaseTasks].sort((a, b) => b.id - a.id);
    return sorted[0].delta || '0';
  };

  return (
    <div className="p-6">
      {/* Toolbar */}
      <div className="flex items-center justify-between mb-6">
        <div className="flex items-center gap-3">
          <div className="flex bg-slate-100 rounded-lg p-1">
            {!currentUser.permissions?.isAdmin && (
              <button
                onClick={() => setViewMode('my')}
                className={`px-4 py-2 rounded-md text-sm font-medium transition-all ${
                  viewMode === 'my' 
                    ? 'bg-white text-slate-900 shadow-sm' 
                    : 'text-slate-600 hover:text-slate-900'
                }`}
              >
                My Queue
              </button>
            )}
            <button
              onClick={() => setViewMode('team')}
              className={`px-4 py-2 rounded-md text-sm font-medium transition-all ${
                viewMode === 'team' 
                  ? 'bg-white text-slate-900 shadow-sm' 
                  : 'text-slate-600 hover:text-slate-900'
              }`}
            >
              {currentUser.permissions?.isAdmin ? 'All Tasks' : 'Team Queue'}
            </button>
          </div>
          
          <div className="relative">
            <Search size={16} className="absolute left-3 top-1/2 -translate-y-1/2 text-slate-400" />
            <input 
              type="text" 
              placeholder="Search tasks..." 
              value={searchQuery}
              onChange={(e) => setSearchQuery(e.target.value)}
              className="pl-9 pr-4 py-2 border border-slate-200 rounded-lg w-64 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
            />
          </div>
        </div>
        
        <div className="flex items-center gap-3">
          <select 
            value={filterDesigner}
            onChange={(e) => setFilterDesigner(e.target.value)}
            className="border border-slate-200 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
          >
            <option value="all">All Designers</option>
            {mockDesigners.map(d => (
              <option key={d.id} value={d.name}>{d.name}</option>
            ))}
          </select>
          <select 
            value={filterStatus}
            onChange={(e) => setFilterStatus(e.target.value)}
            className="border border-slate-200 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
          >
            <option value="all">All Status</option>
            <option value="New">New</option>
            <option value="In Production">In Production</option>
            <option value="Review">Review</option>
          </select>
          {currentUser.permissions?.canCreateTasks && (
            <button 
              onClick={() => setShowAddTask(true)}
              className="flex items-center gap-2 bg-blue-600 text-white px-4 py-2 rounded-lg text-sm font-medium hover:bg-blue-700 transition-colors shadow-sm"
            >
              <Plus size={18} /> Add Task
            </button>
          )}
        </div>
      </div>

      {/* Priority Legend */}
      <div className="bg-white rounded-xl border border-slate-200 p-4 mb-4">
        <div className="flex items-center gap-6 text-sm">
          <span className="text-slate-500 font-medium">Priority Guide:</span>
          <div className="flex items-center gap-2">
            <span className="w-7 h-7 bg-rose-100 text-rose-700 rounded-full flex items-center justify-center text-xs font-bold">-1</span>
            <span className="text-slate-600">Revision (2 day turnaround)</span>
          </div>
          <div className="flex items-center gap-2">
            <span className="w-7 h-7 bg-blue-100 text-blue-700 rounded-full flex items-center justify-center text-xs font-bold">1</span>
            <span className="text-slate-600">Highest Priority</span>
          </div>
          <div className="flex items-center gap-2">
            <span className="w-7 h-7 bg-slate-100 text-slate-600 rounded-full flex items-center justify-center text-xs font-bold">20</span>
            <span className="text-slate-600">Lowest Priority</span>
          </div>
        </div>
      </div>

      {/* Task Table */}
      <div className="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
        <table className="w-full">
          <thead className="bg-slate-50 border-b border-slate-200">
            <tr>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider w-16">Pri</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Job.Phase</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Task</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider w-20">Cat</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider w-28">Status</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider w-32">Progress</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Designer</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider w-28">Due</th>
              <th className="px-4 py-3 text-right text-xs font-semibold text-slate-500 uppercase tracking-wider w-16">Actions</th>
            </tr>
          </thead>
          <tbody className="divide-y divide-slate-100">
            {filteredTasks.map(task => {
              const daysUntil = getDaysUntilDue(task.dueDate);
              const isOverdue = daysUntil < 0;
              const isUrgent = daysUntil >= 0 && daysUntil <= 2;
              
              return (
                <tr key={task.id} className="hover:bg-slate-50 transition-colors">
                  <td className="px-4 py-3">
                    <span className={`w-8 h-8 rounded-full flex items-center justify-center text-xs font-bold ${
                      task.priority < 0 
                        ? 'bg-rose-100 text-rose-700 ring-2 ring-rose-200' 
                        : task.priority <= 5
                          ? 'bg-blue-100 text-blue-700'
                          : 'bg-slate-100 text-slate-600'
                    }`}>
                      {task.priority}
                    </span>
                  </td>
                  <td className="px-4 py-3">
                    <p className="font-semibold text-slate-900">{task.job}.{task.phase}</p>
                    <p className="text-slate-400 text-xs">#{task.taskNum}</p>
                  </td>
                  <td className="px-4 py-3">
                    <p className="font-medium text-slate-900">{task.title}</p>
                    {task.denialReason && (
                      <p className="text-rose-600 text-xs flex items-center gap-1 mt-1">
                        <AlertTriangle size={12} /> {task.denialReason.substring(0, 40)}...
                      </p>
                    )}
                    {task.pcoNumber && (
                      <p className="text-slate-400 text-xs mt-0.5">PCO: {task.pcoNumber}</p>
                    )}
                  </td>
                  <td className="px-4 py-3">
                    <span className="px-2 py-1 bg-slate-100 rounded text-xs font-mono font-medium text-slate-700">
                      {task.catCode}
                    </span>
                  </td>
                  <td className="px-4 py-3">
                    <span className={`px-2.5 py-1 rounded-full text-xs font-medium border ${STATUS_COLORS[task.status]}`}>
                      {task.status}
                    </span>
                  </td>
                  <td className="px-4 py-3">
                    {task.status === 'In Production' && (currentUser.permissions?.isAdmin || task.designer === currentUser.name) ? (
                      <select
                        value={task.progress}
                        onChange={(e) => handleProgressUpdate(task.id, parseInt(e.target.value))}
                        className="w-full border border-slate-200 rounded px-2 py-1 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
                      >
                        {[0, 20, 40, 60, 80, 100].map(v => (
                          <option key={v} value={v}>{v}%</option>
                        ))}
                      </select>
                    ) : (
                      <ProgressBar value={task.progress} size="sm" />
                    )}
                  </td>
                  <td className="px-4 py-3">
                    <div className="flex items-center gap-2">
                      <div className="w-7 h-7 bg-slate-200 rounded-full flex items-center justify-center text-xs font-medium">
                        {task.designer.split(' ').map(n => n[0]).join('')}
                      </div>
                      <span className="text-sm text-slate-700">{task.designer}</span>
                    </div>
                  </td>
                  <td className="px-4 py-3">
                    <p className={`text-sm font-medium ${isOverdue ? 'text-rose-600' : isUrgent ? 'text-amber-600' : 'text-slate-700'}`}>
                      {formatDate(task.dueDate)}
                    </p>
                    {isOverdue && (
                      <p className="text-rose-500 text-xs">{Math.abs(daysUntil)} days overdue</p>
                    )}
                  </td>
                  <td className="px-4 py-3 text-right">
                    <button 
                      onClick={() => setSelectedTask(task)}
                      className="p-1.5 hover:bg-slate-100 rounded-lg transition-colors"
                    >
                      <MoreVertical size={16} className="text-slate-400" />
                    </button>
                  </td>
                </tr>
              );
            })}
          </tbody>
        </table>
        
        {filteredTasks.length === 0 && (
          <div className="p-12 text-center">
            <List size={48} className="mx-auto text-slate-300 mb-4" />
            <p className="text-slate-500 font-medium">No tasks found</p>
            <p className="text-slate-400 text-sm mt-1">Try adjusting your filters</p>
          </div>
        )}
      </div>

      {/* Add Task Modal */}
      <AddTaskModal 
        isOpen={showAddTask} 
        onClose={() => setShowAddTask(false)} 
        projects={projects || mockProjects}
        tasks={tasks}
        getNextTaskNum={getNextTaskNum}
        getMostRecentDelta={getMostRecentDelta}
        currentUser={currentUser}
        onAdd={(task) => {
          setTasks(prev => [...prev, { ...task, id: Math.max(...prev.map(t => t.id)) + 1 }]);
          setShowAddTask(false);
        }}
      />

      {/* Task Detail Modal */}
      <TaskDetailModal 
        task={selectedTask} 
        onClose={() => setSelectedTask(null)}
        onUpdate={(updated) => {
          setTasks(prev => prev.map(t => t.id === updated.id ? updated : t));
          setSelectedTask(null);
        }}
      />
    </div>
  );
};

// Add Task Modal
// Add Task Modal - Fully Functional
const AddTaskModal = ({ isOpen, onClose, onAdd, projects, tasks, getNextTaskNum, getMostRecentDelta, currentUser }) => {
  const [selectedProject, setSelectedProject] = useState(null);
  const [attachments, setAttachments] = useState([]);
  const [formData, setFormData] = useState({
    job: '',
    phase: '',
    catCode: '',
    title: '',
    description: '',
    dueDate: '',
    delta: '0',
    pcoNumber: '',
    designer: '',
    priority: 10,
  });
  const [errors, setErrors] = useState({});

  // Reset form when modal opens
  useEffect(() => {
    if (isOpen && projects.length > 0) {
      const defaultProject = projects[0];
      setSelectedProject(defaultProject);
      setFormData({
        job: defaultProject.job,
        phase: defaultProject.phase,
        catCode: '',
        title: '',
        description: '',
        dueDate: '',
        delta: getMostRecentDelta ? getMostRecentDelta(defaultProject.job, defaultProject.phase) : '0',
        pcoNumber: '',
        designer: defaultProject.designer || '',
        priority: 10,
      });
      setAttachments([]);
      setErrors({});
    }
  }, [isOpen, projects]);

  // Update form when project changes
  const handleProjectChange = (jobPhase) => {
    const [job, phase] = jobPhase.split('.');
    const project = projects.find(p => p.job === job && p.phase === phase);
    if (project) {
      setSelectedProject(project);
      setFormData(prev => ({
        ...prev,
        job: project.job,
        phase: project.phase,
        catCode: '', // Reset category code
        delta: getMostRecentDelta ? getMostRecentDelta(project.job, project.phase) : '0',
        designer: project.designer || '',
      }));
    }
  };

  // Get available category codes for selected project (only open codes)
  const getAvailableCatCodes = () => {
    if (!selectedProject) return [];
    // Filter to only open category codes for this project
    const openCodes = selectedProject.openCatCodes || [];
    return openCodes.map(code => ({
      code,
      ...CATEGORY_CODES[code]
    })).filter(c => c.name); // Only include valid codes
  };

  // Handle file drop/selection
  const handleFileChange = (e) => {
    const files = Array.from(e.target.files);
    setAttachments(prev => [...prev, ...files.map(f => ({
      name: f.name,
      size: f.size,
      type: f.type,
      file: f
    }))]);
  };

  const removeAttachment = (index) => {
    setAttachments(prev => prev.filter((_, i) => i !== index));
  };

  // Validate form
  const validateForm = () => {
    const newErrors = {};
    if (!formData.catCode) newErrors.catCode = 'Category code is required';
    if (!formData.title.trim()) newErrors.title = 'Task title is required';
    if (!formData.description.trim()) newErrors.description = 'Description is required';
    if (!formData.dueDate) newErrors.dueDate = 'Due date is required';
    if (!formData.designer) newErrors.designer = 'Designer is required';
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    if (!validateForm()) return;

    const taskNum = getNextTaskNum ? getNextTaskNum(formData.job, formData.phase) : String(Math.floor(Math.random() * 9000) + 1000);
    const project = projects.find(p => p.job === formData.job && p.phase === formData.phase);
    
    const newTask = {
      ...formData,
      taskNum,
      status: 'New',
      progress: 0,
      pm: project?.pm || 'Unassigned',
      denialCount: 0,
      originalDueDate: formData.dueDate,
      createdAt: new Date().toISOString().split('T')[0],
      lastUpdated: new Date().toISOString().split('T')[0],
      createdBy: currentUser?.name || 'Admin',
      attachments: attachments.map(a => a.name),
    };
    
    onAdd(newTask);
    
    // Reset form
    setFormData({
      job: '',
      phase: '',
      catCode: '',
      title: '',
      description: '',
      dueDate: '',
      delta: '0',
      pcoNumber: '',
      designer: '',
      priority: 10,
    });
    setAttachments([]);
    setSelectedProject(null);
  };

  const availableCatCodes = getAvailableCatCodes();

  return (
    <Modal isOpen={isOpen} onClose={onClose} title="Add New Task" size="lg">
      <form onSubmit={handleSubmit} className="space-y-5">
        {/* Project Selection */}
        <div className="bg-slate-50 rounded-lg p-4 border border-slate-200">
          <label className="block text-sm font-semibold text-slate-700 mb-2">Select Project</label>
          <select
            value={selectedProject ? `${selectedProject.job}.${selectedProject.phase}` : ''}
            onChange={(e) => handleProjectChange(e.target.value)}
            className="w-full border border-slate-200 rounded-lg px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 bg-white"
          >
            <option value="">Select a project...</option>
            {projects.map(p => (
              <option key={`${p.job}.${p.phase}`} value={`${p.job}.${p.phase}`}>
                {p.job}.{p.phase} - {p.name}
              </option>
            ))}
          </select>
          
          {selectedProject && (
            <div className="mt-3 grid grid-cols-3 gap-3 text-xs">
              <div className="bg-white rounded px-3 py-2 border border-slate-200">
                <span className="text-slate-500">PM:</span>
                <span className="ml-1 font-medium text-slate-700">{selectedProject.pm}</span>
              </div>
              <div className="bg-white rounded px-3 py-2 border border-slate-200">
                <span className="text-slate-500">Status:</span>
                <span className="ml-1 font-medium text-slate-700">{selectedProject.status}</span>
              </div>
              <div className="bg-white rounded px-3 py-2 border border-slate-200">
                <span className="text-slate-500">Panel Type:</span>
                <span className="ml-1 font-medium text-slate-700">{selectedProject.panelType}</span>
              </div>
            </div>
          )}
        </div>

        {/* Auto-populated fields display */}
        {selectedProject && (
          <div className="grid grid-cols-3 gap-4">
            <div>
              <label className="block text-xs font-medium text-slate-500 mb-1">Job Number</label>
              <div className="px-3 py-2 bg-slate-100 rounded-lg text-sm font-medium text-slate-700">
                {formData.job}
              </div>
            </div>
            <div>
              <label className="block text-xs font-medium text-slate-500 mb-1">Phase</label>
              <div className="px-3 py-2 bg-slate-100 rounded-lg text-sm font-medium text-slate-700">
                {formData.phase}
              </div>
            </div>
            <div>
              <label className="block text-xs font-medium text-slate-500 mb-1">Task Number</label>
              <div className="px-3 py-2 bg-slate-100 rounded-lg text-sm font-medium text-slate-700">
                #{getNextTaskNum ? getNextTaskNum(formData.job, formData.phase) : '####'}
              </div>
            </div>
          </div>
        )}

        {/* Category Code Selection */}
        <div>
          <label className="block text-sm font-medium text-slate-700 mb-1.5">
            Category Code <span className="text-rose-500">*</span>
          </label>
          <select
            value={formData.catCode}
            onChange={(e) => setFormData({ ...formData, catCode: e.target.value })}
            className={`w-full border rounded-lg px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 ${
              errors.catCode ? 'border-rose-300 bg-rose-50' : 'border-slate-200'
            }`}
            disabled={!selectedProject}
          >
            <option value="">Select Category Code (Open codes only)</option>
            {availableCatCodes.map(cat => (
              <option key={cat.code} value={cat.code}>
                {cat.code} - {cat.name} {cat.hasBudget ? '(Budgeted)' : '(Non-budgeted)'}
              </option>
            ))}
          </select>
          {errors.catCode && <p className="text-rose-500 text-xs mt-1">{errors.catCode}</p>}
          {selectedProject && availableCatCodes.length === 0 && (
            <p className="text-amber-600 text-xs mt-1 flex items-center gap-1">
              <AlertTriangle size={12} /> No open category codes available for this project
            </p>
          )}
        </div>

        {/* Designer Assignment */}
        <div>
          <label className="block text-sm font-medium text-slate-700 mb-1.5">
            Assign Designer <span className="text-rose-500">*</span>
          </label>
          <select
            value={formData.designer}
            onChange={(e) => setFormData({ ...formData, designer: e.target.value })}
            className={`w-full border rounded-lg px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 ${
              errors.designer ? 'border-rose-300 bg-rose-50' : 'border-slate-200'
            }`}
          >
            <option value="">Select Designer...</option>
            {mockDesigners.map(d => (
              <option key={d.id} value={d.name}>{d.name} ({d.utilization}% utilized)</option>
            ))}
          </select>
          {errors.designer && <p className="text-rose-500 text-xs mt-1">{errors.designer}</p>}
        </div>

        {/* Task Title */}
        <div>
          <label className="block text-sm font-medium text-slate-700 mb-1.5">
            Task Title <span className="text-rose-500">*</span>
          </label>
          <input
            type="text"
            value={formData.title}
            onChange={(e) => setFormData({ ...formData, title: e.target.value })}
            className={`w-full border rounded-lg px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 ${
              errors.title ? 'border-rose-300 bg-rose-50' : 'border-slate-200'
            }`}
            placeholder="Enter task title (e.g., Panel Layout - Main Building)"
          />
          {errors.title && <p className="text-rose-500 text-xs mt-1">{errors.title}</p>}
        </div>

        {/* Description */}
        <div>
          <label className="block text-sm font-medium text-slate-700 mb-1.5">
            Description <span className="text-rose-500">*</span>
          </label>
          <textarea
            value={formData.description}
            onChange={(e) => setFormData({ ...formData, description: e.target.value })}
            className={`w-full border rounded-lg px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 h-24 resize-none ${
              errors.description ? 'border-rose-300 bg-rose-50' : 'border-slate-200'
            }`}
            placeholder="Describe the task requirements and deliverables..."
          />
          {errors.description && <p className="text-rose-500 text-xs mt-1">{errors.description}</p>}
        </div>

        {/* Due Date, Delta, Priority, PCO */}
        <div className="grid grid-cols-4 gap-4">
          <div>
            <label className="block text-sm font-medium text-slate-700 mb-1.5">
              Due Date <span className="text-rose-500">*</span>
            </label>
            <input
              type="date"
              value={formData.dueDate}
              onChange={(e) => setFormData({ ...formData, dueDate: e.target.value })}
              className={`w-full border rounded-lg px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 ${
                errors.dueDate ? 'border-rose-300 bg-rose-50' : 'border-slate-200'
              }`}
              min={new Date().toISOString().split('T')[0]}
            />
            {errors.dueDate && <p className="text-rose-500 text-xs mt-1">{errors.dueDate}</p>}
          </div>
          <div>
            <label className="block text-sm font-medium text-slate-700 mb-1.5">
              Delta <span className="text-rose-500">*</span>
              <Info size={12} className="inline ml-1 text-slate-400" />
            </label>
            <input
              type="text"
              value={formData.delta}
              onChange={(e) => setFormData({ ...formData, delta: e.target.value })}
              className="w-full border border-slate-200 rounded-lg px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
              placeholder="0"
            />
            <p className="text-slate-400 text-xs mt-1">External revision #</p>
          </div>
          <div>
            <label className="block text-sm font-medium text-slate-700 mb-1.5">Priority</label>
            <select
              value={formData.priority}
              onChange={(e) => setFormData({ ...formData, priority: parseInt(e.target.value) })}
              className="w-full border border-slate-200 rounded-lg px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
            >
              {Array.from({ length: 20 }, (_, i) => i + 1).map(p => (
                <option key={p} value={p}>{p} {p === 1 ? '(Highest)' : p === 20 ? '(Lowest)' : ''}</option>
              ))}
            </select>
          </div>
          <div>
            <label className="block text-sm font-medium text-slate-700 mb-1.5">PCO Number</label>
            <input
              type="text"
              value={formData.pcoNumber}
              onChange={(e) => setFormData({ ...formData, pcoNumber: e.target.value })}
              className="w-full border border-slate-200 rounded-lg px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
              placeholder="PCO-XXXX-XXX"
            />
          </div>
        </div>

        {/* File Attachments */}
        <div>
          <label className="block text-sm font-medium text-slate-700 mb-1.5">Attachments</label>
          <div className="border-2 border-dashed border-slate-200 rounded-lg p-4 hover:border-blue-400 transition-colors">
            <input
              type="file"
              multiple
              onChange={handleFileChange}
              className="hidden"
              id="file-upload"
            />
            <label htmlFor="file-upload" className="cursor-pointer block text-center">
              <Upload size={24} className="mx-auto text-slate-400 mb-2" />
              <p className="text-sm text-slate-500">Drop files here or click to upload</p>
              <p className="text-xs text-slate-400 mt-1">Supports: PDF, DWG, DXF, Images</p>
            </label>
          </div>
          
          {attachments.length > 0 && (
            <div className="mt-3 space-y-2">
              {attachments.map((file, index) => (
                <div key={index} className="flex items-center justify-between bg-slate-50 rounded-lg px-3 py-2 text-sm">
                  <div className="flex items-center gap-2">
                    <Paperclip size={14} className="text-slate-400" />
                    <span className="text-slate-700">{file.name}</span>
                    <span className="text-slate-400 text-xs">({(file.size / 1024).toFixed(1)} KB)</span>
                  </div>
                  <button
                    type="button"
                    onClick={() => removeAttachment(index)}
                    className="text-slate-400 hover:text-rose-500 transition-colors"
                  >
                    <X size={14} />
                  </button>
                </div>
              ))}
            </div>
          )}
        </div>

        {/* Form Actions */}
        <div className="flex items-center justify-between pt-4 border-t border-slate-200">
          <div className="text-xs text-slate-500">
            <span className="text-rose-500">*</span> Required fields
          </div>
          <div className="flex gap-3">
            <button
              type="button"
              onClick={onClose}
              className="px-4 py-2.5 border border-slate-200 rounded-lg text-sm font-medium text-slate-700 hover:bg-slate-50 transition-colors"
            >
              Cancel
            </button>
            <button
              type="submit"
              disabled={!selectedProject}
              className="px-4 py-2.5 bg-blue-600 text-white rounded-lg text-sm font-medium hover:bg-blue-700 transition-colors disabled:opacity-50 disabled:cursor-not-allowed flex items-center gap-2"
            >
              <Plus size={16} />
              Create Task
            </button>
          </div>
        </div>
      </form>
    </Modal>
  );
};

// Task Detail Modal
const TaskDetailModal = ({ task, onClose, onUpdate }) => {
  if (!task) return null;

  return (
    <Modal isOpen={!!task} onClose={onClose} title={`Task #${task.taskNum}`} size="lg">
      <div className="space-y-5">
        <div className="flex items-start justify-between">
          <div>
            <h4 className="text-lg font-bold text-slate-900">{task.title}</h4>
            <p className="text-slate-500 text-sm mt-1">{task.job}.{task.phase} • {task.catCode}</p>
          </div>
          <span className={`px-3 py-1 rounded-full text-sm font-medium ${STATUS_COLORS[task.status]}`}>
            {task.status}
          </span>
        </div>

        <div className="bg-slate-50 rounded-lg p-4">
          <p className="text-sm text-slate-700">{task.description}</p>
        </div>

        <div className="grid grid-cols-2 gap-4">
          <div className="bg-slate-50 rounded-lg p-4">
            <p className="text-xs text-slate-500 uppercase tracking-wide mb-1">Designer</p>
            <p className="font-medium text-slate-900">{task.designer}</p>
          </div>
          <div className="bg-slate-50 rounded-lg p-4">
            <p className="text-xs text-slate-500 uppercase tracking-wide mb-1">Project Manager</p>
            <p className="font-medium text-slate-900">{task.pm}</p>
          </div>
          <div className="bg-slate-50 rounded-lg p-4">
            <p className="text-xs text-slate-500 uppercase tracking-wide mb-1">Due Date</p>
            <p className="font-medium text-slate-900">{formatDate(task.dueDate)}</p>
          </div>
          <div className="bg-slate-50 rounded-lg p-4">
            <p className="text-xs text-slate-500 uppercase tracking-wide mb-1">Priority</p>
            <p className="font-medium text-slate-900">{task.priority}</p>
          </div>
        </div>

        <div>
          <p className="text-xs text-slate-500 uppercase tracking-wide mb-2">Progress</p>
          <ProgressBar value={task.progress} size="lg" />
        </div>

        {task.denialReason && (
          <div className="bg-rose-50 border border-rose-200 rounded-lg p-4">
            <div className="flex items-start gap-3">
              <AlertTriangle size={20} className="text-rose-600 shrink-0 mt-0.5" />
              <div>
                <p className="font-medium text-rose-800">Denial Reason</p>
                <p className="text-rose-700 text-sm mt-1">{task.denialReason}</p>
              </div>
            </div>
          </div>
        )}

        <div className="flex items-center justify-between pt-4 border-t border-slate-200">
          <div className="text-xs text-slate-400">
            Created: {formatDate(task.createdAt)} • Updated: {formatDate(task.lastUpdated)}
          </div>
          <div className="flex gap-2">
            <button className="px-3 py-1.5 border border-slate-200 rounded-lg text-sm font-medium text-slate-700 hover:bg-slate-50 transition-colors flex items-center gap-2">
              <FolderOpen size={14} /> Open Files
            </button>
            <button className="px-3 py-1.5 bg-blue-600 text-white rounded-lg text-sm font-medium hover:bg-blue-700 transition-colors flex items-center gap-2">
              <Edit3 size={14} /> Edit Task
            </button>
          </div>
        </div>
      </div>
    </Modal>
  );
};

// Review Queue View
const ReviewQueueView = ({ tasks, setTasks }) => {
  const reviewTasks = tasks.filter(t => t.status === 'Review');
  const [selectedTask, setSelectedTask] = useState(reviewTasks[0] || null);
  const [showDenialModal, setShowDenialModal] = useState(false);
  const [denialReason, setDenialReason] = useState('');

  const handleApproval = (type) => {
    if (!selectedTask) return;
    
    setTasks(prev => prev.map(t => {
      if (t.id === selectedTask.id) {
        return { ...t, status: 'Approved', lastUpdated: new Date().toISOString().split('T')[0] };
      }
      return t;
    }));
    
    const remaining = reviewTasks.filter(t => t.id !== selectedTask.id);
    setSelectedTask(remaining[0] || null);
  };

  const handleDenial = () => {
    if (!selectedTask || !denialReason.trim()) return;
    
    // Find the next available negative priority
    const designerTasks = tasks.filter(t => t.designer === selectedTask.designer && t.priority < 0);
    const nextPriority = designerTasks.length > 0 
      ? Math.min(...designerTasks.map(t => t.priority)) - 1 
      : -1;
    
    setTasks(prev => prev.map(t => {
      if (t.id === selectedTask.id) {
        return { 
          ...t, 
          status: 'In Production', 
          progress: 80, 
          priority: nextPriority,
          denialCount: t.denialCount + 1,
          denialReason,
          lastUpdated: new Date().toISOString().split('T')[0]
        };
      }
      return t;
    }));
    
    setShowDenialModal(false);
    setDenialReason('');
    const remaining = reviewTasks.filter(t => t.id !== selectedTask.id);
    setSelectedTask(remaining[0] || null);
  };

  return (
    <div className="p-6">
      <div className="grid grid-cols-3 gap-6">
        {/* Tasks List */}
        <div className="col-span-2 bg-white rounded-xl shadow-sm border border-slate-200">
          <div className="p-5 border-b border-slate-200">
            <div className="flex items-center justify-between">
              <div>
                <h3 className="font-bold text-slate-900">Tasks Awaiting Review</h3>
                <p className="text-slate-500 text-sm mt-0.5">{reviewTasks.length} tasks at 100%</p>
              </div>
              <button className="flex items-center gap-2 text-sm text-slate-600 hover:text-slate-900">
                <RefreshCw size={14} /> Refresh
              </button>
            </div>
          </div>
          
          <div className="divide-y divide-slate-100">
            {reviewTasks.length === 0 ? (
              <div className="p-12 text-center">
                <CheckCircle size={48} className="mx-auto text-emerald-500 mb-4" />
                <p className="font-medium text-slate-700">All caught up!</p>
                <p className="text-slate-500 text-sm mt-1">No tasks pending review</p>
              </div>
            ) : (
              reviewTasks.map(task => (
                <div 
                  key={task.id}
                  onClick={() => setSelectedTask(task)}
                  className={`p-4 cursor-pointer hover:bg-slate-50 transition-colors ${
                    selectedTask?.id === task.id ? 'bg-blue-50 border-l-4 border-blue-600' : ''
                  }`}
                >
                  <div className="flex items-start justify-between">
                    <div className="flex-1">
                      <p className="font-medium text-slate-900">{task.title}</p>
                      <p className="text-slate-500 text-sm mt-0.5">{task.job}.{task.phase} • #{task.taskNum}</p>
                      <div className="flex items-center gap-4 mt-2 text-xs text-slate-400">
                        <span className="flex items-center gap-1">
                          <Users size={12} /> {task.designer}
                        </span>
                        <span className="flex items-center gap-1">
                          <Calendar size={12} /> Due: {formatDate(task.dueDate)}
                        </span>
                        {task.denialCount > 0 && (
                          <span className="flex items-center gap-1 text-amber-600">
                            <AlertTriangle size={12} /> {task.denialCount} prior denial(s)
                          </span>
                        )}
                      </div>
                    </div>
                    <span className="px-2 py-1 bg-slate-100 rounded text-xs font-mono font-medium">
                      {task.catCode}
                    </span>
                  </div>
                </div>
              ))
            )}
          </div>
        </div>

        {/* Review Actions Panel */}
        <div className="bg-white rounded-xl shadow-sm border border-slate-200">
          <div className="p-5 border-b border-slate-200">
            <h3 className="font-bold text-slate-900">Review Actions</h3>
          </div>
          
          {selectedTask ? (
            <div className="p-5">
              <div className="mb-6">
                <h4 className="font-medium text-slate-900">{selectedTask.title}</h4>
                <p className="text-slate-500 text-sm mt-1">{selectedTask.job}.{selectedTask.phase}</p>
                <p className="text-slate-400 text-xs mt-2">{selectedTask.description}</p>
              </div>
              
              <div className="space-y-3">
                <button 
                  onClick={() => handleApproval('submission')}
                  className="w-full flex items-center justify-center gap-2 bg-emerald-600 text-white px-4 py-3 rounded-lg text-sm font-medium hover:bg-emerald-700 transition-colors"
                >
                  <Send size={16} /> Approve for Submission
                </button>
                <button 
                  onClick={() => handleApproval('comments')}
                  className="w-full flex items-center justify-center gap-2 bg-blue-600 text-white px-4 py-3 rounded-lg text-sm font-medium hover:bg-blue-700 transition-colors"
                >
                  <MessageSquare size={16} /> Approve for Comments
                </button>
                <button 
                  onClick={() => handleApproval('close')}
                  className="w-full flex items-center justify-center gap-2 bg-slate-600 text-white px-4 py-3 rounded-lg text-sm font-medium hover:bg-slate-700 transition-colors"
                >
                  <CheckCircle size={16} /> Approve and Close
                </button>
                <button 
                  onClick={() => setShowDenialModal(true)}
                  className="w-full flex items-center justify-center gap-2 bg-rose-600 text-white px-4 py-3 rounded-lg text-sm font-medium hover:bg-rose-700 transition-colors"
                >
                  <XCircle size={16} /> Deny
                </button>
              </div>

              <div className="mt-6 p-4 bg-slate-50 rounded-lg">
                <p className="text-slate-600 text-xs font-medium mb-2">Denial will:</p>
                <ul className="text-slate-500 text-xs space-y-1">
                  <li className="flex items-center gap-2">
                    <ChevronRight size={12} /> Return to In Production at 80%
                  </li>
                  <li className="flex items-center gap-2">
                    <ChevronRight size={12} /> Assign negative priority (-1, -2...)
                  </li>
                  <li className="flex items-center gap-2">
                    <ChevronRight size={12} /> Require revision within 2 days
                  </li>
                </ul>
              </div>
            </div>
          ) : (
            <div className="p-12 text-center">
              <Eye size={48} className="mx-auto text-slate-300 mb-4" />
              <p className="text-slate-500 text-sm">Select a task to review</p>
            </div>
          )}
        </div>
      </div>

      {/* Denial Modal */}
      <Modal isOpen={showDenialModal} onClose={() => setShowDenialModal(false)} title="Deny Task">
        <div className="space-y-5">
          <div>
            <label className="block text-sm font-medium text-slate-700 mb-1.5">Reason (Required)</label>
            <textarea 
              value={denialReason}
              onChange={(e) => setDenialReason(e.target.value)}
              className="w-full border border-slate-200 rounded-lg p-3 h-24 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 resize-none" 
              placeholder="What needs to be corrected..." 
            />
          </div>
          
          <div>
            <label className="block text-sm font-medium text-slate-700 mb-1.5">Attachment (Required)</label>
            <div className="border-2 border-dashed border-slate-200 rounded-lg p-6 text-center hover:border-blue-400 transition-colors cursor-pointer">
              <Upload size={24} className="mx-auto text-slate-400 mb-2" />
              <p className="text-sm text-slate-500">Drop files or click to upload</p>
              <p className="text-xs text-slate-400 mt-1">If Teams meeting occurred, attach recording</p>
            </div>
          </div>
          
          <div className="bg-amber-50 border border-amber-200 rounded-lg p-4">
            <div className="flex items-start gap-3">
              <AlertTriangle size={18} className="text-amber-600 shrink-0 mt-0.5" />
              <div>
                <p className="text-sm font-medium text-amber-800">Priority Assignment</p>
                <p className="text-amber-700 text-xs mt-1">
                  Task will be assigned priority <strong>-{(tasks.filter(t => t.designer === selectedTask?.designer && t.priority < 0).length || 0) + 1}</strong> (2 day turnaround)
                </p>
              </div>
            </div>
          </div>
          
          <div className="flex gap-3 pt-4 border-t border-slate-200">
            <button 
              onClick={() => setShowDenialModal(false)} 
              className="flex-1 px-4 py-2.5 border border-slate-200 rounded-lg text-sm font-medium hover:bg-slate-50 transition-colors"
            >
              Cancel
            </button>
            <button 
              onClick={handleDenial}
              disabled={!denialReason.trim()}
              className="flex-1 px-4 py-2.5 bg-rose-600 text-white rounded-lg text-sm font-medium hover:bg-rose-700 transition-colors disabled:opacity-50 disabled:cursor-not-allowed"
            >
              Confirm Denial
            </button>
          </div>
        </div>
      </Modal>
    </div>
  );
};

// Projects View
const ProjectsView = ({ projects }) => {
  const [searchQuery, setSearchQuery] = useState('');
  const [filterStatus, setFilterStatus] = useState('all');
  const [selectedProject, setSelectedProject] = useState(null);

  const filteredProjects = projects.filter(p => {
    if (filterStatus !== 'all' && p.status !== filterStatus) return false;
    if (searchQuery) {
      const query = searchQuery.toLowerCase();
      return p.name.toLowerCase().includes(query) || p.job.toLowerCase().includes(query);
    }
    return true;
  });

  return (
    <div className="p-6">
      {/* Toolbar */}
      <div className="flex items-center justify-between mb-6">
        <div className="flex items-center gap-3">
          <div className="relative">
            <Search size={16} className="absolute left-3 top-1/2 -translate-y-1/2 text-slate-400" />
            <input 
              type="text" 
              placeholder="Search projects..." 
              value={searchQuery}
              onChange={(e) => setSearchQuery(e.target.value)}
              className="pl-9 pr-4 py-2 border border-slate-200 rounded-lg w-64 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
          </div>
          <select 
            value={filterStatus}
            onChange={(e) => setFilterStatus(e.target.value)}
            className="border border-slate-200 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
          >
            <option value="all">All Status</option>
            <option value="In Production">In Production</option>
            <option value="QAQC">QAQC</option>
            <option value="AE Released">AE Released</option>
          </select>
        </div>
      </div>

      {/* Projects Grid */}
      <div className="grid grid-cols-2 gap-4">
        {filteredProjects.map(project => (
          <div 
            key={`${project.job}-${project.phase}`} 
            className="bg-white rounded-xl shadow-sm border border-slate-200 p-5 hover:shadow-md transition-shadow cursor-pointer"
            onClick={() => setSelectedProject(project)}
          >
            <div className="flex items-start justify-between mb-4">
              <div>
                <div className="flex items-center gap-3">
                  <h3 className="text-lg font-bold text-slate-900">{project.job}.{project.phase}</h3>
                  <span className={`px-2.5 py-1 rounded-full text-xs font-medium ${STATUS_COLORS[project.status]}`}>
                    {project.status}
                  </span>
                </div>
                <p className="text-slate-600 mt-1">{project.name}</p>
                <p className="text-slate-400 text-sm mt-0.5">Site: {project.site}</p>
              </div>
              <span className={`px-2.5 py-1 rounded-lg text-xs font-medium ${
                project.panelType === 'New Panel' 
                  ? 'bg-violet-100 text-violet-700' 
                  : 'bg-slate-100 text-slate-600'
              }`}>
                {project.panelType}
              </span>
            </div>
            
            {/* Category Codes */}
            <div className="mb-4">
              <p className="text-xs text-slate-500 uppercase tracking-wide mb-2">Category Codes</p>
              <div className="flex flex-wrap gap-1.5">
                {project.catCodes.map(code => (
                  <span 
                    key={code} 
                    className={`px-2 py-1 rounded text-xs font-mono font-medium ${
                      project.openCatCodes.includes(code)
                        ? 'bg-emerald-100 text-emerald-700 ring-1 ring-emerald-300'
                        : 'bg-slate-100 text-slate-500'
                    }`}
                  >
                    {code}
                  </span>
                ))}
              </div>
            </div>

            {/* Budget Progress */}
            <div className="mb-4">
              <div className="flex items-center justify-between text-sm mb-1">
                <span className="text-slate-600">Budget Utilization</span>
                <span className="font-medium text-slate-900">
                  {project.actualHours}h / {project.budgetHours}h
                </span>
              </div>
              <ProgressBar 
                value={Math.round((project.actualHours / project.budgetHours) * 100)} 
                size="sm" 
                showLabel={false}
              />
            </div>

            {/* Team */}
            <div className="flex items-center justify-between pt-4 border-t border-slate-100">
              <div className="flex items-center gap-2">
                <div className="w-7 h-7 bg-blue-100 rounded-full flex items-center justify-center text-xs font-medium text-blue-700">
                  {project.pm.split(' ').map(n => n[0]).join('')}
                </div>
                <span className="text-sm text-slate-600">{project.pm}</span>
              </div>
              <div className="flex items-center gap-2">
                <div className="w-7 h-7 bg-emerald-100 rounded-full flex items-center justify-center text-xs font-medium text-emerald-700">
                  {project.designer.split(' ').map(n => n[0]).join('')}
                </div>
                <span className="text-sm text-slate-600">{project.designer}</span>
              </div>
            </div>

            {/* QAQC Indicator */}
            {project.qaqcRequired && (
              <div className="mt-4 flex items-center gap-2 text-xs text-violet-700 bg-violet-50 rounded-lg px-3 py-2">
                <Shield size={14} />
                <span className="font-medium">QAQC Required (New Panel)</span>
              </div>
            )}
          </div>
        ))}
      </div>

      {/* Project Detail Modal */}
      <ProjectDetailModal 
        project={selectedProject} 
        onClose={() => setSelectedProject(null)} 
      />
    </div>
  );
};

// Project Detail Modal
const ProjectDetailModal = ({ project, onClose }) => {
  if (!project) return null;

  return (
    <Modal isOpen={!!project} onClose={onClose} title={`${project.job}.${project.phase}`} size="xl">
      <div className="space-y-6">
        {/* Header Info */}
        <div className="flex items-start justify-between">
          <div>
            <h4 className="text-xl font-bold text-slate-900">{project.name}</h4>
            <p className="text-slate-500 mt-1">Site: {project.site}</p>
          </div>
          <div className="flex items-center gap-2">
            <span className={`px-3 py-1.5 rounded-full text-sm font-medium ${STATUS_COLORS[project.status]}`}>
              {project.status}
            </span>
            <span className={`px-3 py-1.5 rounded-lg text-sm font-medium ${
              project.panelType === 'New Panel' 
                ? 'bg-violet-100 text-violet-700' 
                : 'bg-slate-100 text-slate-600'
            }`}>
              {project.panelType}
            </span>
          </div>
        </div>

        {/* Dates */}
        <div className="grid grid-cols-4 gap-4">
          <div className="bg-slate-50 rounded-lg p-4">
            <p className="text-xs text-slate-500 uppercase tracking-wide mb-1">Project Start</p>
            <p className="font-medium text-slate-900">{formatDate(project.projectStart)}</p>
          </div>
          <div className="bg-slate-50 rounded-lg p-4">
            <p className="text-xs text-slate-500 uppercase tracking-wide mb-1">Project End</p>
            <p className="font-medium text-slate-900">{formatDate(project.projectEnd)}</p>
          </div>
          <div className="bg-slate-50 rounded-lg p-4">
            <p className="text-xs text-slate-500 uppercase tracking-wide mb-1">Design Start</p>
            <p className="font-medium text-slate-900">{formatDate(project.designStart)}</p>
          </div>
          <div className="bg-blue-50 rounded-lg p-4">
            <p className="text-xs text-blue-600 uppercase tracking-wide mb-1">Design End</p>
            <p className="font-bold text-blue-900">{formatDate(project.designEnd)}</p>
          </div>
        </div>

        {/* Category Codes Section */}
        <div>
          <h5 className="font-medium text-slate-900 mb-3">Category Code Lifecycle</h5>
          <div className="flex items-center gap-2">
            {project.catCodes.map((code, index) => (
              <React.Fragment key={code}>
                <div className={`px-3 py-2 rounded-lg text-sm font-mono font-medium ${
                  project.openCatCodes.includes(code)
                    ? 'bg-emerald-100 text-emerald-700 ring-2 ring-emerald-300'
                    : 'bg-slate-100 text-slate-500'
                }`}>
                  {code}
                  {project.openCatCodes.includes(code) && (
                    <span className="ml-2 text-xs">(Open)</span>
                  )}
                </div>
                {index < project.catCodes.length - 1 && (
                  <ChevronRight size={16} className="text-slate-300" />
                )}
              </React.Fragment>
            ))}
          </div>
        </div>

        {/* Budget */}
        <div>
          <h5 className="font-medium text-slate-900 mb-3">Budget Performance</h5>
          <div className="bg-slate-50 rounded-lg p-4">
            <div className="flex items-center justify-between mb-2">
              <span className="text-slate-600">Hours Used</span>
              <span className="font-bold text-slate-900">{project.actualHours}h / {project.budgetHours}h</span>
            </div>
            <ProgressBar value={Math.round((project.actualHours / project.budgetHours) * 100)} size="lg" />
          </div>
        </div>

        {/* Team */}
        <div className="grid grid-cols-2 gap-4">
          <div className="bg-slate-50 rounded-lg p-4">
            <p className="text-xs text-slate-500 uppercase tracking-wide mb-2">Project Manager</p>
            <div className="flex items-center gap-3">
              <div className="w-10 h-10 bg-blue-100 rounded-full flex items-center justify-center text-sm font-bold text-blue-700">
                {project.pm.split(' ').map(n => n[0]).join('')}
              </div>
              <p className="font-medium text-slate-900">{project.pm}</p>
            </div>
          </div>
          <div className="bg-slate-50 rounded-lg p-4">
            <p className="text-xs text-slate-500 uppercase tracking-wide mb-2">Designer</p>
            <div className="flex items-center gap-3">
              <div className="w-10 h-10 bg-emerald-100 rounded-full flex items-center justify-center text-sm font-bold text-emerald-700">
                {project.designer.split(' ').map(n => n[0]).join('')}
              </div>
              <p className="font-medium text-slate-900">{project.designer}</p>
            </div>
          </div>
        </div>

        {/* File Links */}
        <div className="flex items-center gap-4 pt-4 border-t border-slate-200">
          <button className="flex items-center gap-2 px-4 py-2 border border-slate-200 rounded-lg text-sm font-medium text-slate-700 hover:bg-slate-50 transition-colors">
            <FolderOpen size={16} /> J-Drive (Base Files)
          </button>
          <button className="flex items-center gap-2 px-4 py-2 border border-slate-200 rounded-lg text-sm font-medium text-slate-700 hover:bg-slate-50 transition-colors">
            <FolderOpen size={16} /> I-Drive (Working Files)
          </button>
          <button className="flex items-center gap-2 px-4 py-2 bg-blue-600 text-white rounded-lg text-sm font-medium hover:bg-blue-700 transition-colors">
            <ExternalLink size={16} /> Open in FC-PC
          </button>
        </div>
      </div>
    </Modal>
  );
};

// Activity Log View
const ActivityLogView = () => {
  const [filterAction, setFilterAction] = useState('all');
  const [searchQuery, setSearchQuery] = useState('');

  const actionColors = {
    'TASK_CREATED': 'bg-blue-100 text-blue-700',
    'TASK_DENIED': 'bg-rose-100 text-rose-700',
    'TASK_100_PERCENT': 'bg-violet-100 text-violet-700',
    'CODE_CREATED': 'bg-emerald-100 text-emerald-700',
    'QAQC_BYPASSED': 'bg-amber-100 text-amber-700',
    'QAQC_COMPLETED': 'bg-indigo-100 text-indigo-700',
    'AE_RELEASED': 'bg-teal-100 text-teal-700',
    'SUBMITTED_APPROVAL': 'bg-cyan-100 text-cyan-700',
  };

  const actionIcons = {
    'TASK_CREATED': Plus,
    'TASK_DENIED': XCircle,
    'TASK_100_PERCENT': CheckSquare,
    'CODE_CREATED': GitBranch,
    'QAQC_BYPASSED': AlertTriangle,
    'QAQC_COMPLETED': Shield,
    'AE_RELEASED': Archive,
    'SUBMITTED_APPROVAL': Send,
  };

  const filteredLogs = mockActivityLog.filter(log => {
    if (filterAction !== 'all' && log.action !== filterAction) return false;
    if (searchQuery) {
      const query = searchQuery.toLowerCase();
      return log.jobPhase.toLowerCase().includes(query) || 
             log.notes.toLowerCase().includes(query) ||
             log.user.toLowerCase().includes(query);
    }
    return true;
  });

  return (
    <div className="p-6">
      {/* Toolbar */}
      <div className="flex items-center justify-between mb-6">
        <div className="flex items-center gap-3">
          <div className="relative">
            <Search size={16} className="absolute left-3 top-1/2 -translate-y-1/2 text-slate-400" />
            <input 
              type="text" 
              placeholder="Search activity..." 
              value={searchQuery}
              onChange={(e) => setSearchQuery(e.target.value)}
              className="pl-9 pr-4 py-2 border border-slate-200 rounded-lg w-64 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
          </div>
          <select 
            value={filterAction}
            onChange={(e) => setFilterAction(e.target.value)}
            className="border border-slate-200 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
          >
            <option value="all">All Actions</option>
            <option value="TASK_CREATED">Task Created</option>
            <option value="TASK_DENIED">Task Denied</option>
            <option value="TASK_100_PERCENT">Task 100%</option>
            <option value="CODE_CREATED">Code Created</option>
            <option value="QAQC_BYPASSED">QAQC Bypassed</option>
            <option value="AE_RELEASED">AE Released</option>
          </select>
        </div>
        <button className="flex items-center gap-2 px-4 py-2 border border-slate-200 rounded-lg text-sm font-medium text-slate-700 hover:bg-slate-50 transition-colors">
          <Download size={16} /> Export Log
        </button>
      </div>

      {/* Activity Table */}
      <div className="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
        <table className="w-full">
          <thead className="bg-slate-50 border-b border-slate-200">
            <tr>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Timestamp</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Job.Phase</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Action</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Cat Code</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">User</th>
              <th className="px-4 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Notes</th>
            </tr>
          </thead>
          <tbody className="divide-y divide-slate-100">
            {filteredLogs.map(log => {
              const IconComponent = actionIcons[log.action] || Activity;
              return (
                <tr key={log.id} className="hover:bg-slate-50 transition-colors">
                  <td className="px-4 py-3 text-sm text-slate-500">{log.timestamp}</td>
                  <td className="px-4 py-3">
                    <span className="font-medium text-slate-900">{log.jobPhase}</span>
                  </td>
                  <td className="px-4 py-3">
                    <span className={`inline-flex items-center gap-1.5 px-2.5 py-1 rounded-full text-xs font-medium ${actionColors[log.action] || 'bg-slate-100 text-slate-700'}`}>
                      <IconComponent size={12} />
                      {log.action.replace(/_/g, ' ')}
                    </span>
                  </td>
                  <td className="px-4 py-3">
                    {log.catCode && (
                      <span className="px-2 py-1 bg-slate-100 rounded text-xs font-mono font-medium">
                        {log.catCode}
                      </span>
                    )}
                  </td>
                  <td className="px-4 py-3 text-sm text-slate-700">{log.user}</td>
                  <td className="px-4 py-3 text-sm text-slate-500 max-w-xs truncate">{log.notes}</td>
                </tr>
              );
            })}
          </tbody>
        </table>
      </div>
    </div>
  );
};

// Designer KPI View
const DesignerKPIView = () => {
  const [selectedDesigner, setSelectedDesigner] = useState('John Smith');
  const data = designerKPIData[selectedDesigner];
  const companyAvg = {
    onTimeRate: 85,
    denialRate: 10,
    budgetAdherence: 92,
    avgDaysEarlyLate: -0.5,
  };

  return (
    <div className="p-6 space-y-6">
      {/* Designer Selector */}
      <div className="flex items-center justify-between">
        <div className="flex items-center gap-4">
          <select 
            value={selectedDesigner} 
            onChange={(e) => setSelectedDesigner(e.target.value)} 
            className="border border-slate-200 rounded-lg px-4 py-2.5 text-sm font-medium focus:outline-none focus:ring-2 focus:ring-blue-500"
          >
            {mockDesigners.map(d => (
              <option key={d.id} value={d.name}>{d.name}</option>
            ))}
          </select>
          <span className="text-slate-500 text-sm flex items-center gap-2">
            <Info size={14} /> Compared to company average
          </span>
        </div>
        <div className="flex items-center gap-2">
          <button className="px-3 py-2 border border-slate-200 rounded-lg text-sm font-medium text-slate-700 hover:bg-slate-50 transition-colors">
            This Week
          </button>
          <button className="px-3 py-2 border border-slate-200 rounded-lg text-sm font-medium text-slate-700 hover:bg-slate-50 transition-colors">
            This Month
          </button>
          <button className="px-3 py-2 bg-blue-100 text-blue-700 rounded-lg text-sm font-medium">
            This Quarter
          </button>
        </div>
      </div>

      {/* KPI Cards */}
      <div className="grid grid-cols-4 gap-4">
        <StatCard 
          title="On-Time Rate" 
          value={`${data.onTimeRate}%`} 
          subtitle={`vs ${companyAvg.onTimeRate}% avg`} 
          icon={Clock} 
          trend={data.onTimeRate - companyAvg.onTimeRate}
          color="blue"
        />
        <StatCard 
          title="Days Early/Late" 
          value={data.avgDaysEarlyLate.toFixed(1)} 
          subtitle="Negative = early" 
          icon={Calendar}
          color={data.avgDaysEarlyLate < 0 ? 'green' : 'amber'}
        />
        <StatCard 
          title="Budget Adherence" 
          value={`${data.budgetAdherence}%`} 
          subtitle={`vs ${companyAvg.budgetAdherence}% avg`} 
          icon={BarChart2} 
          trend={data.budgetAdherence - companyAvg.budgetAdherence}
          color="green"
        />
        <StatCard 
          title="Denial Rate" 
          value={`${data.denialRate}%`} 
          subtitle={`vs ${companyAvg.denialRate}% avg`} 
          icon={XCircle}
          trend={companyAvg.denialRate - data.denialRate}
          color={data.denialRate < companyAvg.denialRate ? 'green' : 'rose'}
        />
      </div>

      {/* Charts Row */}
      <div className="grid grid-cols-2 gap-6">
        {/* Weekly Throughput */}
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <h3 className="font-bold text-slate-900 mb-4">Weekly Throughput</h3>
          <ResponsiveContainer width="100%" height={200}>
            <BarChart data={data.weeklyThroughput}>
              <CartesianGrid strokeDasharray="3 3" stroke="#e2e8f0" />
              <XAxis dataKey="week" tick={{ fontSize: 12, fill: '#64748b' }} />
              <YAxis tick={{ fontSize: 12, fill: '#64748b' }} />
              <Tooltip 
                contentStyle={{ 
                  borderRadius: '8px', 
                  border: '1px solid #e2e8f0',
                  boxShadow: '0 4px 6px -1px rgba(0, 0, 0, 0.1)'
                }} 
              />
              <Bar dataKey="tasks" fill="#3b82f6" radius={[4, 4, 0, 0]} />
            </BarChart>
          </ResponsiveContainer>
        </div>

        {/* Queue Depth */}
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <h3 className="font-bold text-slate-900 mb-4">Current Queue Depth</h3>
          <div className="space-y-4">
            <div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-sm text-slate-600 flex items-center gap-2">
                  <span className="w-3 h-3 bg-rose-500 rounded-full"></span>
                  Revisions (-20 to -1)
                </span>
                <span className="font-bold text-slate-900">{data.queueDepth.revisions}</span>
              </div>
              <div className="w-full bg-slate-100 rounded-full h-3">
                <div 
                  className="h-3 bg-rose-500 rounded-full transition-all" 
                  style={{ width: `${Math.min(data.queueDepth.revisions * 20, 100)}%` }} 
                />
              </div>
            </div>
            <div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-sm text-slate-600 flex items-center gap-2">
                  <span className="w-3 h-3 bg-blue-500 rounded-full"></span>
                  High Priority (1-5)
                </span>
                <span className="font-bold text-slate-900">{data.queueDepth.highPriority}</span>
              </div>
              <div className="w-full bg-slate-100 rounded-full h-3">
                <div 
                  className="h-3 bg-blue-500 rounded-full transition-all" 
                  style={{ width: `${Math.min(data.queueDepth.highPriority * 20, 100)}%` }} 
                />
              </div>
            </div>
            <div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-sm text-slate-600 flex items-center gap-2">
                  <span className="w-3 h-3 bg-slate-400 rounded-full"></span>
                  Normal (6-20)
                </span>
                <span className="font-bold text-slate-900">{data.queueDepth.normal}</span>
              </div>
              <div className="w-full bg-slate-100 rounded-full h-3">
                <div 
                  className="h-3 bg-slate-400 rounded-full transition-all" 
                  style={{ width: `${Math.min(data.queueDepth.normal * 10, 100)}%` }} 
                />
              </div>
            </div>
          </div>
        </div>
      </div>

      {/* Additional Metrics */}
      <div className="grid grid-cols-3 gap-4">
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <div className="flex items-center justify-between mb-4">
            <h4 className="font-medium text-slate-900">Avg Denials per Task</h4>
            <span className="text-2xl font-bold text-slate-900">{data.avgDenialsPerTask}</span>
          </div>
          <p className="text-sm text-slate-500">Lower is better</p>
        </div>
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <div className="flex items-center justify-between mb-4">
            <h4 className="font-medium text-slate-900">Revision Turnaround</h4>
            <span className="text-2xl font-bold text-slate-900">{data.revisionTurnaround} days</span>
          </div>
          <p className="text-sm text-slate-500">Avg time to complete denied tasks</p>
        </div>
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <div className="flex items-center justify-between mb-4">
            <h4 className="font-medium text-slate-900">Total Tasks (4 Weeks)</h4>
            <span className="text-2xl font-bold text-slate-900">
              {data.weeklyThroughput.reduce((a, b) => a + b.tasks, 0)}
            </span>
          </div>
          <p className="text-sm text-slate-500">Completed tasks</p>
        </div>
      </div>
    </div>
  );
};

// PM KPI View
const PMKPIView = () => {
  const [selectedPM, setSelectedPM] = useState('Sarah Johnson');
  const data = pmKPIData[selectedPM];
  const companyAvg = {
    firstTimeApprovalRate: 82,
    bypassFrequency: 2,
    correctionCycleCount: 1.2,
  };

  const isUnderThreshold = data.firstTimeApprovalRate < 80;

  return (
    <div className="p-6 space-y-6">
      {/* PM Selector */}
      <div className="flex items-center justify-between">
        <div className="flex items-center gap-4">
          <select 
            value={selectedPM} 
            onChange={(e) => setSelectedPM(e.target.value)} 
            className="border border-slate-200 rounded-lg px-4 py-2.5 text-sm font-medium focus:outline-none focus:ring-2 focus:ring-blue-500"
          >
            {mockPMs.map(p => (
              <option key={p.id} value={p.name}>{p.name}</option>
            ))}
          </select>
          <span className="text-slate-500 text-sm flex items-center gap-2">
            <Info size={14} /> Compared to company average
          </span>
        </div>
      </div>

      {/* Warning Alert */}
      {isUnderThreshold && (
        <div className="bg-rose-50 border border-rose-200 rounded-xl p-4 flex items-start gap-3">
          <AlertTriangle className="text-rose-600 shrink-0 mt-0.5" size={20} />
          <div>
            <p className="font-medium text-rose-800">First-Time Approval Below Threshold</p>
            <p className="text-rose-600 text-sm mt-1">
              Current rate ({data.firstTimeApprovalRate}%) is below the 80% threshold. Performance review may be triggered.
            </p>
          </div>
        </div>
      )}

      {/* KPI Cards */}
      <div className="grid grid-cols-4 gap-4">
        <StatCard 
          title="First-Time Approval" 
          value={`${data.firstTimeApprovalRate}%`} 
          subtitle="Threshold: 80%" 
          icon={CheckCircle}
          trend={data.firstTimeApprovalRate - companyAvg.firstTimeApprovalRate}
          color={data.firstTimeApprovalRate >= 80 ? 'green' : 'rose'}
        />
        <StatCard 
          title="Bypass Frequency" 
          value={data.bypassFrequency} 
          subtitle="Rolling 90 days" 
          icon={AlertTriangle}
          color={data.bypassFrequency <= 3 ? 'amber' : 'rose'}
        />
        <StatCard 
          title="Bypass Cost Ratio" 
          value={`${data.bypassCostRatio}%`} 
          subtitle="Q hrs ÷ base hrs" 
          icon={BarChart2}
          color="amber"
        />
        <StatCard 
          title="DRFC Frequency" 
          value={data.drfcFrequency} 
          subtitle="Schedule extensions" 
          icon={Calendar}
          color="blue"
        />
      </div>

      {/* Charts Row */}
      <div className="grid grid-cols-2 gap-6">
        {/* Turnaround Times */}
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <h3 className="font-bold text-slate-900 mb-4">Turnaround Times</h3>
          <div className="space-y-5">
            <div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-slate-600">Submission Turnaround</span>
                <span className="text-lg font-bold text-slate-900">{data.submissionTurnaround} days</span>
              </div>
              <p className="text-xs text-slate-400">QAQC to submission</p>
              <div className="mt-2 w-full bg-slate-100 rounded-full h-2">
                <div 
                  className="h-2 bg-blue-500 rounded-full" 
                  style={{ width: `${Math.min(data.submissionTurnaround / 5 * 100, 100)}%` }} 
                />
              </div>
            </div>
            <div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-slate-600">Approval Turnaround</span>
                <span className="text-lg font-bold text-slate-900">{data.approvalTurnaround} days</span>
              </div>
              <p className="text-xs text-slate-400">Submission to marking approved</p>
              <div className="mt-2 w-full bg-slate-100 rounded-full h-2">
                <div 
                  className="h-2 bg-emerald-500 rounded-full" 
                  style={{ width: `${Math.min(data.approvalTurnaround / 7 * 100, 100)}%` }} 
                />
              </div>
            </div>
            <div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-slate-600">Correction Cycles</span>
                <span className="text-lg font-bold text-slate-900">{data.correctionCycleCount}</span>
              </div>
              <p className="text-xs text-slate-400">Avg rounds before approval</p>
              <div className="mt-2 w-full bg-slate-100 rounded-full h-2">
                <div 
                  className="h-2 bg-amber-500 rounded-full" 
                  style={{ width: `${Math.min(data.correctionCycleCount / 3 * 100, 100)}%` }} 
                />
              </div>
            </div>
          </div>
        </div>

        {/* Active Projects */}
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <h3 className="font-bold text-slate-900 mb-4">Active Projects</h3>
          <div className="text-center mb-6">
            <p className="text-5xl font-bold text-blue-600">{data.activeProjects}</p>
            <p className="text-slate-500 text-sm mt-1">Total Projects</p>
          </div>
          <div className="grid grid-cols-3 gap-3">
            <div className="text-center p-4 bg-amber-50 rounded-xl">
              <p className="text-2xl font-bold text-amber-700">{data.projectBreakdown.inProduction}</p>
              <p className="text-xs text-amber-600 mt-1">In Production</p>
            </div>
            <div className="text-center p-4 bg-violet-50 rounded-xl">
              <p className="text-2xl font-bold text-violet-700">{data.projectBreakdown.review}</p>
              <p className="text-xs text-violet-600 mt-1">In Review</p>
            </div>
            <div className="text-center p-4 bg-teal-50 rounded-xl">
              <p className="text-2xl font-bold text-teal-700">{data.projectBreakdown.ae}</p>
              <p className="text-xs text-teal-600 mt-1">AE Phase</p>
            </div>
          </div>
        </div>
      </div>

      {/* Additional Metric */}
      <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
        <div className="flex items-center justify-between">
          <div>
            <h4 className="font-medium text-slate-900">Task Reclassification Rate</h4>
            <p className="text-sm text-slate-500 mt-1">Manual task moves per project (E1 → EC, etc.)</p>
          </div>
          <span className="text-3xl font-bold text-slate-900">{data.taskReclassificationRate}</span>
        </div>
      </div>
    </div>
  );
};

// Operations View
const OperationsView = () => {
  const pieData = [
    { name: 'New', value: operationsData.queueHealth.new, color: '#3b82f6' },
    { name: 'In Production', value: operationsData.queueHealth.inProduction, color: '#f59e0b' },
    { name: 'Review', value: operationsData.queueHealth.review, color: '#8b5cf6' },
  ];

  const materialOverages = [
    { job: 'G22104.00', name: '1950 Avenue of the Stars', pm: 'Sarah Johnson', overage: 18.5, status: 'Under Review' },
    { job: 'G22105.01', name: 'Century Plaza Tower B', pm: 'Mike Williams', overage: 22.1, status: 'Escalated' },
  ];

  return (
    <div className="p-6 space-y-6">
      {/* Top Stats */}
      <div className="grid grid-cols-4 gap-4">
        <StatCard 
          title="On-Time Delivery" 
          value={`${operationsData.onTimeDelivery}%`} 
          subtitle="Department-wide" 
          icon={Clock} 
          trend={3}
          color="blue"
        />
        <StatCard 
          title="Budget Performance" 
          value={`${operationsData.budgetPerformance}%`} 
          subtitle="Actual vs budget" 
          icon={BarChart2}
          trend={2}
          color="green"
        />
        <StatCard 
          title="QAQC Compliance" 
          value={`${operationsData.qaqcCompliance}%`} 
          subtitle="Proper vs bypassed" 
          icon={Shield}
          color="violet"
        />
        <StatCard 
          title="Overdue Tasks" 
          value={operationsData.overdueCount} 
          subtitle="Needs attention" 
          icon={AlertTriangle}
          color="rose"
        />
      </div>

      {/* Middle Row */}
      <div className="grid grid-cols-3 gap-6">
        {/* Queue Health Pie Chart */}
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <h3 className="font-bold text-slate-900 mb-4">Queue Health</h3>
          <ResponsiveContainer width="100%" height={180}>
            <PieChart>
              <Pie 
                data={pieData} 
                cx="50%" 
                cy="50%" 
                innerRadius={45} 
                outerRadius={70} 
                dataKey="value"
                stroke="none"
              >
                {pieData.map((entry, index) => (
                  <Cell key={`cell-${index}`} fill={entry.color} />
                ))}
              </Pie>
              <Tooltip />
            </PieChart>
          </ResponsiveContainer>
          <div className="text-center -mt-2">
            <p className="text-3xl font-bold text-slate-900">{pieData.reduce((a, b) => a + b.value, 0)}</p>
            <p className="text-slate-500 text-sm">Total Tasks</p>
          </div>
          <div className="flex justify-center gap-4 mt-4">
            {pieData.map(item => (
              <div key={item.name} className="flex items-center gap-2 text-xs">
                <span className="w-3 h-3 rounded-full" style={{ backgroundColor: item.color }}></span>
                <span className="text-slate-600">{item.name}</span>
              </div>
            ))}
          </div>
        </div>

        {/* Cost Attribution */}
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <h3 className="font-bold text-slate-900 mb-4">Cost Attribution</h3>
          <div className="space-y-5">
            <div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-slate-600 text-sm">Q Code (Internal - Our Fault)</span>
                <span className="font-bold text-rose-600">{operationsData.bypassCostImpact} hrs</span>
              </div>
              <div className="w-full bg-slate-100 rounded-full h-2.5">
                <div className="h-2.5 bg-rose-500 rounded-full" style={{ width: '33%' }} />
              </div>
            </div>
            <div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-slate-600 text-sm">C Code (External - Their Fault)</span>
                <span className="font-bold text-amber-600">{operationsData.correctionLoad} hrs</span>
              </div>
              <div className="w-full bg-slate-100 rounded-full h-2.5">
                <div className="h-2.5 bg-amber-500 rounded-full" style={{ width: '25%' }} />
              </div>
            </div>
            <div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-slate-600 text-sm">E1+ (Revisions)</span>
                <span className="font-bold text-blue-600">{operationsData.revisionVolume} hrs</span>
              </div>
              <div className="w-full bg-slate-100 rounded-full h-2.5">
                <div className="h-2.5 bg-blue-500 rounded-full" style={{ width: '50%' }} />
              </div>
            </div>
          </div>
        </div>

        {/* Resource Utilization */}
        <div className="bg-white rounded-xl shadow-sm border border-slate-200 p-5">
          <h3 className="font-bold text-slate-900 mb-4">Resource Utilization</h3>
          <div className="space-y-4">
            {mockDesigners.map(designer => (
              <div key={designer.id} className="flex items-center gap-3">
                <div className="w-8 h-8 bg-blue-100 rounded-full flex items-center justify-center text-xs font-bold text-blue-700">
                  {designer.avatar}
                </div>
                <div className="flex-1">
                  <div className="flex items-center justify-between text-sm mb-1">
                    <span className="text-slate-700">{designer.name}</span>
                    <span className="font-medium text-slate-900">{designer.utilization}%</span>
                  </div>
                  <div className="w-full bg-slate-100 rounded-full h-2">
                    <div 
                      className={`h-2 rounded-full ${
                        designer.utilization >= 90 ? 'bg-rose-500' : 
                        designer.utilization >= 75 ? 'bg-emerald-500' : 'bg-amber-500'
                      }`}
                      style={{ width: `${designer.utilization}%` }} 
                    />
                  </div>
                </div>
              </div>
            ))}
          </div>
        </div>
      </div>

      {/* Material Overages Table */}
      <div className="bg-white rounded-xl shadow-sm border border-slate-200">
        <div className="p-5 border-b border-slate-200 flex items-center justify-between">
          <div>
            <h3 className="font-bold text-slate-900">Material Overages (&gt;15%)</h3>
            <p className="text-slate-500 text-sm mt-0.5">Projects exceeding material budget threshold</p>
          </div>
          <Badge variant="danger">{materialOverages.length} Projects</Badge>
        </div>
        <table className="w-full">
          <thead className="bg-slate-50 border-b border-slate-200">
            <tr>
              <th className="px-5 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Job.Phase</th>
              <th className="px-5 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Project</th>
              <th className="px-5 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">PM</th>
              <th className="px-5 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Overage</th>
              <th className="px-5 py-3 text-left text-xs font-semibold text-slate-500 uppercase tracking-wider">Status</th>
            </tr>
          </thead>
          <tbody className="divide-y divide-slate-100">
            {materialOverages.map((item, i) => (
              <tr key={i} className="hover:bg-slate-50 transition-colors">
                <td className="px-5 py-4 font-medium text-slate-900">{item.job}</td>
                <td className="px-5 py-4 text-slate-700">{item.name}</td>
                <td className="px-5 py-4 text-slate-700">{item.pm}</td>
                <td className="px-5 py-4">
                  <span className="font-bold text-rose-600">+{item.overage}%</span>
                </td>
                <td className="px-5 py-4">
                  <span className={`px-2.5 py-1 rounded-full text-xs font-medium ${
                    item.status === 'Escalated' 
                      ? 'bg-rose-100 text-rose-700' 
                      : 'bg-amber-100 text-amber-700'
                  }`}>
                    {item.status}
                  </span>
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
    </div>
  );
};

// ============================================
// MAIN APP COMPONENT
// ============================================

export default function FCProjectControl() {
  const [activeView, setActiveView] = useState('dashboard');
  const [tasks, setTasks] = useState(mockTasks);
  
  const currentUser = {
    name: 'Admin User',
    avatar: 'AU',
    role: 'Operations/Admin',
    email: 'admin@bec.com',
    permissions: {
      canCreateTasks: true,
      canAssignDesigners: true,
      canBypassQAQC: true,
      canCompleteQAQC: true,
      canApproveReview: true,
      canDenyReview: true,
      canViewAllKPIs: true,
      canViewAllTasks: true,
      canEditPriorities: true,
      canManageProjects: true,
      canApproveDueDateChanges: true,
      canCreateDRFC: true,
      isAdmin: true
    }
  };

  const getViewInfo = () => {
    const views = {
      'dashboard': { title: 'Dashboard', subtitle: `Welcome back, ${currentUser.name.split(' ')[0]}${currentUser.permissions?.isAdmin ? ' (Admin)' : ''}` },
      'tasks': { title: 'Task Queue', subtitle: 'Manage priorities and track progress' },
      'projects': { title: 'Projects', subtitle: 'All active projects and phases' },
      'review': { title: 'Review Queue', subtitle: 'Tasks awaiting approval (100% complete)' },
      'activity': { title: 'Activity Log', subtitle: 'Comprehensive audit trail' },
      'designer-kpi': { title: 'Designer KPIs', subtitle: 'Performance metrics and benchmarks' },
      'pm-kpi': { title: 'PM KPIs', subtitle: 'Project Manager performance metrics' },
      'operations': { title: 'Operations Dashboard', subtitle: 'Department-wide metrics and alerts' },
    };
    return views[activeView] || { title: 'FC Project Control', subtitle: '' };
  };

  const renderView = () => {
    switch (activeView) {
      case 'dashboard':
        return <DashboardView tasks={tasks} projects={mockProjects} />;
      case 'tasks':
        return <TaskQueueView tasks={tasks} setTasks={setTasks} currentUser={currentUser} projects={mockProjects} />;
      case 'projects':
        return <ProjectsView projects={mockProjects} />;
      case 'review':
        return <ReviewQueueView tasks={tasks} setTasks={setTasks} />;
      case 'activity':
        return <ActivityLogView />;
      case 'designer-kpi':
        return <DesignerKPIView />;
      case 'pm-kpi':
        return <PMKPIView />;
      case 'operations':
        return <OperationsView />;
      default:
        return <DashboardView tasks={tasks} projects={mockProjects} />;
    }
  };

  const viewInfo = getViewInfo();

  return (
    <div className="flex h-screen bg-slate-100">
      <Sidebar 
        activeView={activeView} 
        setActiveView={setActiveView} 
        currentUser={currentUser}
      />
      <div className="flex-1 flex flex-col overflow-hidden">
        <Header title={viewInfo.title} subtitle={viewInfo.subtitle} />
        <div className="flex-1 overflow-y-auto">
          {renderView()}
        </div>
      </div>
    </div>
  );
}
