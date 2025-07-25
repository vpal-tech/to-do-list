todo_list = []

def show_menu():
    print("\n==== TO-DO LIST MENU ====")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Mark Task as Done")
    print("4. Delete Task")
    print("5. Exit")

def add_task():
    task = input("Enter a new task: ")
    todo_list.append({"task": task, "done": False})
    print("Task added!")

def view_tasks():
    if not todo_list:
        print("No tasks in the list.")
        return
    print("\nYour Tasks:")
    for i, item in enumerate(todo_list, 1):
        status = "✔️" if item["done"] else "❌"
        print(f"{i}. [{status}] {item['task']}")

def mark_done():
    view_tasks()
    try:
        task_no = int(input("Enter task number to mark as done: "))
        todo_list[task_no - 1]["done"] = True
        print("Task marked as done!")
    except (IndexError, ValueError):
        print("Invalid task number!")

def delete_task():
    view_tasks()
    try:
        task_no = int(input("Enter task number to delete: "))
        del todo_list[task_no - 1]
        print("Task deleted!")
    except (IndexError, ValueError):
        print("Invalid task number!")

# Main loop
while True:
    show_menu()
    choice = input("Choose an option (1-5): ")

    if choice == '1':
        add_task()
    elif choice == '2':
        view_tasks()
    elif choice == '3':
        mark_done()
    elif choice == '4':
        delete_task()
    elif choice == '5':
        print("Goodbye!")
        break
    else:
        print("Invalid choice! Try again.")

