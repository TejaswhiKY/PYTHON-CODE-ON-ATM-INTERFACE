# ATM Interface in Python

import sys

# Sample user account data
accounts = {
    "12345": {"pin": "1111", "balance": 1000},
    "67890": {"pin": "2222", "balance": 2000}
}

def atm():
    print("\n===== Welcome to Python ATM =====")

    account_number = input("Enter your account number: ")

    if account_number not in accounts:
        print("❌ Invalid account number!")
        return

    pin = input("Enter your PIN: ")
    if pin != accounts[account_number]["pin"]:
        print("❌ Incorrect PIN!")
        return

    while True:
        print("\n--- ATM Menu ---")
        print("1. Check Balance")
        print("2. Deposit Money")
        print("3. Withdraw Money")
        print("4. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            print(f"✅ Your balance is: ${accounts[account_number]['balance']}")

        elif choice == "2":
            amount = float(input("Enter amount to deposit: "))
            accounts[account_number]["balance"] += amount
            print(f"✅ Deposited ${amount}. New balance: ${accounts[account_number]['balance']}")

        elif choice == "3":
            amount = float(input("Enter amount to withdraw: "))
            if amount > accounts[account_number]["balance"]:
                print("❌ Insufficient balance!")
            else:
                accounts[account_number]["balance"] -= amount
                print(f"✅ Withdrawn ${amount}. New balance: ${accounts[account_number]['balance']}")

        elif choice == "4":
            print("👋 Thank you for using Python ATM. Goodbye!")
            sys.exit()

        else:
            print("❌ Invalid option, please try again.")

# Run the ATM program
atm()
