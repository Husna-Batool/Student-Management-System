# Student-Management-System

students = []

#function to calculate grade
def calculate_grade(marks):
    if marks>=90:
        return "A+"
    elif marks>=80:
        return "A"
    elif marks>=70:
        return "B"
    elif marks>=60:
        return "C"
    elif marks>=50:
        return "D"
    else:
        return "F"
    
#function to Add Student
def add_student():
    print("\n Add Student ")
    student_id = input("Enter Student id: ")
    
#Check if student id already exists
    for student in students:
        if student["ID"] == student_id:
            print("Student ID already exists")
            return
    name = input("Enter Student's name: ")
 # Validate Age
    while True:
        try:
            age = int(input("Enter Age: "))
            if age > 0:
                break
            else:
                print("Age must be greater than 0.")
        except ValueError:
            print("Please enter a valid number.")

    course = input("Enter Course: ")

#Validate Marks
    while True:
        try:
            marks = float(input("Enter Marks (0-100): "))
            if 0 <= marks <= 100:
                break
            else:
                print("Marks must be between 0 and 100.")
        except ValueError:
            print("Please enter valid marks.")

    grade = calculate_grade(marks)

#Store student information in dictionary
    student = {
        "ID": student_id,
        "Name": name,
        "Age": age,
        "Course": course,
        "Marks": marks,
        "Grade": grade
    }

    students.append(student)

    print("Student added successfully!")

#Function to View All Students
def view_students():
    print("\n Student Records ")

    if len(students) == 0:
        print("No student records found.")
        return

    for student in students:
        print("Student ID :", student["ID"])
        print("Name       :", student["Name"])
        print("Age        :", student["Age"])
        print("Course     :", student["Course"])
        print("Marks      :", student["Marks"])
        print("Grade      :", student["Grade"])

#Function to Search Student
def search_student():
    print("\n Search Student ")
    search_id = input("Enter Student ID: ")
    for student in students:
        if student["ID"] == search_id:
            print("\nStudent Found")
            print("Student ID :", student["ID"])
            print("Name       :", student["Name"])
            print("Age        :", student["Age"])
            print("Course     :", student["Course"])
            print("Marks      :", student["Marks"])
            print("Grade      :", student["Grade"])
            return

    print("Student not found.")

#Function to Update Student
def update_student():
    print("\n Update Student ")
    update_id = input("Enter Student ID: ")
    for student in students:
        if student["ID"] == update_id:

            print("Student Found!")
            student["Name"] = input("Enter New Name: ")

            while True:
                try:
                    age = int(input("Enter New Age: "))
                    if age > 0:
                        student["Age"] = age
                        break
                    else:
                        print("Age must be greater than 0.")
                except ValueError:
                    print("Invalid input.")

            student["Course"] = input("Enter New Course: ")

            while True:
                try:
                    marks = float(input("Enter New Marks: "))
                    if 0 <= marks <= 100:
                        student["Marks"] = marks
                        student["Grade"] = calculate_grade(marks)
                        break
                    else:
                        print("Marks should be between 0 and 100.")
                except ValueError:
                    print("Invalid marks.")

            print("Student information updated successfully!")
            return

    print("Student not found.")

#Function to Delete Student
def delete_student():
    print("\n Delete Student ")
    delete_id = input("Enter Student ID: ")
    for student in students:
        if student["ID"] == delete_id:
            students.remove(student)
            print("Student deleted successfully!")
            return

    print("Student not found")
while True:

    print("\n")
    print(" Student Management System ")
    print("1. Add Student")
    print("2. View All Students")
    print("3. Search Student")
    print("4. Update Student Information")
    print("5. Delete Student")
    print("6. Exit")
    choice = input("Enter your choice (1-6): ")

    if choice == "1":
        add_student()

    elif choice == "2":
        view_students()

    elif choice == "3":
        search_student()

    elif choice == "4":
        update_student()

    elif choice == "5":
        delete_student()

    elif choice == "6":
        print("\nThank you for using Student Management System")
        break

    else:
        print("Invalid choice! Please enter a number from 1 to 6")
