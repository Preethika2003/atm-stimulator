print("Welcome to the ATM")
class ATM:
    pin = "1515"
    balance = 0
    def verify_pin():
        attempts = 3
        while attempts > 0:
            entered_pin = input("Enter your PIN: ")
            if entered_pin == ATM.pin:
                print("PIN verified successfully!")
                return True
            else:
                attempts -= 1
                if attempts > 0:
                    print(f"Invalid PIN! {attempts} attempts remaining.")
                else:
                    print("Too many incorrect attempts. Exiting...")
                    return False
    def deposit():
        amount = float(input("Enter amount to deposit: ₹"))
        if amount > 0:
            ATM.balance += amount
            print(f"₹{amount} deposited successfully!")
        else:
            print("Invalid deposit amount!")
        ATM.check_balance()
    def withdraw():
        amount = float(input("Enter amount to withdraw: ₹"))
        if amount > ATM.balance:
            print("Insufficient funds!")
        elif amount <= 0:
            print("Invalid withdrawal amount!")
        else:
            ATM.balance -= amount
            print(f"₹{amount} withdrawn successfully!")
        ATM.check_balance()
    def check_balance():
        print(f"Current balance: ₹{ATM.balance}\n")
    def atm_menu():
        if not ATM.verify_pin():
            return

        while True:
            print("\n1. Deposit Money\n2. Withdraw Money\n3. Check Balance\n4. Exit")
            choice = input("Select an option (1-4): ")

            if choice == "1":
                ATM.deposit()
            elif choice == "2":
                ATM.withdraw()
            elif choice == "3":
                ATM.check_balance()
            elif choice == "4":
                print("Thank you for using the ATM. Goodbye!")
                break
            else:
                print("Invalid option! Please select a valid choice.")
ATM.atm_menu()
