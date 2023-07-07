.. code:: ipython3

    import csv

.. code:: ipython3

    def calculate_profit_losses(file_path="./budget_data.csv"):
        total_months = 0
        net_total = 0
        changes = []
        greatest_increase = ["", 0]
        greatest_decrease = ["", 0]

.. code:: ipython3

    total_months = 0 #initialize total_months to 0
    net_total = 0
    changes = []
    greatest_increase = ["", 0]
    greatest_decrease = ["", 0]
    
    with open("./budget_data.csv", 'r') as file:
        csv_reader = csv.reader(file)
        header = next(csv_reader) #skip the header row
    
    
        # Read the first row to initialize variables
        first_row = next(csv_reader)
        total_months += 1
        net_total += int(first_row[1])
        previous_profit_loss = int(first_row[1])
    
        # Iterate through the remaining rows
        for row in csv_reader:
            total_months += 1
            current_profit_loss = int(row[1])
            net_total += current_profit_loss
        
        #Calculate the change in profit/loss
            change = current_profit_loss - previous_profit_loss
            changes.append(change)
        
        # Check for the greatest increase and decrease
            if change > greatest_increase[1]:
                greatest_increase = [row[0], change]
            if change < greatest_decrease[1]:
                greatest_decrease = [row[0], change]
            
            previous_profit_loss = current_profit_loss

.. code:: ipython3

    #Calculate the average change
    average_change = sum(changes) / len(changes)

.. code:: ipython3

    #Print the results
    print("Financial Analysis")
    print("----------------------------")
    print(f"Total Months: {total_months}")
    print(f"Total: ${net_total}")
    print(f"Average Change: ${average_change: .2f}")
    print(f"Greatest Increase in Profits: {greatest_increase[0]} (${greatest_increase[1]})")
    print(f"Greatest Decrease in Profits: {greatest_increase[0]} (${greatest_decrease[1]})")


.. parsed-literal::

    Financial Analysis
    ----------------------------
    Total Months: 86
    Total: $22564198
    Average Change: $-8311.11
    Greatest Increase in Profits: Aug-16 ($1862002)
    Greatest Decrease in Profits: Aug-16 ($-1825558)
    

