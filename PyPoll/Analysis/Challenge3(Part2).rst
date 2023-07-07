.. code:: ipython3

    import csv

.. code:: ipython3

    def analyze_votes(file_path="./election_data.csv"):
        # Inititalize variables
        total_votes = 0
        candidates = {}

.. code:: ipython3

    total_votes = 0
    candidates = {}
    
    with open("C:\\Users\\Drenaline\\Documents\\TCC Data Analytics Bootcamp\\Challenges\\Module 3 Challenge\\Starter_Code\\PyPoll\\Resources\\election_data.csv", 'r') as file:
        csv_reader = csv.reader(file)
        next(csv_reader) # Skip the header row
        
        # Iterate over each row in the dataset
        for row in csv_reader:
            # Extract the candidate name from the row
            candidate = row[2]
            
            # Count the total number of votes
            total_votes += 1
            
            # Update the vote count for the candidate
            if candidate in candidates:
                candidates[candidate] += 1
            else:
                candidates[candidate] = 1
                
        # Calculate the percentage of votes and find the winner
        winner = ""
        max_votes = 0
        percentages = {}
        
        for candidate, votes in candidates.items():
            percentage = (votes / total_votes) * 100
            percentages[candidate] = round(percentage, 2)
            
            if votes > max_votes:
                max_votes = votes
                winner = candidate
        

.. code:: ipython3

    # Printing the Results!! Woo!
    print("Election Results")
    print("-------------------------")
    print(f"Total Votes: {total_votes}")
    print("-------------------------")
    
    for candidate, votes in candidates.items():
        percentage = percentages[candidate]
        print(f"{candidate}: {percentage}% ({votes})")
        
    print("--------------------------")
    print(f"Winner: {winner}")
    print("--------------------------")


.. parsed-literal::

    Election Results
    -------------------------
    Total Votes: 369711
    -------------------------
    Charles Casper Stockham: 23.05% (85213)
    Diana DeGette: 73.81% (272892)
    Raymon Anthony Doane: 3.14% (11606)
    --------------------------
    Winner: Diana DeGette
    --------------------------
    

