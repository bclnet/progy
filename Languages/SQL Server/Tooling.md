## SQL TOOLING ##

**SQL Server Management Studio (SSMS)**

* Database Engine
* Analysis Services
* Integration Services
* Reporting Services
* Azure Storage


### Database Engine ###

**SERVER**

Settings are in runtime, and configure, needs recycle for some changes to take efffet

 - *Context Menu* - Connect, Disconnect, Register
   * New Query - Query tool (ctrl-n)
   * Activity Monitor
   * Start, Stop, Pause, Resume, Restart
 - *Properties*
   * General
   * Memory
   * Processors
   * Security
   * Connections
   * Database Settings
   * Advanced
   * Permissions
 - Databases
   - *Context Menu* - New Database
     * Attach, Restore Database, Restore Files and Groups
     * Deploy Data-tier Application, Import Data-tier Application
 - Security
   - Logins - New Login
   - Server Roles - New Server Role
   - Credentials - New Credential
   - Cryptographic Providers
   - Audits - New Audit
   - Server Audit Specifications - New Server Audit Specification
 - Server Objects
   - Backup Devices - New Backup Device, Back Up a Database
   - Endpoints
   - Linked Servers - New Linked Server
   - Triggers
 - Replication
 - Always On High Availability
 - Management
   - Policy Management - Disable, Enable
   - Data Collection 
   - Resource Governor - New Resource Pool
   - Extended Events
   - Maintenance Plans
   - SQL Server Logs
   - Database Mail
   - Distributed Transaction Coordinator
   - Legacy
 - Integration Services Catalogs
 - SQL Server Agent
   - Jobs
   - JOb Activity Monitor
   - Alerts
   - Operatiors
   - Proxies
   - Error Logs


**DATABASE**
 - *Context Menu* - New Database, New Query, Script Database as
   * Detach
   * Take Offline, Bring Online
   * Shrink
   * Backup, Restore
   * Mirror, Launch Database Mirroring Monitor
   * Ship Transansaction Logs
   * Generate Scripts, Generate In-Memory OLTP Migration Checklist
   * Data-tier Application Tasks...
   * Import Data, Export Data, Copy Database
   * Manage Database Encryption
 - *Properties*
   * General
   * Files
   * Filegroups
   * Options
   * Change Tracking
   * Permissions
   * Extended Properties
   * Mirroring
   * Transaction Log Shipping
 - Database Diagrams
 - Tables
 - Views
 - Synonyms
 - Programmability
   - Stored Procedures
   - Functions
     - Table-valued Functions
     - Scalar-valued Functions
     - Aggregate Functions
     - System Functions
   - Database Triggers
   - Assemblies
   - Types
   - Rules
   - Defaults
   - Plan Guides
   - Sequences
 - Service Broker
   - Message Types
   - Contracts
   - Queues
   - Services
   - Routes
   - Remote Service Binding
   - Broker Priorities
 - Storage
   - Full Text Catalogs
   - Partition Schemes
   - Partition Functions
   - Full Text Stoplists
   - Search Property Lists
 - Security
   - Users
   - Roles
   - Schemas
   - Asymmetric Keys
   - Certificates
   - Symmetric Keys
   - Database Audit Specifications
 
 **TABLE**
 - *Context Menu* - New Table, Design, Select Top 1000 Rows, Edit Top 200 Rows
   * Script Table as
   * View Dependencies
   * Memory Optimization Advisor
   * Full Text Index
 - *Properties*
   * General
   * Permissions
   * Change Tracking
   * Storage
   * Extended Properties
 - Columns
 - Keys
 - Constraints
 - Triggers
 - Indexes
 - Statistics


**TOOLS**

- Query
  * Direct SQL (F5), [red] to stop
  * Database as dropdown
  * highlight to selectively execute
  * Can comment/uncomment (cntl-k-c/cntl-k-u)
  * GO for multiple batches
  * Show Execution Plan (estimated/actual)
  * Show Client Statistics

- SQL Server Profiler

- Database Engine Tuning Advisor

- Code Snippets Manager
