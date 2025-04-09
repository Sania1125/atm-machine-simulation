# atm-machine-simulation
Simple ATM machine simulator using Python and OOP
# ---------------------------------------------
# Project Title: ATM Machine Simulation System
# Author: Sania Irshad
# Roll No: BSM-23-19
# GitHub: https://github.com/Sania1125
# Description: A basic ATM simulation using OOP in Python.
# ---------------------------------------------

class ATM:
    def __init__(self, user_name, pin, balance):
        self.user_name = user_name
        self.__pin = pin
        self.__balance = balance

    def authenticate(self, entered_pin):
        return self.__pin == entered_pin

    def check_balance(self):
        return f"💰 Current Balance: Rs.{self.__balance}"

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return f"✅ Rs.{amount} deposited successfully."
        else:
            return "❌ Invalid deposit amount."

    def withdraw(self, amount):
        if amount <= self.__balance:
            self.__balance -= amount
            return f"✅ Rs.{amount} withdrawn successfully."
        else:
            return "❌ Insufficient balance."


# --- Main Program Starts Here ---

if __name__ == "__main__":
    atm = ATM("Sania", "1234", 5000)

    print("🏧 Welcome to ATM Machine")
    entered_pin = input("Enter your 4-digit PIN: ")

    if atm.authenticate(entered_pin):
        print(f"Hello, {atm.user_name}!\n")

        while True:
            print("\n1. Check Balance\n2. Deposit Money\n3. Withdraw Money\n4. Exit")
            choice = input("Choose an option: ")

            if choice == "1":
                print(atm.check_balance())
            elif choice == "2":
                amount = float(input("Enter amount to deposit: "))
                print(atm.deposit(amount))
            elif choice == "3":
                amount = float(input("Enter amount to withdraw: "))
                print(atm.withdraw(amount))
            elif choice == "4":
                print("🚪 Thank you for using ATM. Goodbye!")
                break
            else:
                print("❌ Invalid option. Try again.")
    else:
        print("❌ Incorrect PIN. Access Denied.")
