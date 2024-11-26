# Welcome to the Cash Flow Minimizer System README!

This system minimizes the number of transactions among multiple banks in different corners of the world that use different modes of payment. There is one World Bank (with all payment modes) to act as an intermediary between banks that have no common mode of payment.

---

## Getting Started

Let's take an example. Say we have the following banks:

- **Bank of America (World Bank)**
- **Wells Fargo**
- **Royal Bank of Canada**
- **Westpac**
- **National Australia Bank**
- **Goldman Sachs**

---

### Payments to be Done

| **Debtor Bank**              | **Creditor Bank**         | **Amount** |
|-------------------------------|---------------------------|------------|
| Goldman Sachs                | Bank of America           | Rs 100     |
| Goldman Sachs                | Wells Fargo               | Rs 300     |
| Goldman Sachs                | Royal Bank of Canada      | Rs 100     |
| Goldman Sachs                | Westpac                   | Rs 100     |
| National Australia Bank      | Bank of America           | Rs 300     |
| National Australia Bank      | Royal Bank of Canada      | Rs 100     |
| Bank of America              | Wells Fargo               | Rs 400     |
| Wells Fargo                  | Royal Bank of Canada      | Rs 200     |
| Royal Bank of Canada         | Westpac                   | Rs 500     |

---

This is represented below as a directed graph with the directed edge representing debts. 
![image](https://github.com/user-attachments/assets/99e5c89c-b311-4029-bbce-ef1e884069ff)


#### Payment Modes

Each bank only supports a set of payment modes and can make or receive payments only via those modes. **Only the World Bank supports all payment modes.**

For this example, the available payment modes are:

- **Google_Pay**
- **AliPay**
- **Paytm**

### Supported Payment Modes by Each Bank

| Bank                       | Supported Payment Modes           |
|----------------------------|------------------------------------|
| Bank_of_America            | Google_Pay, AliPay, Paytm         |
| Wells_Fargo                | Google_Pay, AliPay                |
| Royal_Bank_of_Canada       | AliPay                            |
| Westpac                    | Google_Pay, Paytm                 |
| Goldman_Sachs              | Paytm                             |
| National_Australia_Bank    | AliPay, Paytm                     |

---

## Algorithm

To minimize cash flow, we calculate the **net amount** for each bank:

**Net Amount** = `[Sum of all credits (amounts to be received)] - [Sum of all debits (amounts to pay)]`

### Steps:

1. Identify the **max debtor** (Bank X with net amount `x`) and **max creditor** (Bank Y with net amount `y`) among the banks.  
2. Ensure Bank X and Bank Y share at least one common payment mode (say `M1`).  
3. Calculate `z = min(|x|, y)` (minimum of the absolute value of `x` and `y`).  
4. Settle `z` by transferring from Bank X to Bank Y via `M1`.  

### After Settlement:

- If `|x| < y`:  
  Bank X is **completely settled** and removed from the list.  
- If `|x| > y`:  
  Bank Y is **completely settled** and removed from the list.  
- If `|x| = y`:  
  Both Bank X and Bank Y are **completely settled** and removed from the list.

5. Repeat the process for the remaining banks until all debts are cleared.

---

### Example Output

For the current example, the transactions for **minimum cash flow** are as follows:

![image](https://github.com/user-attachments/assets/b2846649-da1a-41f0-bb2e-ad61846bfb8b)

So this is the required answer.

---

## How to Use?

This system is completely menu-driven. When you run the **C Application**, it will guide you through the process and display the final output.  
Below is the execution of our current example:

![Screenshot 2024-11-26 145655](https://github.com/user-attachments/assets/26271c32-eabf-4592-b325-deaddc720a1d)
![Screenshot 2024-11-26 145711](https://github.com/user-attachments/assets/9f5a90b5-bb34-4a21-b904-38aff6806492)


---

## Thank You!!

Enjoy using the **Cash Flow Minimizer System** to optimize and simplify financial transactions across multiple banks!




