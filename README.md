# Assignment II: Oracle Pluggable Database Management Report

Pluggable Database (PDB): a portable, self-contained logical database that functions as a regular standalone database to applications but operates under a shared Container Database (CDB).

TASK 4,

**Date:** September 22, 2026  
**Course:** Advanced Database Systems / PL-SQL  
**Environment:** Oracle Database 21c Express Edition (XE) via Docker on Kali Linux

---

## 1. Overview of Tasks
This assignment demonstrates the administrative lifecycle of a Pluggable Database (PDB) operating within a Container Database (CDB) cluster environment. The exercise encompasses structural container creation, operational lifecycle modification, administrative role handling, structural deletion, and environment verification.

---

## 2. Oracle Environment Configuration
*   **Operating System Host:** Kali Linux (Rolling Release)
*   **Database Management Clients:** Oracle SQL Developer Extension for Visual Studio Code 
*   **Administrative Access Role:** `SYSDBA`

---

## 3. Core Task Execution Logs

### Task A: Pluggable Database Creation
The target pluggable container database was successfully provisioned using isolated directory definitions mapped directly within the runtime environment engine.

```sql
CREATE PLUGGABLE DATABASE elo_db_20252SEN241
ADMIN USER elois_plsqlauca_20252SEN241 IDENTIFIED BY "3LO15" 
FILE_NAME_CONVERT=('pdbseed','elo_db_20252SEN241');

ALTER PLUGGABLE DATABASE elo_db_20252SEN241 OPEN;
ALTER PLUGGABLE DATABASE elo_db_20252SEN241 SAVE STATE; (For saving the user even when the docker restarts).
```

### Task B: Environment Status Verification
To establish factual evidence of active operation, the following dictionary lookup was executed to confirm a `READ WRITE` operational profile:

```sql
SELECT name, open_mode FROM v$pdbs WHERE name = 'ELO_DB_20252SEN241';
```
*Verification State: Active / Online*

### Task C: Pluggable Database Deletion
The database infrastructure was intentionally torn down and wiped cleanly from the container runtime system using structural dropping protocols:

```sql
ALTER PLUGGABLE DATABASE elo_db_20252SEN241 CLOSE IMMEDIATE;
DROP PLUGGABLE DATABASE elo_db_20252SEN241 INCLUDING DATAFILES;
```

---

## 4. Challenges Faced & Solutions

### Challenge 1: OEM dashboard screenshot included, i didnt access it
---

## 5. Integrity Statement
I hereby declare on my honor that the database configurations, query outputs, and log documentation presented across this submission represent original technical administration tasks performed individually on my environment workstation.

---

## 6. Required Submission Details Block
*   **Repository Link:** https://github.com/elois-dotcom/oracle_pdb_II_2025SEN241_MUTABOBA 
*   **PDB Name Created:** `ELO_DB_20252SEN241`
*   **Issues Encountered:** Yes

