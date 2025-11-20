
# Bank-System-V1

🏦 Bank Management System (C++)

A simple console-based bank management system written in C++.
This project manages clients, their accounts, balances, and financial transactions using text-file storage instead of a database.

It includes a full menu-based UI, CRUD operations, and deposit/withdraw functionality.

📌 Features
✅ Client Management

Add new clients

Update existing client info

Delete clients

Find clients by account number

List all clients with formatted output

💰 Transactions

Deposit money

Withdraw money (with balance validation)

Display total balances of all clients

📂 File Handling

All data is stored in a text file: Clients.txt

Records are saved using the format:

AccountNumber#//#PinCode#//#Name#//#Phone#//#Balance

🧩 Input Validation and Utilities

String splitting and parsing

Conversion between text lines and client objects

Marking clients for deletion

Console UI with structured menus

📑 Project Structure
📁 Project  
 ├── main.cpp                → Main application logic  
 ├── Clients.txt             → Persistent storage  
 ├── (other .h or .cpp files if separated)

🔧 How It Works
1. Loading Data

Clients are loaded from Clients.txt using:

vector<sClient> LoadCleintsDataFromFile(string FileName);

2. Saving Data

Records are rewritten (overwritten) when updates or deletions occur:

vector<sClient> SaveCleintsDataToFile(string FileName, vector<sClient> vClients);

3. Parsing Data

Lines are converted to client records using:

sClient ConvertLinetoRecord(string Line);

4. User Interface

The app shows two menus:

🏠 Main Menu
1 - Show Client List
2 - Add New Client
3 - Delete Client
4 - Update Client Info
5 - Find Client
6 - Transactions
7 - Exit

💳 Transactions Menu
1 - Deposit
2 - Withdraw
3 - Total Balances
4 - Main Menu

📘 Code Overview
Client Structure
struct sClient {
    string AccountNumber;
    string PinCode;
    string Name;
    string Phone;
    double AccountBalance;
    bool MarkForDelete = false;
};

Example of Converting Client → String
string ConvertRecordToLine(sClient Client) {
    return Client.AccountNumber + "#//#" +
           Client.PinCode + "#//#" +
           Client.Name + "#//#" +
           Client.Phone + "#//#" +
           to_string(Client.AccountBalance);
}

🧮 Transactions
Deposit
DepositBalanceToClientByAccountNumber(AccountNumber, Amount, vClients);


Updates the client balance and rewrites the file.

Withdraw

Includes balance validation:

while (Amount > Client.AccountBalance) {
    cout << "Amount Exceeds the balance...";
}

📊 Client List Example
| Account Number | Pin Code | Client Name                   | Phone       | Balance     |
-----------------------------------------------------------------------------------------
| 12345          | 7788     | John Doe                      | 0655998877  | 15000
| 98765          | 4455     | Alice Smith                   | 0661223344  | 3500

🚀 How to Run
1. Compile

Use any C++ compiler:

g++ main.cpp -o BankSystem

2. Run
./BankSystem

⚠️ Notes

The system uses a plain text file — no database required.

system("cls") and system("pause>0") are Windows-only.
If you're on Linux or macOS, replace them with:

system("clear")

cin.get()

📌 Possible Improvements (Future Work)

Encryption for sensitive data like PinCode

Convert to OOP with classes and modules

Store data in JSON / binary / SQLite

Add login system for admin/users

Add UI colors (ANSI)

Error handling for corrupted files

🧑‍💻 Author

Charaf Eddine Jador
C++ Developer & Programmer
