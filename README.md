#  Daily Task python-file
tasks = []

def show_menu():
    print("\n📋 TO-DO LIST APP")
    print("1. Add a task")
    print("2. View tasks")
    print("3. Mark task as done")
    print("4. Remove a task")
    print("5. Quit")

def add_task():
    task = input("Enter a new task: ")
    tasks.append({"task": task, "done": False})
    print("Task added!")

def view_tasks():
    if not tasks:
        print("No tasks added yet.")
        return
    print("\nYour Tasks:")
    for i, t in enumerate(tasks):
        status = "✅" if t["done"] else "❌"
        print(f"{i+1}. {t['task']} [{status}]")

def mark_done():
    view_tasks()
    try:
        task_no = int(input("Enter task number to mark as done: ")) - 1
        if 0 <= task_no < len(tasks):
            tasks[task_no]["done"] = True
            print("Marked as done!")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Please enter a valid number.")

def remove_task():
    view_tasks()
    try:
        task_no = int(input("Enter task number to remove: ")) - 1
        if 0 <= task_no < len(tasks):
            removed = tasks.pop(task_no)
            print(f"Removed task: {removed['task']}")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Please enter a valid number.")

def main():
    while True:
        show_menu()
        choice = input("Choose an option (1-5): ")
        
        if choice == "1":
            add_task()
        elif choice == "2":
            view_tasks()
        elif choice == "3":
            mark_done()
        elif choice == "4":
            remove_task()
        elif choice == "5":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please choose 1-5.")

# Start the app
main()

