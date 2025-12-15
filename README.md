# Restaurant Management System

menu = {
    1: ["Masala Dosa", 50],
    2: ["Idli Vada", 40],
    3: ["Paneer Fried Rice", 120],
    4: ["Veg Biryani", 150],
    5: ["Fresh Lime Soda", 30]
}

order_list = []

print("--------------------------------------")
print(" Welcome to South Spice Restaurant ")
print("--------------------------------------")
print("MENU:")
for key, value in menu.items():
    print(f"{key}. {value[0]} - ₹{value[1]}")

while True:
    try:
        choice = int(input("\nEnter item number: "))
        if choice not in menu:
            print("Invalid choice! Try again.")
            continue
        
        qty = int(input("Enter quantity: "))
        
        item_name = menu[choice][0]
        price = menu[choice][1] * qty
        
        order_list.append([item_name, qty, price])

        more = input("Do you want to order more? (yes/no): ").lower()
        if more == "no":
            break
    except:
        print("Invalid input! Try again.")

# Bill Calculation
subtotal = sum(item[2] for item in order_list)
gst = subtotal * 0.05
service_charge = subtotal * 0.02
total = subtotal + gst + service_charge

print("\n======== FINAL BILL ========")
print("{:<20} {:<10} {:<10}".format("Item", "Qty", "Price"))

for item in order_list:
    print("{:<20} {:<10} {:<10}".format(item[0], item[1], item[2]))

print("----------------------------")
print(f"Subtotal:        ₹{subtotal}")
print(f"GST (5%):        ₹{gst}")
print(f"Service Charge:  ₹{service_charge}")
print("============================")
print(f"TOTAL AMOUNT:    ₹{total}")
print("============================\n")

print(" Thank you! Visit Again ")
