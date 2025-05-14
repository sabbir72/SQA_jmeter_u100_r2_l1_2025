# SQA_jmeter_u100_r2_l1_2025

# 🧪 JMeter Performance Test: BlazeMeter → JMeter → HTML Report (Win + Ubuntu)

This guide shows how to:

1. Record a `.jmx` test plan using BlazeMeter Chrome Extension
2. Run it with Apache JMeter in CLI (headless) mode
3. Generate `.jtl` result log
4. Export performance data as HTML report
5. Push the entire project into a GitHub repository

---

## 📦 Requirements

- Java JDK 8 or 11
- Apache JMeter (5.x or later)
- Git & github
- BlazeMeter Chrome Extension
- OS: ✅ Ubuntu or ✅ Windows

---

## 🧩 Step 1: Record Test Plan (`.jmx`) 



1. Install the [BlazeMeter Recorder Chrome Extension](https://chrome.google.com/webstore/detail/blazemeter-the-continuous/mbopgmdnpcbohhpnfglgohlbhfongabi)
2. Start recording, interact with your website.
3. Export the recording as `JMeter .jmx`
4. Save it as `Blaz_Rec.jmx`

---

## ⚙️ Step 2: Configure `jmeter.properties` for HTML Report (if you Need)



> Edit the file:  
**Ubuntu:**  
```bash
nano apache-jmeter-5.x/bin/jmeter.properties
```

**Windows:**  
Open `apache-jmeter-5.x\bin\jmeter.properties` with Notepad or VS Code.

Ensure the following properties are set:
```
# Save format
jmeter.save.saveservice.output_format=csv

# Ensure no header in .jtl (header  timestamp error )
jmeter.save.saveservice.print_field_names=false

# Timestamp format should be in milliseconds (required for report)
jmeter.save.saveservice.timestamp_format=ms

# Save individual data fields (keep these true to have proper data)
jmeter.save.saveservice.save.timestamp=true
jmeter.save.saveservice.save.label=true
jmeter.save.saveservice.save.response_code=true
jmeter.save.saveservice.save.response_message=true
jmeter.save.saveservice.save.thread_name=true
jmeter.save.saveservice.save.data_type=true
jmeter.save.saveservice.save.success=true
jmeter.save.saveservice.save.bytes=true
jmeter.save.saveservice.save.sent_bytes=true
jmeter.save.saveservice.save.grpThreads=true
jmeter.save.saveservice.save.allThreads=true
jmeter.save.saveservice.save.latency=true
jmeter.save.saveservice.save.connect_time=true
jmeter.save.saveservice.save.url=true
---

## 🧪 Step 3: Run JMeter Test Plan

**Ubuntu:**

```bash
jmeter -n -t /home/user/PerformanceTest/Blaz_Rec.jmx -l /home/user/PerformanceTest/result.jtl 
```

**Windows (CMD):**

```cmd
jmeter -n -t C:\PerformanceTest\Blaz_Rec.jmx -l C:\PerformanceTest\result.jtl
```

---

## 📊 Step 4: Generate HTML Report

**Ubuntu:**

```bash
jmeter -g /home/user/PerformanceTest/result.jtl -o /home/user/PerformanceTest/html-report
```

**Windows (CMD):**

```cmd
jmeter -g C:\PerformanceTest\result.jtl -o C:\PerformanceTest\html-report
```

---

## 🌐 Step 5: View the Report

**Ubuntu:**

```bash
xdg-open /home/user/PerformanceTest/html-report/index.html
```

**Windows:**

Just double-click `index.html` from `html-report` folder, or:

```cmd
start C:\PerformanceTest\html-report\index.html
```

---

---

## 🗃️ Git Workflow (for Both OS)

```bash
git init
git add .
git commit -m "Initial JMeter test setup with HTML report"
git branch -M main
git remote add origin https://github.com/your-username/your-repo-name.git
git push -u origin main
```

---

## 📂 Recommended Project Structure

```
PerformanceTest/
├── TestPlan.jmx
├── result.jtl
├── html-report/
│   └── index.html
├── run-test.sh (Ubuntu only)
└── README.md
```

---

## ✅ That's it!

Now your load test is:
- Recorded from browser
- Run via JMeter
- Exported to a clean HTML report
- Ready to share on GitHub!
