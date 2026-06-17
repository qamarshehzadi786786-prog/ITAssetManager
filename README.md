# IT Asset Manager



A Windows desktop application built with **C# (.NET 10)** and **Windows Forms** for managing IT assets, employees, and assignments within an organization.



---



## 📋 Table of Contents



- [About the Project](#about-the-project)

- [Features](#features)

- [Tech Stack](#tech-stack)

- [Project Structure](#project-structure)

- [Getting Started](#getting-started)

- [Database Setup](#database-setup)

- [Usage](#usage)

- [Team Members](#team-members)



---



## About the Project



IT Asset Manager is a semester project that provides a centralized system for tracking IT hardware assets (laptops, monitors, peripherals, etc.), managing employee records, and recording asset assignments. It includes a real-time dashboard that summarizes the current state of all assets.



---



## Features



- **Dashboard** — Live summary of total assets, available assets, assigned assets, assets under repair, total employees, and active assignments.

- **Asset Management** — Add, edit, view, and delete IT assets with details such as brand, model, serial number, purchase date, category, status, and notes.

- **Employee Management** — Maintain employee records including name, department, contact number, email, and active status.

- **Assignment Tracking** — Assign assets to employees and track all active assignments.

- **Category Management** — Organize assets into categories for easier filtering and reporting.



---



## Tech Stack



| Layer | Technology |

|---|---|

| Language | C# |

| Framework | .NET 10 |

| UI | Windows Forms (WinForms) |

| Database | SQL Server (via ADO.NET) |

| IDE | Visual Studio |



---



## Project Structure



```

ITAssetManager/

├── App.Core/                  

│   ├── Models/                

│   ├── Interfaces/            

│   └── Services/              

│

└── App.WindowsApp/            

    ├── Forms/                 

    │   ├── MainForm            

    │   ├── DashboardView       

    │   ├── AssetForm           

    │   ├── EmployeeForm        

    │   ├── AssignmentForm      

    │   └── CategoryForm        

    └── Program.cs             

```

---



## Getting Started



### Prerequisites



- [Visual Studio 2022](https://visualstudio.microsoft.com/) with the **.NET Desktop Development** workload

- [.NET 9 SDK](https://dotnet.microsoft.com/en-us/download)

- SQL Server (Express or higher) or SQL Server LocalDB



### Installation



1. Clone the repository:

git clone https://github.com/qamarshehzadi786786-prog/ITAssetManager 



2. Open the solution in Visual Studio:

ITAssetManager/ITAssetManager.slnx



3. Restore NuGet packages (automatic on build).



4. Set up the database — see Database Setup below.



5. Update the connection string in App.WindowsApp/App.config



6. Build and run the project (F5).



---



## Database Setup



CREATE DATABASE ITAssetManager;

GO



USE ITAssetManager;

GO



CREATE TABLE Categories (

    CategoryID INT PRIMARY KEY IDENTITY,

    CategoryName NVARCHAR(100) NOT NULL

);



CREATE TABLE Assets (

    AssetID INT PRIMARY KEY IDENTITY,

    AssetName NVARCHAR(150) NOT NULL,

    CategoryID INT REFERENCES Categories(CategoryID),

    Brand NVARCHAR(100),

    Model NVARCHAR(100),

    SerialNumber NVARCHAR(100),

    PurchaseDate DATE,

    Status NVARCHAR(50) DEFAULT 'Available',

    Notes NVARCHAR(500)

);



CREATE TABLE Employees (

    EmployeeID INT PRIMARY KEY IDENTITY,

    FullName NVARCHAR(150) NOT NULL,

    Department NVARCHAR(100),

    ContactNumber NVARCHAR(20),

    Email NVARCHAR(150),

    IsActive BIT DEFAULT 1

);



CREATE TABLE Assignments (

    AssignmentID INT PRIMARY KEY IDENTITY,

    AssetID INT REFERENCES Assets(AssetID),

    EmployeeID INT REFERENCES Employees(EmployeeID),

    AssignedDate DATE,

    ReturnDate DATE,

    Notes NVARCHAR(500)

);



---



## Usage



1. Launch the application.

2. Dashboard loads automatically with live count of assets and assignments.

3. Use navigation menu to switch between Assets, Employees, Assignments, and Categories.

4. Use Add / Edit / Delete buttons to manage records.



---



## Team Members



| Name | Roll Number | Role |

|---|---|---|

| Qamar Shehzadi | F23BDOCS1M01193 | Group Member |

| Nosheen Bibi  | F23BDOCS1M01200 | Group Leader |

| Zohaib Hassan | F23BDOCS1M01156 | Group Member |





---



## License



This project was developed as part of a university semester project.

Advanced Programming (CS-1036) | Spring 2026
