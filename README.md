# TaskFlow Documentation

## 1. Project Overview

TaskFlow is a modern, Jira-integrated task and bug management application tailored for teams looking to streamline their workflow with a clean interface and powerful functionality. Inspired by tools like Linear, ClickUp, and Monday.com, TaskFlow offers a professional experience with deep customization and intuitive navigation.

### Purpose
TaskFlow was built to help teams manage tasks, bugs, and time tracking in one unified platform, fully integrated with Jira. It provides a single source of truth for project management while offering powerful reporting capabilities.

### Scope
The application covers:
- Task and bug tracking
- Project management
- Time tracking and reporting
- Jira integration
- Team collaboration

### Goals
- Simplify project management workflows
- Provide clear visibility into task and bug statuses
- Track time spent on projects for better resource allocation
- Generate insightful reports for project analysis
- Seamlessly integrate with existing Jira workspaces

## 2. Key Features

### Tasks Management
- Create, view, and manage tasks
- Filter tasks by status (Todo, In Progress, In Review, Done)
- Assign tasks to team members
- Set due dates and priorities

### Bugs Tracking
- Report and track bugs separately from regular tasks
- Assign severity and priority levels
- Monitor bug resolution progress
- Filter bugs by status

### Projects Management
- Organize tasks and bugs within project contexts
- View project-specific dashboards
- Track project progress with summary metrics
- Navigate through project-related items efficiently

### Reports
- **Weekly Time Tracker**: Log hours spent on different projects
- **Project Reports**: Visualize time distribution with pie charts
- **Time Trends**: Analyze time allocation trends across periods

### Jira Integration
- Connect to Jira workspaces
- Sync tasks and bugs between TaskFlow and Jira
- Use existing Jira workflows within TaskFlow

### Time Tracking
- Track time spent on tasks and projects
- Log daily work hours
- Generate time-based reports
- Analyze time allocation trends

## 3. Navigation Structure

### Left Sidebar Design
The application uses a responsive sidebar navigation system that provides access to all major sections:

- **Dashboard**: Overview of all tasks and bugs
- **Tasks**: Dedicated view for all tasks
- **Bugs**: Dedicated view for all bugs
- **Projects**: List of all projects
- **Reports**: Time tracking and reporting tools
- **Settings**: Application configuration

### Routing Logic
TaskFlow uses React Router for navigation with the following route structure:

- `/` - Dashboard
- `/tasks` - Tasks list
- `/tasks/:id` - Task detail view
- `/bugs` - Bugs list
- `/projects` - Projects list
- `/projects/:id` - Project detail view
- `/reports` - Reports and time tracking
- `/settings` - Application settings

Each route is wrapped in a `MainLayout` component that ensures the sidebar and header are consistently displayed across the application.

## 4. User Roles and Permissions

TaskFlow currently uses a simplified permission model where all authenticated users have the same access level to the application features. Future versions may implement more granular role-based access control.

Current user distinctions:
- **Authenticated Users**: Full access to all features
- **Unauthenticated Users**: Access to login page only

## 5. Dashboard Functionality

The dashboard provides a quick overview of all tasks and bugs relevant to the user.

### Components
- **My Tasks & Bugs**: Tasks and bugs assigned to the current user
- **Project-Wide Tasks & Bugs**: All tasks and bugs across projects
- **Task Filter**: Filter tasks by status

### Real-time Filtering
The dashboard implements client-side filtering logic that:
- Updates the displayed tasks/bugs immediately when filter options change
- Filters can be applied based on status (Todo, In Progress, In Review, Done)
- Separate filters for personal tasks and project-wide tasks

### Tab System
Both task cards implement a tab system that allows users to switch between:
- All items
- Tasks only
- Bugs only

## 6. Task & Bug Detail Pages

The detail pages provide comprehensive information and actions for individual tasks and bugs.

### Available Fields
- **Title**: Task/bug name
- **ID**: Unique identifier (can be linked to Jira)
- **Status**: Current workflow status
- **Assignee**: Team member responsible
- **Due Date**: Target completion date
- **Priority**: Importance level (high, medium, low)
- **Description**: Detailed information
- **Type**: Task or Bug classification

### Actions and Interactions
- **Update Status**: Change workflow status
- **Change Assignee**: Reassign to different team members
- **Set Due Date**: Use calendar picker to set deadlines
- **Adjust Priority**: Change importance level
- **Edit Description**: Update task details
- **Add Comments**: Contribute to discussion thread
- **Attach Files**: Upload relevant documents (UI available but functionality limited in current version)

### Activity Feed
- Chronological display of comments and changes
- Timestamp for each activity
- User identification for each action

## 7. Projects Section

The Projects section provides a view of all available projects and allows drilling down into project-specific tasks and bugs.

### Project List View
- Card-based display of all projects
- Each card shows:
  - Project name
  - Task count
  - Bug count
  - Total items count

### Project Detail View
- Project header with name and description
- Tab system to switch between tasks and bugs
- Filters for status and other attributes
- Task/bug list specific to the project
- Project summary showing counts of tasks/bugs by status

### Project Navigation
Users can click on any project card to navigate to its detail page, which provides project-specific task and bug management.

## 8. Reports Page

The Reports section offers tools for time tracking and generating visual reports of time allocation.

### Weekly Time Tracker Layout
- Grid-based interface for logging hours by project and day
- Date range navigation (previous/next week)
- Daily and weekly totals calculated automatically
- Save functionality that persists entries to localStorage

### Reports Summary
- Pie chart visualization of time distribution by project
- Time summary showing:
  - Total hours logged
  - Breakdown by project with hours and percentages
- Export options for reports (PDF and DOC formats)

### Time Trends
- Line or area charts showing time allocation trends
- Toggle between weekly and monthly views
- Project-specific trend lines
- Data table with detailed time entries by period
- Export functionality for CSV data

### Pie Chart Logic
- Calculates percentage of time spent on each project
- Color-coded segments for easy project identification
- Interactive tooltips showing hours and percentages
- Legend displaying all projects included in the chart

## 9. Settings Page

The Settings page provides configuration options for the application, with a focus on Jira integration.

### Jira Integration Setup Flow
1. Connect Jira account using OAuth
2. Select workspace and projects to sync
3. Configure field mappings between TaskFlow and Jira
4. Set sync frequency and options
5. Test connection
6. Save configuration

### Configuration Options
- User profile settings
- Notification preferences
- Theme customization
- Jira connection management

## 10. UI/UX Guidelines

### Styling Decisions
TaskFlow uses a clean, modern interface with consistent spacing, typography, and interaction patterns.

### Color Palette
- **Primary**: Blue/purple shades for branding and primary actions
- **Secondary**: Complementary colors for less prominent elements
- **Status Colors**:
  - Todo: Gray
  - In Progress: Blue
  - In Review: Purple
  - Done: Green
  - Bug: Red

### Animations
- Smooth transitions between pages
- Subtle hover effects on interactive elements
- Loading states with gentle animations
- Fade-in animations for newly loaded content

### Component System
TaskFlow uses the shadcn/ui component library built on Radix UI, providing accessible and consistent UI elements throughout the application.

## 11. Known Limitations

- **Mock Data**: The application currently uses static mock data instead of real API endpoints
- **Authentication**: Simple authentication system without full user management
- **File Attachments**: UI for file uploads exists but backend storage is not implemented
- **Jira Integration**: UI flow exists but actual API integration is limited
- **Offline Support**: No dedicated offline functionality
- **Mobile Optimization**: While responsive, some complex views (like time tracker) may have limited functionality on small screens

## 12. Future Improvements

- **Real-time Collaboration**: Implement WebSockets for live updates
- **Notification System**: Add in-app and email notifications
- **Advanced Filtering**: More powerful search and filtering options
- **Custom Fields**: Allow users to define custom fields for tasks and bugs
- **Team Management**: Add team creation and permission management
- **Time Tracking Automation**: Implement automatic time tracking based on activity
- **Gantt/Timeline Views**: Add visual project scheduling tools
- **API Documentation**: Create developer documentation for API endpoints
- **Public API**: Expose APIs for third-party integrations
- **Mobile App**: Develop dedicated mobile applications

## 13. Getting Started Guide

### Local Development Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/your-org/taskflow.git
   cd taskflow
   ```

2. Install dependencies:
  ```bash
  npm install
  ```

3. Configure environment variables: Create a .env.local file with the necessary configuration:
  ```bash
  VITE_API_URL=your_api_url
  VITE_JIRA_CLIENT_ID=your_jira_client_id
  ```

4. Start the development server:
  ```bash
  npm run dev
  ```

5. Access the application: Open your browser and navigate to 
  ```bash
  http://localhost:3000
  ```
