# Debugging Log — Corporate Account Auditor


Record of every bug found in the original (broken) prototype, the symptom it caused, and the fix applied. Organized by file, in the order recommended by the README's troubleshooting steps.

---

## `audit_menu.sh`

| 1 | Found error `case "$selection"` was changed to`$choice`  `*)`, error was discovered once ran; menu appeared completely non-functional | Changed to `case "$choice"` |

| 2 | On line 39 Option `2` called `python3 scripts/account_audit.py` instead of `department_summary.py` Selecting "Run department summary" silently produced an account audit report instead | Changed to call `scripts/department_summary.py` |

| 3 | Added `mkdir -p reports archive` near the top of the script |



<img width="1051" height="517" alt="choice-selection-error-1" src="https://github.com/user-attachments/assets/a76ab24e-5e27-4300-a0bf-a72f64f760b8" />


<img width="740" height="892" alt="choice-selection-error2" src="https://github.com/user-attachments/assets/0f623e26-c74f-4f20-9fff-d819596409bf" />


<img width="1212" height="572" alt="audit-choice2" src="https://github.com/user-attachments/assets/5007e3ae-1ae1-4a9d-8f19-b8978cca1416" />


<img width="588" height="155" alt="audit-menu-choice" src="https://github.com/user-attachments/assets/c61ecfd8-6185-4cd2-96be-ce90c1df257b" />


<img width="1057" height="780" alt="audit-menu-change" src="https://github.com/user-attachments/assets/0ca2371a-0eb2-46e0-bb63-0fb552b54a8a" />


<img width="452" height="115" alt="mkdir-p-archive" src="https://github.com/user-attachments/assets/6003e434-0135-49a9-bb23-9af2dc822e0b" />








---

## `scripts/account_audit.py`

| 4 | `line.strip()` was changed to `line = line.strip()` |
| 5 | `department = employee[2]` and `days = employee[1]` fields are in the wrong order | Logic | Department and days-since-login values were swapped in every printed row | Corrected to `department = employee[1]`, `days = employee[2]` |
| 6 | `elif days >= 30` missing trailing colon | Syntax | `SyntaxError`, script would not run at all | Added `:` |



<img width="756" height="662" alt="account-audit-addtest" src="https://github.com/user-attachments/assets/fde7cf6f-f173-4b4f-b042-6dad0310c58c" />



<img width="640" height="892" alt="account-audit-change-order1" src="https://github.com/user-attachments/assets/39d1dd75-15dc-4e0e-a9cd-5409e54e6d18" />



<img width="712" height="903" alt="account-audit-change-orderpy2" src="https://github.com/user-attachments/assets/3533c3c7-29aa-42d7-8037-c1c8720cea6d" />



<img width="995" height="829" alt="account-audit-missing-colon png " src="https://github.com/user-attachments/assets/4de79a0e-c9ac-489f-9532-9ef4266a19a8" />



<img width="964" height="780" alt="account-audit-corrected-colon" src="https://github.com/user-attachments/assets/4d7aaf1f-3075-421b-8c70-0568d10196fe" />




---

## `scripts/department_summary.py`

| 7 | `department_counts[department] == 1` used comparison (`==`) instead of assignment (`=`) Changed to `department_counts[department] = 1` |
| 8 | `for department, count in department_counts.items()` missing trailing colon | Syntax | `SyntaxError`, script would not run at all | Added `:` |


<img width="875" height="791" alt="department-summary-removeextraequal" src="https://github.com/user-attachments/assets/61cb8a2a-a65f-422c-b6e9-9fe2f4af888e" />


<img width="1445" height="143" alt="department-summary-pyError2" src="https://github.com/user-attachments/assets/8490312c-3b69-4fec-a0b6-2d5676cd7ffc" />


<img width="969" height="810" alt="department-summary-colon-pyfix3-2" src="https://github.com/user-attachments/assets/4dd6a9e7-376d-4e96-b642-d8cfd95fd192" />


---

## `scripts/add_employee.py`

| 9 | `if username == "" and department == ""` used `and` instead of `or` so we changed `and` to `or` |
| 10 | `elif not days.isdigit()` missing trailing colon | Syntax | `SyntaxError`, script would not run at all | Added `:` |
| 11 | `file.write(new_employee)` attempted to write a tuple directly to a file | Runtime | `TypeError: write() argument must be str, not tuple` | Changed to `file.write(",".join(map(str, new_employee)) + "\n")` |



<img width="634" height="181" alt="add-employee-or" src="https://github.com/user-attachments/assets/489607ef-b387-4894-97f9-74760c570fcc" />



<img width="631" height="183" alt="add-employee-and" src="https://github.com/user-attachments/assets/f5c0253b-6103-4a06-82ec-7075ff00df56" />



<img width="983" height="806" alt="add-employee-missing-colon" src="https://github.com/user-attachments/assets/744f6c38-d3c6-4e2b-9e25-cff0648aee87" />



<img width="795" height="447" alt="add-employee-correction2-1" src="https://github.com/user-attachments/assets/24a1f1de-7bf9-42d9-93bc-5d0720c8018b" />


---

## Summary

- **Syntax errors (3):** missing colons in `account_audit.py`, `department_summary.py`, `add_employee.py` — each an immediate `SyntaxError` that blocked execution entirely.
- **Runtime error (1):** writing a `tuple` to a file in `add_employee.py` — a `TypeError` that only surfaced once valid input reached that code path.
- **Logic errors (7):** wrong variable name in a `case` statement, wrong script invoked from the menu, missing directory setup, a discarded `.strip()` result, swapped tuple fields, `==` vs `=`, and `and` vs `or` — none of these crashed the program, but each produced silently incorrect behavior that only shows up against the business requirements or test data.

## Verification

After fixes, `./evaluate_lab.sh` passes all 15 checks:

<img width="555" height="373" alt="evaluation-check-passed1" src="https://github.com/user-attachments/assets/4719eee6-7f72-4b37-b5f0-d9a6dfd5cf4d" />

```text
Results: 15 passed, 0 failed.
Lab evaluation passed.
```
