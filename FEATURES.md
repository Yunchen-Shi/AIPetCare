# Pet Feeding Planner - Features & Updates

## Version 2.0 - Multi-Language & Feedback System

### New Features Added:

#### 1. **Multi-Language Support (English & Chinese)**
- Language switcher in the top navigation bar
- All UI text, buttons, and messages translated to English and Chinese
- Language preference persists in localStorage
- Covers all pages, components, and dialog boxes

#### 2. **Disabled Authentication**
- Login/Signup functionality has been disabled
- Application uses a demo user system that creates a persistent user ID in localStorage
- No authentication required to use the application
- All user data is stored locally with unique user IDs

#### 3. **Dedicated Settings Page**
- Separate full-page settings interface (accessible from navigation)
- User profile management with full name
- Preferences section including:
  - Theme selection (Light/Dark)
  - Unit preferences (Metric/Imperial)
  - Notification toggle
  - Language selection
- All settings are saved to the database

#### 4. **User Feedback System**
- **Feedback Submission Page**: 
  - Category selection (Bug Report, Feature Request, General Feedback, Other)
  - Feedback description (up to 1000 characters)
  - Optional email for follow-up
  - Automatically saved to database
  
- **Admin Feedback Viewer**:
  - View all submitted feedback in a table format
  - Sort by date, category, and message
  - Export feedback data as CSV file
  - Accessible via navigation (admin access)

#### 5. **Home/Landing Page with Disclaimer**
- Welcome page with app introduction
- **Prominent Disclaimer Section** with:
  - "Alpha Version" notice
  - "Created by students at XJTLU" attribution
  - "This is not a commercial application" disclaimer
  - Expandable details section with full description
- Quick stats showing pets count, features, and languages
- Call-to-action buttons for main features
- Feature highlights section

#### 6. **Improved Navigation**
- Top navigation bar with:
  - App logo and title
  - Language switcher (English/中文)
  - Navigation buttons: Home, Pets, Feedback, Settings
  - Active page highlighting

### Database Schema Updates:

#### New Table: `feedback`
- `id` (uuid, primary key)
- `category` (text) - bug, feature, general, other
- `description` (text) - feedback content up to 1000 chars
- `email` (text, nullable) - optional contact email
- `created_at` (timestamptz) - submission timestamp
- Public insert access (no auth required)

### File Structure:

**New Components:**
- `src/pages/HomePage.tsx` - Landing page with disclaimer
- `src/pages/SettingsPage.tsx` - Dedicated settings page
- `src/pages/FeedbackPage.tsx` - User feedback submission
- `src/pages/AdminFeedbackPage.tsx` - Admin feedback viewer
- `src/context/LanguageContext.tsx` - Language provider and hook
- `src/lib/i18n.ts` - Translations for English and Chinese

**Updated Components:**
- `src/App.tsx` - Main app with page routing and navigation
- `src/lib/types.ts` - Added Feedback types and UserPreferences

### How to Use:

#### Language Switching:
1. Click the language selector in the top navigation
2. Choose English or 中文
3. The entire interface updates instantly
4. Choice is saved for next visit

#### Settings:
1. Click "Settings" in the top navigation
2. Update full name, theme, units, and notifications
3. Click "Save Settings"

#### Submitting Feedback:
1. Click "Feedback" in the top navigation
2. Select feedback category
3. Enter your feedback (max 1000 characters)
4. Optionally provide your email
5. Click "Submit"
6. Success message confirms submission

#### Viewing Feedback (Admin):
1. Access the admin page (can be accessed directly via URL or navigation)
2. View all submitted feedback in table format
3. Click "Export CSV" to download feedback data

### Technical Details:

- **Demo User System**: 
  - Each user gets a unique ID stored in localStorage
  - All pets and data are associated with this ID
  - Persists across browser sessions

- **RLS Policies**: 
  - Feedback table allows public insert/select for anonymous submissions
  - User data remains private to their own user ID

- **Translations**: 
  - 180+ translation keys
  - Comprehensive coverage of all UI elements
  - Easy to extend with additional languages

### Access Instructions:

**Home Page**: Navigate to app or click "Home" button
**Pets Page**: Click "Pets" button - manage your pets and generate feeding plans
**Feedback**: Click "Feedback" button - submit feedback about the application
**Settings**: Click "Settings" button - manage your preferences
**Admin**: Direct navigation or internal link to feedback admin viewer

---

**Note**: This is an Alpha version created by students at Xi'an Jiaotong-Liverpool University (XJTLU). This is not a commercial application.
