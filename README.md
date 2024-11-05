# Expense and Approval Management System

This project is an **Expense and Approval Management System** built to streamline expense submissions, approvals, and finance tracking within a company. It includes three key tables with distinct roles and access permissions, ensuring secure and efficient expense management.

## Table of Contents
- [Description](#description)
- [Features](#features)
- [Database Structure](#database-structure)
  - [Expense Submission Table](#expense-submission-table)
  - [Approval Table](#approval-table)
  - [Finance Table](#finance-table)
- [Access Control](#access-control)
- [Automation](#automation)
  - [Client Scripts](#client-scripts)
  - [Business Rules](#business-rules)
- [Installation](#installation)
- [License](#license)

## Description

The **Expense and Approval Management System** allows company employees to submit expenses (e.g., meals, travel, office supplies) for approval. Approvers and finance personnel can manage and approve these expenses through a series of automated workflows and role-based access control, ensuring that only authorized personnel can interact with specific data.

## Features ✨
- **Automated Approval Process**: Creates approval and finance records automatically based on expense submission status.
- **Role-Based Access Control (ACL)**: Ensures only authorized users can view or edit data in specific tables.
- **Dynamic Status Updates**: Status and employee name fields are updated automatically for a user-friendly experience.
- **Inter-User Communication**: Approvers and requestors can communicate within the system via work notes.

## Database Structure

### Expense Submission Table
- **Purpose**: Allows users to submit expenses incurred during company time, such as meals, travel, or office supplies.
- **Access**: Regular users can view this table only; they cannot access other tables.
- **Key Fields**: 
  - Expense ID
  - Status
  - Employee Name
  - Work Notes
  - Expense Details

### Approval Table
- **Purpose**: Allows approvers to review and approve expense submissions.
- **Access**: Only visible to approvers; approvers can view both this table and the Expense Submission Table.
- **Automatic Creation**: An entry in this table is created automatically upon expense submission.

### Finance Table
- **Purpose**: Enables finance personnel to finalize expenses post-approval.
- **Access**: Finance users can view both the Finance Table and Expense Submission Table but cannot access the Approval Table.
- **Automatic Creation**: An entry is created in this table only after an expense is approved.

## Access Control 🔒

Roles and groups were created to enforce access control through Access Control Lists (ACLs), ensuring that:

- **Regular Users**: Can only view the Expense Submission Table.
- **Approvers**: Can view and manage records in both the Approval Table and Expense Submission Table.
- **Finance Personnel**: Can view and manage records in the Finance Table and Expense Submission Table.

## Automation ⚙️

### Client Scripts
- **Status Update**: When a form is submitted, the status of the expense changes from empty to “Pending Approval.”
- **Employee Name Update**: The employee name field automatically populates with the name of the user who initially opens the form.

### Business Rules
- **Auto-Creation of Approval Records**: Creates a new approval record in the Approval Table when a user submits an expense.
- **Work Notes Communication**: Allows approvers and users to communicate via work notes in the system, facilitating clear interaction about the expense status and other details.

## Installation

To set up this application:

1. Clone or download the repository.
2. Import it into your ServiceNow instance via Studio.
3. Configure roles, groups, and ACLs as needed.
4. Set up client scripts and business rules based on the provided documentation to ensure functionality.

**Note**: This application was created using ServiceNow Studio. Ensure you have the necessary permissions and modules enabled in your ServiceNow instance.

## License

This project is licensed under the terms of the [license name] license.
