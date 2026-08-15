Prerequistes 

During the begining stages of this lab we updated and checked that both bash and python3 were running its most up to date versions.

The chmod +x audit_menu.sh evaluate_lab.sh was excutable as you see in the screenshots
<img width="1200" height="84" alt="Screenshot 2026-07-28 193806" src="https://github.com/user-attachments/assets/0547c794-0183-4a87-98fb-da6b37bdb4c0" />
<img width="1662" height="843" alt="Screenshot 2026-07-28 193700" src="https://github.com/user-attachments/assets/ec75b339-b2d5-4919-bd93-1e1fdf6bdaf6" />
<img width="1265" height="290" alt="Screenshot 2026-07-28 194041" src="https://github.com/user-attachments/assets/c394fc15-2318-40ec-bb9d-11a2b7e3c92e" />

Scenario 1-Account Audit
Command : python3 scripts/account_audit.py
We used the above commands to get the expected output. Lots of editing and mistakes were made to get us to the expected outcome. The edits and outcomes are found in the screenshots
<img width="1051" height="517" alt="Screenshot 2026-07-28 2040-bashChange1-1" src="https://github.com/user-attachments/assets/51a51529-bc8e-4e41-9fac-2644b12fe265" />

Scenario 2 -Department Summary
To run the command for Windows you have to take the
3 off python3 scripts/account_audit.py and leave it on 
for Macs. 
<img width="1068" height="600" alt="image" src="https://github.com/user-attachments/assets/c0238b66-068f-47ea-aa14-570d8ead822f" />
  
Scenario 3-Valid Employee Input and expected result
We were able to get the expected results from the inputs that were provided to us, as seen in the screen shot
<img width="556" height="810" alt="Screenshot 2026-08-07 1918-scanario3" src="https://github.com/user-attachments/assets/8a47c9ad-b411-4de2-a528-537321424fe1" />

Scenario 4 -Invalid Employee Input
Input: Username:
Department: Legal
Days since last login: 44

Made many adjustments to get the desired results as seen in the screenshots
Expected results
<img width="750" height="273" alt="Screenshot 2026-07-29 2056-blankmenutest" src="https://github.com/user-
attachments/assets/0f618845-ef36-4129-89ca-5632117715ef" />
<img width="423" height="227" alt="Screenshot 2026-07-29 2048-BashRunFour1-3" src="https://github.com/user-attachments/assets/2e9baa1d-67e0-40dc-9285-e62baa949072" />
<img width="973" height="497" alt="Screenshot 2026-07-29 2047-BashRunFour1-2" src="https://github.com/user-attachments/assets/bc763bac-2606-4ced-bbab-b3373571a144" />

Scenario 5 — Full Orchestration Flow
Menu input sequence:
In order to get the script to run in order, step 3 was moved upward to step 1, then the rest were pushed down.
New order = 3,1,2,3,4
Proof:
Before: <img width="1035" height="842" alt="Screenshot 2026-08-07 1922-bashtweak1-1" src="https://github.com/user-attachments/assets/54b78013-fcc7-4c0d-992f-6c56675ae935" />
After: <img width="721" height="916" alt="Screenshot 2026-08-07 1928-bashtweak1-2" src="https://github.com/user-attachments/assets/e3c4bb62-6be9-4807-a2a3-88dd631ce73f" />
