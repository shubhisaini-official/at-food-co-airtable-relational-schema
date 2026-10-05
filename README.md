# at-food-co-airtable-relational-schema
Normalized 3-table relational database architecture for AT Food Co. built in Airtable. Features primary and foreign key definitions, record linkage across customer profiles, subscription tiers, and lead tracking endpoints.
# 🐶 AT Food Co. — Airtable: Relational Database Architecture & Schema Engineering
> **No-Code Product Management: Data Normalization, Foreign Key Linking, Relational Schemas, and Lead Capture Systems**

[![Domain](https://img.shields.io/badge/Domain-Database%20Ops%20%7C%20No--Code-orange)](#)
[![Tool](https://img.shields.io/badge/Tool-Airtable-blue)](#)
[![Methodology](https://img.shields.io/badge/Methodology-Relational%20Data-green)](#)

---

## 📌 Executive Summary

* **Objective:** Establish a normalized 3-table relational database structure in **Airtable** for **AT Food Co.’s** D2C meal platform, eliminating duplicate data entry and enabling relational link records between user leads and subscription tiers.
* **Core Output:** Master database schema containing `Leads`, `Meal_Plans`, and `Plan_Subscriptions`.
* **Live Production Endpoint:** https://airtable.com/appzzrB7uQehnJIrd/shrDCyVfSz2B6ZkEx

---

## 🗄️ 1. Relational Database Schema Architecture

    Table 1: Leads
    Column Name     | Field Type         | Database Role
    ----------------|--------------------|--------------------------------------------------
    Email           | Email              | Primary Key (Unique Customer ID)
    Full Name       | Single Line Text   | Contact Profile Name
    Signup Date     | Created Time       | System Auto-Timestamp
    Status          | Single Select      | Options: New Lead, Trial Active, Converted

    Table 2: Meal_Plans
    Column Name     | Field Type         | Database Role
    ----------------|--------------------|--------------------------------------------------
    Plan ID         | Single Line Text   | Primary Key (e.g., PLAN-PUPPY-01)
    Plan Name       | Single Line Text   | Subscription Category Name
    Monthly Price   | Currency (INR)     | Billing Tier
    Caloric Range   | Single Line Text   | Daily Nutritional Target

    Table 3: Plan_Subscriptions (Relational Link Table)
    Column Name     | Field Type         | Database Role
    ----------------|--------------------|--------------------------------------------------
    Sub ID          | Autonumber         | Primary Key
    User Lead       | Link to Leads      | Foreign Key linking to Table 1 (Leads)
    Selected Plan   | Link to Meal_Plans | Foreign Key linking to Table 2 (Meal_Plans)
    Sub Status      | Single Select      | Options: Active Trial, Active Monthly, Cancelled

---

## ⚡ 2. Why Relational Data Modeling Matters

* **Prevents Duplicate Bloat:** Storing user information once in `Leads` and linking it to multiple purchases in `Plan_Subscriptions` ensures customer updates (like email changes) propagate system-wide automatically.
* **Scalable Product Architecture:** Allows Product Managers to track top-performing meal plans and conversion rates across subscriber cohorts without manual spreadsheet editing.
