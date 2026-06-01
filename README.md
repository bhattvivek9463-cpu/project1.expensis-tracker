# project1.expensis-tracker
A simple and user-friendly Expense Tracker built with Python to manage daily income and expenses, track spending, and monitor financial records efficiently.
# Expense Tracker Project

expenses_list = []

print(" Welcome to Expense Tracker ")
print(" Kharcha kam kiya karo ")


while True:

    print("\n========= MENU =========")
    print("1. Add Expense")
    print("2. View All Expenses")
    print("3. View Total Expense")
    print("4. Exit")

    # input safety
    try:
        choice = int(input("Enter your choice: "))
    except ValueError:
        print("Please enter numbers only!")
        continue

    # 1. Add Expense
    if choice == 1:

        date = input("Enter expense date: ")
        category = input("Enter category (food/travel/shopping/books): ")
        description = input("Enter description: ")

        try:
            amount = float(input("Enter amount: "))
        except ValueError:
            print("Invalid amount!")
            continue

        expense = {
            "date": date,
            "category": category,
            "description": description,
            "amount": amount
        }

        expenses_list.append(expense)

        print("\n Expense added successfully!")

    # 2. View All Expenses
    elif choice == 2:

        if len(expenses_list) == 0:
            print("\n No expenses found!")

        else:
            print("\n======= ALL EXPENSES =======")

            count = 1

            for item in expenses_list:

                print(f"""
Expense #{count}
Date        : {item['date']}
Category    : {item['category']}
Description : {item['description']}
Amount      : {item['amount']}
------------------------------
""")

                count += 1

    # 3. View Total Expense
    elif choice == 3:

        total = 0

        for item in expenses_list:
            total += item["amount"]

        print(f"\n Total Expense = ₹{total}")

    # 4. Exit
    elif choice == 4:

        print("\n Thank you for using Expense Tracker!")
        break

    # Invalid choice
    else:
        print("\n Invalid choice! Please try again.")
