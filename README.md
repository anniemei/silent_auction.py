
#-------------------------------------------------------------------------------
# Name:        module1
# Purpose:
#
# Author:      meia
#
# Created:     02/09/2016

highest_bid = 0.00

reserve_price = ""
reserve_price = int(input("What is the reserved price?"))
print ("Reserved Price is $", reserve_price)


def get_bids(names, bid_order):
    print ("Auction has started")
    name = ""
    while name.upper()!= "F":
        name = input("What is the customer's name? (\"F\" to finish)")
        if name.upper()!= "F":
            names.append(name)
            bid_order.append(read_int("How much would " + name + " like to bid?"))

def show_bids(names, bid_order):
#calculate against reserved price
    print("Showing bids")
    for i in range(len(names)):
        if bid_order[i] > reserve_price and bid_order[i] > highest_bid:
            print("{} made a ${:.2f} bid.".format(names, bid_order[i]))
        else:
            print("This does not meet the reserve price. Please try again")


def show_report(bid_order):
#displays summary
    if len(names) == 0:
       print ("No orders")
    else:
        total = 0
        for bids in bid_order:
            total += bids
        print ("Summary")
        print ("Total bid: $", total)

def read_int(prompt):
    choice = -1;
    while choice == -1:
        try:
            choice = int(input(prompt))
        except ValueError:
            print ("Not a valid integer")
    return choice

#main routine
names = []
bid_order = []
get_bids(names, bid_order)
show_bids(names, bid_order) #Cannot get the highest bid to be working
show_report(bid_order)
