# BUDGET-TRACKER
The budget tracker tracks income and expenses and displays a summery


**Course:** ITP 100 Software Design & Logic
**Author:** Samiullah Mushfiq
**Deliverable:** Algorithm Design (IPO, Flowchart, Psuedocode)

---

## 1. Problem Description & Scope
* **Problem:** Students need a command-line interface to enter income and expenses, keep track of how much money is either earned or spent in each category, and generate a monthly summary that tells them if they made a profit, or loss, or broke even.
* **Scope:**
  *  Features a continuous main loop with 2 hierarchical submenus (Income and Expense).
  *  Validates menu bounds (rejects values outside menu options) and duration inputs (rejects negative numbers).
  *  Aggregates total amount in memory during execution and outputs a progress summary on demand.
  *  Terminates cleanly when the user selects the Exit option.

---

## 2. IPO Chart (Input - Process - Output)

| Input | Processing | Output |
| :--- | :--- | :--- |
| • `main_choice` (Integer: 1-4)<br>• `sub_choice` (Integer: 1-3)<br>• `amount` (Real: ≥ 0) | 1. Initialize income and expense totals to zero.<br>2. Display main menu until user selects Exit.<br>3. Validate main menu choices (1-4).<br>4. If Income selected:<br>  a. Display income submenu.<br>  b. Validate category choice (1-3).<br>  c. Input amount and validate amount ≥ 0.<br>  d. Add amount to total income.<br>5. If Expense selected:<br>  a. Display expense submenu.<br>  b. Validate category choice (1-3).<br>  c. Input amount and validate amount ≥ 0.<br>  d. Add amount to total expenses.<br>6. If Summary selected:<br>  a. Calculate net balance.<br>  b. Determine financial status.<br>  c. Display summary report.<br>7. Exit when user selects option 4. | • Error messages for invalid input<br>• Confirmation messages for recorded income/expense entries<br>• Financial Summary showing:<br>  - Total Income<br>  - Total Expenses<br>  - Net Balance<br>  - Financial Status Message<br>• Exit goodbye message |


---
## 3. Pseudocode

```
MODULE Main()
    DECLARE Integer total_income = 0
    DECLARE Integer total_expense = 0
    DECLARE Integer total_amount = 0
    DECLARE String main_choice = ""
    DECLARE String sub_choice = ""
    DECLARE Real amount = 0.0
    DECLARE String option_name = ""

    DISPLAY "=============================="
    DISPLAY "    PERSONAL BUDGET TRACKER   "
    DISPLAY "=============================="

    WHILE True
        // Step 1: Main Menu & Input Validation
        DISPLAY "---MAIN MENU---"
        DISPLAY "1. Log Income"
        DISPLAY "2. Log Expense"
        DISPLAY "3. View Financial Summary"
        DISPLAY "4. Exit"
        DISPLAY "Enter your choice (1-4):"
        INPUT main_choice

        WHILE main_choice != 1 AND main_choice != 2 AND main_choice != 3 AND main_choice != 4
            DISPLAY "Invalid. Choice must be 1, 2, 3, or 4. Try Again:"
            INPUT main_choice
        END WHILE

        // Step 2. Route Submenus and Actions
        IF main_choice == 1 THEN
            DISPLAY "--- INCOME MENU ---"
            DISPLAY "1. Design"
            DISPLAY "2. Coding"
            DISPLAY "3. User Documentation"
            DISPLAY "Enter income option (1-3):"
            INPUT sub_choice

            WHILE sub_choice != 1 AND sub_choice != 2 AND sub_choice != 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try again!"
                INPUT sub_choice
            END WHILE

            IF sub_choice == 1 THEN
                option_name = "Design"
            ELSE IF sub_choice == 2 THEN
                option_name = "Coding"
            ELSE
                option_name "User Documentation"
            END IF

            DISPLAY "Enter income amount:"
            INPUT amount
            WHILE amount < 0
                DISPLAY "Invalid. Please enter amount >= 0:"
                INPUT amount
            END WHILE

            total_income = total_income + amount
            DISPLAY "Successfully added ", amount, "dollars for", option_name, "."

         ELSE IF main_choice == 2 THEN
             DISPLAY "--- EXPENSE MENU ---"
             DISPLAY "1. Software"
             DISPLAY "2. Equipment"
             DISPLAY "3. Workspace"
             DISPLAY "Enter expense option (1-3):"

             WHILE sub_choice != 1 AND sub_choice != 2 AND sub_choice != 3
                 DISPLAY "Invalid. Please enter 1, 2, or 3. Try again!"
             END WHILE

             IF sub_choice == 1 THEN
                 option_name = "Software"
             ELSE IF sub_choice == 2 THEN
                 option_name = "Equipment"
             ELSE
                 option_name = "Workspace"
             END IF

             DISPLAY "Enter expense amount:"
             INPUT amount
             wHILE amount < 0
                 DISPLAY "Invalid. Please enter amount >= 0:"
                 INPUT amount
             END WHILE

             total_expense = total_expense + amount
             DISPLAY "Succesfully added ", amount, "dollars for", option_name, "."

        ELSE IF main_choice == 3 THEN
            total_amount = total_income - total_expense
            DISPLAY "========================================="
            DISPLAY "          FINANCIAL SUMMARY              "
            DISPLAY "========================================="
            DISPLAY "Total Income:", total_income
            DISPLAY "Total Expenses:", total_expense
            DISPLAY "Net Balance:", total_amount

            IF total_amount >= 1 THEN
                DISPLAY "You are profitable this month!"
            ELSE IF total_amount = 0 THEN
                DISPLAY "You broke even this month!"
            ELSE IF total_amount <= 0 THEN
                DISPLAY "You are at a loss this month!"
            ELSE
                DISPLAY "Status: No amount logged yet."
            END IF
            DISPLAY "========================================="
         ELSE If main_choice == 4 THEN
            DISPLAY "Thank you for using Personal Budget Tracker!"
            BREAK
         END IF
       END WHILE
END MODULE

```
 

