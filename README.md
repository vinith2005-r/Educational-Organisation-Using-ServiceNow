🎓 Educational Organisation Using ServiceNow

KSK College of Engineering and Technology
Department of Computer Science and Engineering

🧑‍💻 Team Details
Role	Name
Team ID	NM2025TMID05478
Team Size	4
Team Leader	Nithish C
Team Member 1	Kumaresan G
Team Member 2	Vasanth R
Team Member 3	Vinith R
🧩 Problem Statement

Educational institutions often struggle with managing large volumes of student and staff information through manual or disconnected systems.
Tasks such as admissions, student record management, and progress tracking become time-consuming and prone to errors.
The lack of a unified digital platform leads to inefficiency, communication gaps, and delays in decision-making.

👉 This project addresses these challenges by developing an Educational Management System on ServiceNow to automate administrative workflows, centralize data, and improve institutional efficiency.

🎯 Objectives

Design and implement a centralized system for managing student and teacher information using ServiceNow.

Automate key processes such as admissions, attendance, and progress monitoring.

Enable real-time access and updates of academic and administrative data.

Improve coordination among departments and reduce manual workloads.

Generate reports and analytics for better decision-making.

Enhance transparency and user experience for students, faculty, and administrators.

🛠️ Skills and Technologies Used

Platform: ServiceNow

Skills:

ServiceNow Administration & Configuration

Form and Table Design

Workflow & Flow Designer

Reporting and Dashboard Creation

🚀 Project Development Steps
🧱 Step 1: Setting up ServiceNow Instance

Sign up at ServiceNow Developer Portal
.

Request a Personal Developer Instance.

Log in using your instance credentials.

⚙️ Step 2: Creating an Update Set

All → Local Update Sets → New

Name: Educational Organisation

Submit and Make Current

🧩 Step 3: Creating Tables
🔹 Salesforce Table

All → Tables → New

Label: Salesforce → API name auto-generates

Enable Extensible under Controls

Create columns (Admin Number, Grade, etc.)

For Admin Number: enable Display = True, and set Dynamic Default = Get Next Padded Number

🔹 Admission Table

Extend Table → Salesforce

Add Module → Salesforce

Create columns (Admission No, Student Name, Course Name, Department, Admission Date, Contact No, Email, Grade, Status, etc.)

🔹 Student Progress Table

Add Module → Salesforce

Create fields for subjects, total marks, percentage, and result.

🧰 Step 4: Form Layout & Design

Configure Form Layout and Form Design for all tables (Salesforce, Admission, Student Progress).

Arrange fields properly using drag & drop.

🔢 Step 5: Number Maintenance

All → Number Maintenance → New

Configure prefix and digits for Admin Number generation.

🔄 Step 6: Process Flow

All → Process Flow → New

Define stages in order:
New → InProgress → Joined → Rejected → Rejoined → Closed → Cancelled

💻 Step 7: Client Scripts
1️⃣ Auto-Populate Script (Admission Table)

Fetch related student details automatically when Admission Number changes.

2️⃣ Pincode Update Script

Auto-fill Mandal, City, and District based on Pincode.

3️⃣ Disable Fields Script (Student Progress)

Lock calculated fields like Total, Percentage, Result.

4️⃣ Total Update Script

Calculate total marks from individual subjects.

5️⃣ Result Script

Display “Pass” or “Fail” based on percentage range.

6️⃣ Percentage Script

Calculate percentage dynamically from total marks.

🧮 Example Script (Percentage Calculation)
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') {
      return;
   }

   var total = parseFloat(g_form.getValue('u_total_marks'));
   if (isNaN(total) || total < 0 || total > 600) {
       alert('Please enter a valid total mark between 0 and 600.');
       g_form.setValue('u_percentage', '');
       return;
   }

   var percentage = (total / 600) * 100;
   if (percentage > 100) {
       percentage = 100;
   }
   g_form.setValue('u_percentage', percentage.toFixed(2));
}

📊 Result

The ServiceNow-based Educational Management System demonstrates:
✅ Automated student admission and academic tracking
✅ Centralized, error-free data storage
✅ Simplified workflows
✅ Real-time reporting and analytics

🧾 Conclusion

The Educational Organisation Using ServiceNow project effectively modernizes the way educational institutions handle academic and administrative processes.
By leveraging ServiceNow’s workflow automation, forms, and reporting tools, this system improves efficiency, transparency, and accuracy — enabling smarter decision-making and seamless operations.

This project proves how cloud platforms like ServiceNow can revolutionize educational management, creating a more connected and intelligent academic environment.

🧠 Repository Information

GitHub: (Add your repo link here)
Project Report & Screenshots: /docs/ folder
Demo Video (Optional): Upload link or .mp4 in repo root
