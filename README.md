# Dictionary to store the support tickets
tickets = {}

# Function to create a new ticket
def create_ticket(customer_name, issue):
    ticket_id = len(tickets) + 1
    tickets[ticket_id] = {
        'customer_name': customer_name,
        'issue': issue,
        'status': 'Open',
        'assigned_to': None
    }
    print(f"Ticket created successfully! Ticket ID: {ticket_id}")

# Function to view all tickets
def view_tickets():
    if len(tickets) == 0:
        print("No tickets available.")
    else:
        for ticket_id, ticket_info in tickets.items():
            print(f"\nTicket ID: {ticket_id}")
            print(f"Customer Name: {ticket_info['customer_name']}")
            print(f"Issue: {ticket_info['issue']}")
            print(f"Status: {ticket_info['status']}")
            assigned_to = ticket_info['assigned_to'] if ticket_info['assigned_to'] else "Not assigned"
            print(f"Assigned to: {assigned_to}")

# Function to update the status of a ticket
def update_ticket_status(ticket_id, new_status):
    if ticket_id in tickets:
        tickets[ticket_id]['status'] = new_status
        print(f"Ticket {ticket_id} status updated to '{new_status}'.")
    else:
        print(f"Ticket ID {ticket_id} not found.")

# Function to assign a ticket to an agent
def assign_ticket(ticket_id, agent_name):
    if ticket_id in tickets:
        tickets[ticket_id]['assigned_to'] = agent_name
        print(f"Ticket {ticket_id} assigned to {agent_name}.")
    else:
        print(f"Ticket ID {ticket_id} not found.")

# Main function to interact with the user
def main():
    while True:
        print("\n--- Support Ticket System ---")
        print("1. Create a ticket")
        print("2. View all tickets")
        print("3. Update ticket status")
        print("4. Assign a ticket to an agent")
        print("5. Exit")

        try:
            choice = int(input("Enter your choice: "))

            if choice == 1:
                customer_name = input("Enter customer name: ")
                issue = input("Describe the issue: ")
                create_ticket(customer_name, issue)

            elif choice == 2:
                view_tickets()

            elif choice == 3:
                ticket_id = int(input("Enter ticket ID: "))
                new_status = input("Enter new status (Open, In Progress, Closed): ")
                update_ticket_status(ticket_id, new_status)

            elif choice == 4:
                ticket_id = int(input("Enter ticket ID: "))
                agent_name = input("Enter agent's name: ")
                assign_ticket(ticket_id, agent_name)

            elif choice == 5:
                print("Exiting the program. Thank you!")
                break

            else:
                print("Invalid choice. Please try again.")
        
        except ValueError:
            print("Please enter a valid number.")

if _name_ == "_main_":
    main()
