# 🎓 Educational Organisation Using ServiceNow  

> 🏫 **K.S.K College of Engineering and Technology**  
> 💻 **Department of Computer Science and Engineering**

---

## 👥 Team Details  

| Role | Name |
|------|------|
| **Team ID** | NM2025TMID05478 |
| **Team Size** | 4 |
| **Team Leader** | Nithish C |
| **Team Member 1** | Kumaresan G |
| **Team Member 2** | Vasanth R |
| **Team Member 3** | Vinith R |

---

## 🧩 Problem Statement  

Educational institutions often face challenges in managing large volumes of student and staff information.  
Manual processes in **admissions**, **records management**, and **progress tracking** result in inefficiency, duplication, and human errors.  

> This project introduces a **ServiceNow-based Educational Management System** that automates and centralizes all institutional workflows to improve efficiency, transparency, and user experience.

---

## 🎯 Project Objectives  

✅ Develop a centralized data system for students and staff.  
✅ Automate workflows for admission and progress tracking.  
✅ Enable real-time updates and quick data access.  
✅ Generate reports and analytics for informed decision-making.  
✅ Improve collaboration between administration and faculty.  
✅ Minimize manual errors through automation.

---

## 🛠️ Skills & Technologies Used  

| Category | Details |
|-----------|----------|
| **Platform** | ServiceNow |
| **Languages** | JavaScript (Client Scripts) |
| **ServiceNow Components** | Forms, Tables, Workflows, Update Sets, Catalogs |
| **Other Tools** | Process Flow Designer, Number Maintenance, Report Builder |

---

## 🚀 Development Workflow  

### ⚙️ Step 1: ServiceNow Instance Setup  
- Visit [ServiceNow Developer Portal](https://developer.servicenow.com).  
- Request a **Personal Developer Instance**.  
- Log in and configure your workspace.

---

### 🧱 Step 2: Create Local Update Set  
**Path:** `All → Local Update Sets → New`  
- Name: `Educational Organisation`  
- Submit → Click **"Make Current"**

---

### 🧩 Step 3: Table Creation  

#### 🔹 Salesforce Table  
- Navigate: `System Definition → Tables → New`  
- Label: `Salesforce`  
- Check “Extensible” under *Controls*  
- Create fields:  
  - Admission Number (Display = True)  
  - Grade  
  - Student Name  
  - Father Name  
  - Mother Name  
  - Contact Numbers  
  - Address Fields  

---

#### 🔹 Admission Table  
- Extended from **Salesforce Table**  
- Create fields:  
  - Admission Date  
  - Course Name  
  - Department  
  - Email ID  
  - Status  

---

#### 🔹 Student Progress Table  
- Create fields for:  
  - Subject Marks (Subject1, Subject2, …)  
  - Total Marks  
  - Percentage  
  - Result  

---

### 🧰 Step 4: Form Design  
- Go to **Form Layout** and **Form Designer** for all tables.  
- Organize and group fields logically using drag-and-drop.

---

### 🔢 Step 5: Number Maintenance  
`System Definition → Number Maintenance → New`  
- Table: `Salesforce`  
- Prefix: `SALES`  
- Digits: `4`

---

### 🔄 Step 6: Process Flow Configuration  
`Process Flow → New`  
- Define stages:  New → InProgress → Joined → Rejected → Rejoined → Closed → Cancelled

- 
---

## 🧠 Core Client Scripts  

### 🧮 1️⃣ Calculate Total Marks  

```
function calculateTotal() {
var s1 = parseFloat(g_form.getValue('u_subject1')) || 0;
var s2 = parseFloat(g_form.getValue('u_subject2')) || 0;
var s3 = parseFloat(g_form.getValue('u_subject3')) || 0;
var s4 = parseFloat(g_form.getValue('u_subject4')) || 0;
var s5 = parseFloat(g_form.getValue('u_subject5')) || 0;
var s6 = parseFloat(g_form.getValue('u_subject6')) || 0;
var total = s1 + s2 + s3 + s4 + s5 + s6;
g_form.setValue('u_total_marks', total);
}
📊 2️⃣ Calculate Percentage
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') return;

   var total = parseFloat(g_form.getValue('u_total_marks'));
   if (isNaN(total) || total < 0 || total > 600) {
       g_form.showFieldMsg('u_total_marks', 'Total should be between 0 and 600', 'error');
       g_form.setValue('u_percentage', '');
       return;
   }

   var percentage = (total / 600) * 100;
   g_form.setValue('u_percentage', percentage.toFixed(2));
}


🏁 3️⃣ Result Script
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') return;

   var percentage = parseFloat(g_form.getValue('u_percentage'));
   if (percentage >= 40) {
      g_form.setValue('u_result', 'Pass');
   } else {
      g_form.setValue('u_result', 'Fail');
   }
} 



📊 Output Snapshots

📸 Attach screenshots here of:

Admission Form

Student Progress Form

Calculated Percentage and Result

Process Flow


| Deliverable               | Description                                |
| ------------------------- | ------------------------------------------ |
| **Source Code**           | All client scripts and form configurations |
| **Documentation**         | Project report with screenshots            |
| **GitHub Repository**     | Upload all code and screenshots            |
| **Demo Video (Optional)** | Project working demo video                 |


🏆 Results

✅ Automated student admission and academic tracking
✅ Real-time calculation of marks and percentage
✅ Centralized database with error-free data management
✅ Streamlined institutional workflow

🧠 Conclusion

The Educational Organisation Using ServiceNow project showcases how ServiceNow’s automation capabilities can transform academic administration.
It brings together students, staff, and administrators under a single unified system that ensures efficiency, transparency, and reliability.

This digital transformation promotes smarter operations and data-driven decision-making in modern educational institutions.

📚 References

ServiceNow Documentation

ServiceNow Developer Site

YouTube Tutorials for ServiceNow Form Design and Flow

🌐 GitHub Details

📦 Repository Link: (Add your GitHub Repo URL here)

🎥 Demo Video: https://drive.google.com/file/d/1cAoGujoIO6yr6K36Z_s55Ec6cK_JGgnb/view?usp=sharing
