# SORSOGON STATE UNIVERSITY
**College of Information and Communications Technology**  
*Bulan Campus, Zone 8, Bulan, Sorsogon*  
**Email Address:** cict@sorsu.edu.ph | **Tel. No.:** 056 311-0103  

---

## CC 101 Laboratory Activity: Exploring the Windows Command Line

| Item | Details |
| :--- | :--- |
| **Course** | CC 101 Introduction to Computing (BSCS 1st Year) |
| **Course Outcome** | CO2: Identify the functions and relationships of major hardware and software components |
| **Output** | Command Line Exploration Documentation (PDF) |
| **Estimated time** | 2 to 2½ hours |
| **Reference** | CC 101 Lecture Notes: Exploring the Windows Command Line |

---

### Instructions
Follow every step in order, take the screenshots marked `[Screenshot]`, and answer the questions marked `[Answer]` in your documentation.

#### Before you start
* You need a Windows 10 or 11 computer. No administrator rights are needed.
* To take a screenshot, press $\text{Windows} + \text{Shift} + \text{S}$, drag over the terminal window, then paste it ($\text{Ctrl} + \text{V}$) into your documentation.
* Replace the sample values (*Juan Dela Cruz, BSCS 1-1*) with your own details.
* Type every command yourself. Do not copy and paste; typing is how you learn.

---

### Part A: Open the Two Shells

1. Press $\text{Windows} + \text{R}$, type `cmd`, and press **Enter**. Type `cls` and press **Enter**.
2. Type `echo Juan Dela Cruz, BSCS 1-1` (your own name and section) and press **Enter**.

```cmd
C:\Users\Administrator>echo Angel Lyra Escandor, BSCS 1-1
Angel Lyra Escandor, BSCS 1-1
```
*Figure A1*

3. Press $\text{Windows} + \text{R}$, type `powershell`, and press **Enter**. Type the same `echo` command, but put the text in quotation marks: `echo "Juan Dela Cruz, BSCS 1-1"`. PowerShell treats the comma as a list separator without them.

```powershell
PS C:\Users\Administrator> echo "Angel Lyra Escandor, BSCS 1-1"
Angel Lyra Escandor, BSCS 1-1
```
*Figure A2*

> **[Answer] A-Q1. Compare the two prompts. What is different, and what does each part of the Command Prompt prompt mean?**  
> The Command Prompt shows the current drive and folder, while PowerShell adds `"PS"` before the path. The `>` symbol means it is ready for a command.

---

### Part B: Inspect Your System (Command Prompt)
*Use the Command Prompt window for Parts B to D.*

1. Run these commands one at a time: `whoami`, then `hostname`, then `ver`.

```cmd
C:\Users\Administrator>whoami
administrator\administrator

C:\Users\Administrator>hostname
ADMINISTRATOR

C:\Users\Administrator>ver
Microsoft Windows [Version 10.0.19045.3745]
```
*Figure B1*

2. Run the command below. It may take 10 to 30 seconds.

```cmd
C:\Users\Administrator>systeminfo | findstr /B/C:"OS Name" /C:"OS Version" /C:"System Type" /C:"Total Physical Memory"
OS Name:                   Microsoft Windows 10 Pro
OS Version:                10.0.19045 N/A Build 19045
System Type:               x64-based PC
Total Physical Memory:     7,973 MB
```
*Figure B2*

3. Run `ipconfig`. Find the adapter that shows an IPv4 Address.

```cmd
C:\Users\Administrator>ipconfig

Windows IP Configuration

Ethernet adapter Ethernet 2:
   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::8124:5981:fc35:64c5%13
   IPv4 Address. . . . . . . . . . . : 192.168.56.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
```
*Figure B3*

> **[Answer] B-Q1. Complete this table in your documentation using your results:**

| Item | Your result |
| :--- | :--- |
| **Logged-in account (`whoami`)** | `administrator\administrator` |
| **Computer name (`hostname`)** | `ADMINISTRATOR` |
| **OS name** | `Microsoft Windows 10 Pro` |
| **OS version** | `10.0.19045 N/A Build 19045` |
| **System type (x64 or ARM)** | `x64-based PC` |
| **Total physical memory (RAM)** | `7,973 MB` |
| **IPv4 address** | `192.168.56.1` |

> **[Answer] B-Q2. The `|` symbol in step 2 is called a pipe. Run `systeminfo` alone and compare. In your own words, what did `| findstr` do?**  
> It sends the output of `systeminfo` to `findstr`. The `findstr` command then searches the output and displays only the lines containing the specified parameters, such as the OS name, OS version, system type, and physical memory.

---

### Part C: Build a Folder Structure

1. Go to your user folder and create the lab folders:
```cmd
cd %USERPROFILE%
mkdir CC101-Lab
cd CC101-Lab
mkdir Notes Projects Screenshots
```

2. Create a text file about yourself (use your own details):
```cmd
echo Name: Angel Lyra Escandor > profile.txt
echo Section: BSCS 1-1 >> profile.txt
echo Favorite app: Tiktok >> profile.txt
type profile.txt
```
*Figure C1*

3. Run `tree /F` to display your folder structure.

```cmd
C:\Users\Administrator\CC101-Lab>tree /F
Folder PATH listing
Volume serial number is 2862-AB55
C:.
│   profile.tx
│   profile.txt
│
├───Notes
├───Projects
└───Screenshots
```
*Figure C2*

4. Open File Explorer, go to `C:\Users\(your account)\CC101-Lab`, and open `profile.txt` in Notepad.  
*Figure C3*

> **[Answer] C-Q1. What would happen if you used `>` instead of `>>` in the second echo line? Test it on a new file (`test.txt`) and explain.**  
> The `>` symbol overwrites the contents of the file. If the file already contains information, using `>` replaces the old content with the new line. In contrast, `>>` appends the new line to the existing contents without deleting them.

---

### Part D: Copy, Rename, and Delete Files

1. Execute the following sequence:
```cmd
copy profile.txt Notes\profile-copy.txt
cd Notes
ren profile-copy.txt about-me.txt
echo This file will be deleted > temp.txt
dir
```
*Figure D1*

```cmd
C:\Users\Administrator\CC101-Lab\Notes>del temp.txt
C:\Users\Administrator\CC101-Lab\Notes>dir
 Volume in drive C has no label.
 Volume Serial Number is 2862-AB55

 Directory of C:\Users\Administrator\CC101-Lab\Notes

09/23/2026  03:07 PM    <DIR>          .
09/23/2026  03:07 PM    <DIR>          ..
09/23/2026  02:56 PM                20 about-me.txt
               1 File(s)             20 bytes
               2 Dir(s)  138,195,173,376 bytes free

C:\Users\Administrator\CC101-Lab\Notes>cd ..
C:\Users\Administrator\CC101-Lab>tree /F
Folder PATH listing
Volume serial number is 2862-AB55
C:.
│   profile.tx
│   profile.txt
│
├───Notes
│       about-me.txt
│
├───Projects
└───Screenshots
```
*Figure D2 (from del to tree /F)*

> **[Answer] D-Q1. After `del temp.txt`, check your Recycle Bin. Is `temp.txt` there? What does this tell you about deleting files from the command line?**  
> No. A file deleted using the `del` command in Command Prompt does not go to the Recycle Bin. It is deleted directly from the system, so it cannot be restored from the Recycle Bin like a file deleted via File Explorer.

---

### Part E: Explore PowerShell

Switch to the PowerShell window.

1. Go to your lab folder and list and read its files:

```powershell
PS C:\Users\Administrator> cd $HOME\CC101-Lab
PS C:\Users\Administrator\CC101-Lab> Get-ChildItem

    Directory: C:\Users\Administrator\CC101-Lab

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        9/23/2026   3:07 PM                Notes
d-----        9/23/2026   2:55 PM                Projects
d-----        9/23/2026   2:55 PM                Screenshots
-a----        9/23/2026   2:57 PM             51 profile.tx
-a----        9/23/2026   2:56 PM             20 profile.txt

PS C:\Users\Administrator\CC101-Lab> Get-Content profile.txt
Section: BSCS 1-1

PS C:\Users\Administrator\CC101-Lab> $PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.19041.5007
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.5007
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```
*Figure E1*

2. Run `Get-Help Get-ChildItem`.  
*Figure E2*

3. Perform base conversions using PowerShell:

```powershell
PS C:\Users\Administrator\CC101-Lab> [Convert]::ToString(347, 2)
1010100101

PS C:\Users\Administrator\CC101-Lab> [Convert]::ToString(347, 8)
1245

PS C:\Users\Administrator\CC101-Lab> '{0:X}' -f 347
15B
```
*Figure E3*

> **[Answer] E-Q1. Write your number in decimal, binary, octal, and hexadecimal. Keep this; you will verify it by hand in Week 5.**  
> * **Decimal:** 347
> * **Binary:** 1010100101
> * **Octal:** 1245
> * **Hexadecimal:** 15B

---

### Part F: Discover a New Command

1. In Command Prompt, type `help` to see a list of commands.
2. Choose one command that was not taught in this lesson and is safe to run (`tasklist`).
3. Read its help with `tasklist /?`, then run it.

*Figure F1 & Figure F2*

> **[Answer] F-Q1. What does your chosen command do, and when would it be useful?**  
> The `tasklist` command displays the programs and processes currently running on the computer. It is useful when checking active applications or troubleshooting a system that is slow or unresponsive.

---

### Part G: Reflection

> **[Answer] G-Q1. Which task in this activity was faster in the CLI than in the GUI? Which was easier in the GUI? Explain why.**  
> Creating multiple nested folders and files was significantly faster in the CLI because it required only a few concise commands. Conversely, viewing and navigating file contents was easier in the GUI because File Explorer provides a visual, interactive layout. The CLI is superior for rapid execution, while the GUI is more intuitive for visual browsing.

> **[Answer] G-Q2. What error did you encounter (if any), what caused it, and how did you fix it?**  
> An initial typo occurred when specifying a filename. The error was caused by missing a character while typing the filename. I identified it by comparing the terminal error message with the laboratory guide, corrected the spelling, and re-ran the command successfully.

> **[Answer] G-Q3. Give one real-world job or situation in computing where knowing the command line would be important.**  
> Command-line proficiency is essential for System Administrators and DevOps Engineers. They rely on it to automate system administration tasks, configure remote servers without graphical interfaces, manage server networks, and execute bulk operations efficiently.

---

### Documentation and Submission Guidelines

#### Required Contents Order
1. **Cover page:** Activity title, full name, student ID, section, date performed, instructor's name.
2. **Introduction (3-5 sentences):** Explanation of CLI and activity goals.
3. **Procedure and results (Parts A to F):** Headings, commands, labeled figures, and `[Answer]` entries.
4. **Commands Learned Table:** Summary of all executed CLI commands.
5. **Reflection:** Answers to G-Q1 through G-Q3.

#### Formatting Rules

| Item | Requirement |
| :--- | :--- |
| **File type** | PDF (export from Word or Google Docs) |
| **File name** | `CC101_CLI-Lab_Lastname_Firstname.pdf` |
| **Font** | Arial or Calibri (11 pt); commands in Consolas or Courier New |
| **Screenshots** | Cropped to terminal window, clear, and labeled below (e.g., *"Figure B2. Filtered systeminfo output"*) |
| **Personal details** | Name, section, and student ID must appear in screenshots |
| **Total screenshots** | 16 total (A1–A2, B1–B3, C1–C3, D1–D2, E1–E3, F1–F2) |

#### Sample Commands Learned Table

| Command | Shell | What it does |
| :--- | :--- | :--- |
| `mkdir Notes` | Command Prompt | Creates a folder named `Notes` in the current working directory. |
| `type profile.txt` | Command Prompt | Displays the text content of `profile.txt` directly in the terminal. |
| `Get-ChildItem` | PowerShell | Lists the items (files and folders) in the current directory. |
| `Get-Content` | PowerShell | Retrieves and displays the contents of a specified file. |

---

### Grading Rubric

| Criterion | Points | Full Marks | Partial Marks | Low Marks |
| :--- | :---: | :--- | :--- | :--- |
| **Completeness of procedure** | 30 | All 16 labeled, readable screenshots; every part A to F documented | 1 to 4 screenshots missing or unreadable | 5 or more screenshots missing |
| **Accuracy of results** | 20 | System-information table complete; commands and conversions correct and personalized | Minor errors or 1 to 2 missing values | Many errors, or results not the student's own |
| **Answers to guide questions (A to F)** | 20 | Correct, clear, in the student's own words | Mostly correct but brief or vague | Missing, incorrect, or copied |
| **Reflection (G-Q1 to G-Q3)** | 15 | Specific, honest, and linked to the activity | General statements with few specifics | Missing or off-topic |
| **Organization and formatting** | 15 | Follows required order, naming, and formatting rules; commands table complete | Some rules not followed | Disorganized; wrong file type or name |
| **Total** | **100** | | | |
