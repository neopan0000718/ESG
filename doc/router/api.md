# Login

<details>
<summary><code>login</code> <code><b>/{UID}/{password}</b></code> <code>login by given UID and password</code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|UID|true|string|ID for the user|
|password|true|string|Password for the user|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Login successfully!"}|
|400|application/json|{"message": "Bad request - Invalid UID or password."}|
|500|application/json|{"message": "Server error."}|

</details>

<details>
<summary><code>revise_password</code> <code><b>/{UID}/{old password}/{new password}/{new password}</b></code> <code>revise user's password</code></summary>

<br />New pwd should be different from the old one.

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|UID|true|string|ID for the user|
|old password|true|string|Old password for the user|
|new password|true|string|New Password for the user|
|new password|true|string|New Password for the user (enter again)|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Revise password successfully!"}|
|400|application/json|{"message": "Bad request - Invalid password."}|
|500|application/json|{"message": "Server error."}|

</details>

# Admin
#### Create user
<details>
<summary><code>user_create</code> <code><b>/{EID}/{access}</b></code> <code>create an account by EID and assign an access for this account </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|EID|true|string|ID for the employee|
|access|true|string|Access for the user|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Create user successfully!", "UID": "assign_UID", "password": "initial_password"}|
|400|application/json|{"message": "Bad request - Invalid EID or access."}|
|500|application/json|{"message": "Server error."}|

</details>

#### Access assignment
<details>
<summary><code>access_assign</code> <code><b>/{UID}/{access}</b></code> <code>re-assign access for the user </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|UID|true|string|ID for the user|
|access|true|string|Access for the user|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Re-assign user's access successfully!"}|
|400|application/json|{"message": "Bad request - Invalid UID or access."}|
|500|application/json|{"message": "Server error."}|

</details>

#### create project
<details>
<summary><code>project_create</code> <code><b>/{project_name}/{UID}/{MID}/{EQID}</b></code> <code>enter project manager's UID, material ID and equipment ID to create a project </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|PName|true|string|Project name|
|UID|true|string|ID for the PM|
|MID|true|string|ID for the material|
|EQID|true|string|ID for the equipment|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Create project successfully!", "PID": "initial PID", "UID": "UID", "material": "list for material", "equipment": "list for equipment"}|
|400|application/json|{"message": "Bad request - Invalid UID or MID or EQID."}|
|500|application/json|{"message": "Server error."}|

</details>

#### Approve
<details>
<summary><code>approve_revise</code> <code><b>/{PID}/{UID}/{"old EQID": "EQID", "old EQ_usageTime": "EQ_usageTime"}/{"new EQID": "EQID", "new EQ_usageTime": "EQ_usageTime"}/{timestamp}</b></code> <code>approve the revise send from PM to revise the equipment usage time </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|PID|true|string|ID for the project|
|UID|true|string|ID for the PM|
|{"old EQID": "EQID", "old EQ_usageTime": "EQ_usageTime"}|true|json|Old content of the daily record|
|{"new EQID": "EQID", "new EQ_usageTime": "EQ_usageTime"}|true|json|New content of the daily record|
|timestamp|true|timestamp|System produce|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Approve the resive successfully!"}|
|500|application/json|{"message": "Server error."}|

</details>

<details>
<summary><code>reject_revise</code> <code><b>/{PID}/{UID}/{"old EQID": "EQID", "old EQ_usageTime": "EQ_usageTime"}/{"new EQID": "EQID", "new EQ_usageTime": "EQ_usageTime"}/{timestamp}</b></code> <code>reject the revise send from PM to revise the equipment usage time </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|PID|true|string|ID for the project|
|UID|true|string|ID for the PM|
|{"old EQID": "EQID", "old EQ_usageTime": "EQ_usageTime"}|true|json|Old content of the daily record|
|{"new EQID": "EQID", "new EQ_usageTime": "EQ_usageTime"}|true|json|New content of the daily record|
|timestamp|true|timestamp|System produce|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Approve the resive successfully!"}|
|500|application/json|{"message": "Server error."}|

</details>

#### Employee
<details>
<summary><code>Post</code> <code><b>/{name}/{gender}/{phone}/{mail}/{nation}/{PID}</b></code> <code>create an employee </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|name|true|string|Name for the employee|
|gender|true|int|Gender for the employee. 1 for male, 2 for female.|
|phone|true|string|Phone for the employee|
|mail|true|string|Mail for the employee|
|nation|true|string|Nationality for the employee|
|PID|false|string|ID for the project that the employee works on|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Create an employee successfully!", "EID": "initial EID"}|
|400|application/json|{"message": "Bad request - Invalid gender or PID."}|
|500|application/json|{"message": "Server error."}|

</details>

<details>
<summary><code>Revise</code> <code><b>/{EID}/{name}/{gender}/{phone}/{mail}/{nation}/{PID}</b></code> <code>revise an employee's data </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|EID|true|string|ID for the employee|
|name|true|string|Name for the employee|
|gender|true|int|Gender for the employee. 1 for male, 2 for female.|
|phone|true|string|Phone for the employee|
|mail|true|string|Mail for the employee|
|nation|true|string|Nationality for the employee|
|PID|false|string|ID for the project that the employee works on|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Revise an employee successfully!"}|
|400|application/json|{"message": "Bad request - Invalid EID or gender or PID."}|
|500|application/json|{"message": "Server error."}|

</details>

<details>
<summary><code>Delete</code> <code><b>/{EID}/{name}</b></code> <code>delete an employee by EID and name </code></summary>

<br />marked as delete

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|EID|true|string|ID for the employee|
|name|true|string|Name for the employee|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Delete an employee successfully!"}|
|400|application/json|{"message": "Bad request - Invalid EID or name."}|
|500|application/json|{"message": "Server error."}|

</details>

<details>
<summary><code>Retrieve</code> <code><b>/{EID}/{name}/{nation}/{PID}</b></code> <code>retrieve employees by EID or name or nation or PID </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|EID|false|string|ID for the employee|
|name|false|string|Name for the employee|
|nation|false|string|Nationality for the employee|
|PID|false|string|ID for the project that the employee works on|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Retrieve employees successfully!", "employees": "list for employees' data"}|
|400|application/json|{"message": "Bad request - Invalid EID or name or nation or PID."}|
|500|application/json|{"message": "Server error."}|

</details>

#### history logs
<details>
<summary><code>Log</code> <code><b>/x</b></code> <code>retrieve system logs </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|-----|----------|----------|------------|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Retrieve system logs successfully!", "logs": "list of logs"}|
|500|application/json|{"message": "Server error."}|

</details>

# Project Management

#### member
<details>
<summary><code>Post</code> <code><b>/{EID}/{position}</b></code> <code>add employees into the project and assign positions to them </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|EID|true|string|ID for the employee|
|position|true|string|positions for the employee|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Add employee successfully!"}|
|400|application/json|{"message": "Bad request - Invalid EID."}|
|500|application/json|{"message": "Server error."}|

</details>

<details>
<summary><code>Revise</code> <code><b>/{EID}/{position}</b></code> <code>revise the employees' positions </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|EID|true|string|ID for the employee|
|position|true|string|positions for the employee|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Resive employee's positions successfully!"}|
|400|application/json|{"message": "Bad request - Invalid EID."}|
|500|application/json|{"message": "Server error."}|

</details>

<details>
<summary><code>Remove</code> <code><b>/{EID}</b></code> <code>remove employees from project</code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|EID|true|string|ID for the employee|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Remove employee successfully!"}|
|400|application/json|{"message": "Bad request - Invalid EID."}|
|500|application/json|{"message": "Server error."}|

</details>

<details>
<summary><code>Retrieve</code> <code><b>/{EID}/{name}/{position}</b></code> <code>retrieve employees by EID or name or position </code></summary>

#### Header
| key | value | desciption |
|-----|-------|------------|
|-----|-------|------------|

#### Path Parameters
| key | required | datatype | desciption |
|-----|----------|----------|------------|
|EID|false|string|ID for the employee|
|name|false|string|name for the employee|
|position|false|string|position for the employee|

#### Responses
| http code | content-type | response |
|-----------|--------------|----------|
|200|application/json|{"message": "Retrieve employees successfully!", "employees": "list of employees"}|
|400|application/json|{"message": "Bad request - Invalid EID or name or position."}|
|500|application/json|{"message": "Server error."}|

</details>