# ScanSync - Document Scanning & Matching System, Assignment for Cathago

## Overview
ScanSync is a self-contained document scanning and matching system with a built-in credit system. Each user has a daily limit of 20 free scans, and additional scans require admin approval.

## Features
### 1. User Management & Authentication
- User Registration & Login (Basic username/password authentication).
- User Roles: Regular Users & Admins.
- Profile Section displaying user credits, past scans, and requests.

### 2. Credit System
- Each user gets **20 free scans per day** (auto-reset at midnight).
- Users must request additional credits if they exceed their limit.
- Admins can approve or deny credit requests.
- Each document scan deducts **1 credit** from the user’s balance.

### 3. Document Scanning & Matching
- Users upload a **plain text file** for scanning.
- System compares it against stored documents using **text similarity algorithms**.
- **Bonus**: AI-based document matching (using OpenAI, Gemini, or DeepSeek).

### 4. Smart Analytics Dashboard
- Track number of scans per user per day.
- Identify most common scanned document topics.
- View top users by scans and credit usage.
- Generate credit usage statistics for admins.

## API Endpoints
| Method | Endpoint | Description |
|--------|---------|-------------|
| POST | `/auth/register` | User registration |
| POST | `/auth/login` | User login (Session-based) |
| GET | `/user/profile` | Get user profile & credits |
| POST | `/scan` | Upload document for scanning (uses 1 credit) |
| GET | `/matches/:docId` | Get matching documents |
| POST | `/credits/request` | Request admin to add credits |
| GET | `/admin/analytics` | Get analytics for admins |

## Tech Stack
- **Frontend**: HTML, CSS, JavaScript (No frameworks)
- **Backend**: Node.js (Express)
- **Database**: SQLite (or JSON files for small-scale storage)
- **File Storage**: Local storage
- **Authentication**: Basic username-password login (hashed passwords)
- **Text Matching Logic**: Levenshtein distance, word frequency, etc.

## Project Structure
```
ScanSync/
├── backend/
│   ├── server.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── scan.js
│   │   ├── credits.js
│   │   ├── analytics.js
│   ├── models/
│   │   ├── User.js
│   │   ├── Scan.js
│   │   ├── CreditRequest.js
│   ├── middleware/
│   │   ├── authMiddleware.js
│   ├── utils/
│   │   ├── textMatching.js
│   ├── db.json
│   ├── package.json
│   ├── .gitignore
│   ├── README.md
├── frontend/
│   ├── index.html
│   ├── dashboard.html
│   ├── styles/
│   │   ├── main.css
│   ├── scripts/
│   │   ├── auth.js
│   │   ├── scan.js
│   │   ├── credits.js
│   │   ├── analytics.js
│   ├── assets/
│   ├── README.md
```

## Setup Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ScanSync.git
   cd ScanSync
   ```
2. Install backend dependencies:
   ```bash
   cd backend
   npm install
   ```
3. Start the backend server:
   ```bash
   node server.js
   ```
4. Open `frontend/index.html` in a browser to access the UI.

## Bonus Features (Optional)
- **Automated Credit Reset**: Auto-reset free credits at midnight.
- **User Activity Logs**: Track when users scan or request credits.
- **Admin Dashboard**: Simple UI for approving credits & viewing analytics.
- **Export Reports**: Download scan history as a text file.

## License
This project is open-source and available under the MIT License.
