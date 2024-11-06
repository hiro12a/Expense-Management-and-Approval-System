# Expense and Approval Management System

The **Expense and Approval Management System** is designed to streamline the submission, approval, and tracking of expenses within a company. This application, built using ServiceNow Studio, includes three main tables and automated workflows to ensure a smooth and efficient process for managing company expenses.

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
  - [Flow Designer](#flow-designer)
- [Installation](#installation)

## Description

The **Expense and Approval Management System** allows employees to submit expenses (e.g., meals, travel, office supplies) for company reimbursement. Automated workflows and role-based access control ensure secure, authorized access to data. Key roles include regular users (employees), approvers, and finance personnel.

## Features ✨
- **Automated Workflow**: Automatic creation of records in the Approval and Finance tables based on expense status.
- **Role-Based Access Control (ACL)**: Ensures users only see and edit data relevant to their roles.
- **Status Updates**: Automated status changes for efficient tracking.
- **Inter-User Communication**: Enables interaction between users, approvers, and finance through work notes.

## Database Structure

### Expense Submission Table
- **Purpose**: Allows employees to submit expenses incurred during work, such as meals, travel, or office supplies.
- **Access**: Accessible only to regular users, who can view this table but not the others.
- **Automatic Updates**: The status field updates to "Pending Approval" upon submission, and the employee name populates when the form is loaded.

### Approval Table
- **Purpose**: Allows approvers to review and approve submitted expenses.
- **Access**: Accessible to approvers, who can view this table and the Expense Submission Table.
- **Automatic Creation**: This table entry is automatically generated after a user submits an expense.

### Finance Table
- **Purpose**: Allows finance personnel to manage and finalize approved expenses.
- **Access**: Accessible to finance users, who can view this table and the Expense Submission Table but not the Approval Table.
- **Automatic Creation**: This table entry is created only when an expense is approved by an approver.

## Access Control 🔒

Roles and groups are created for Access Control List (ACL) management, ensuring proper permissions:
- **Regular Users**: Can only view the Expense Submission Table.
- **Approvers**: Can view and manage records in both the Approval and Expense Submission Tables.
- **Finance Personnel**: Can view and manage records in the Finance and Expense Submission Tables.

## Automation ⚙️

### Client Scripts
- **Status Update**: Upon form submission, the status of the expense changes from empty to “Pending Approval.”
- **Employee Name Update**: Automatically fills the employee name with the user's name upon form load.

### Business Rules
- **Approval Record Creation**: Automatically creates an approval record and assigns it to a random approver when an expense is submitted.
- **Work Notes Communication**: Allows users, approvers, and finance personnel to communicate via work notes within the system.
- **Finance Record Creation**: Automatically generates a Finance record and assigns it to a finance approver after an expense is approved. If the expense is not approved, no Finance record is created.
- **Status Update for Reimbursement**: When a Finance record is created, the status in the Expense Submission Table updates to “Pending Reimbursement.”

### Flow Designer
- **Reimbursement Status Update**: The flow automatically updates the status in the Expense Submission Table based on the Finance record's reimbursement status. If the Finance approver sets the reimbursement status to “Processed,” the status in the Expense Submission Table changes to “Reimbursed.”

## Installation

To install and configure the application:
1. Clone or download the repository.
2. Import it into your ServiceNow instance using Studio.
3. Configure roles, groups, ACLs, client scripts, business rules, and flows as described to ensure proper functionality.
