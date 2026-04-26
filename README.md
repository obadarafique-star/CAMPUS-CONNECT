
## Run Locally

**Prerequisites:**  Node.js


1. Install dependencies:
   `npm install`
2. Set the `GEMINI_API_KEY` in [.env.local](.env.local) to your Gemini API key
3. Run the app:
   `npm run dev`
1. What is CampusConnect?
CampusConnect is a campus ambassador management platform that connects university program managers with student ambassadors. It uses AI-powered task validation to automate the review process of ambassador submissions.
Key Features:
•	🔐 Google OAuth Authentication - Secure login via Firebase Auth
•	👥 Dual Role System - Ambassador & Manager dashboards
•	🤖 AI-Powered Validation - Gemini AI scores submissions automatically
•	📊 Real-time Analytics - Leaderboards, points, and badges
•	🎯 Task Management - Create, assign, and track ambassador tasks
________________________________________
2. User Roles
🎓 Ambassador
•	View available tasks from programs they're enrolled in
•	Submit task completions with text proof
•	Earn points and climb the leaderboard
•	Earn badges for achievements
🏢 Program Manager
•	Create new ambassador programs
•	Create tasks (referrals, promotions, content, etc.)
•	Invite ambassadors to their programs
•	Review submissions and approve/reject
•	View analytics and cohort performance
________________________________________
3. Technical Architecture
Frontend
•	React 19 - Modern UI framework
•	Vite 6 - Fast build tool
•	Tailwind CSS 4 - Styling
•	Motion - Animations
•	Lucide React - Icons
Backend Services
•	Firebase Auth - Google OAuth
•	Firebase Firestore - Real-time database
•	Google Gemini AI - Submission validation
Key Files:
File	Purpose
App.tsx
Main app with auth flow
firebase.ts
Firebase configuration
aiService.ts
Gemini AI integration
AmbassadorDashboard.tsx
Ambassador UI
ManagerDashboard.tsx
Manager UI
________________________________________
4. How the AI Validation Works
When an ambassador submits a task:
1.	Submission Sent → Text proof and optional image URL
2.	AI Analysis → Gemini AI evaluates against task requirements
3.	Scoring → Returns 0-100 score with reasoning
4.	Storage → Submission saved with AI score in Firestore
•	
•	
•	
•	
________________________________________
5. Database Schema (Firestore)
•	
•	
•	
•	
________________________________________
6. Running the Project Locally
Prerequisites:
•	Node.js installed
•	Google Cloud account (for Firebase)
Steps:
•	
•	
•	
•	
The app runs on http://localhost:3000/
________________________________________



