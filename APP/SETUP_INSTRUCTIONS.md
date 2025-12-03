# FinanceAI - Setup Instructions

## Quick Start Guide

### Prerequisites
- Node.js 18+ 
- npm or yarn
- A code editor (VSCode recommended)

### Installation Steps

#### 1. Clone or Download the Project
\`\`\`bash
# If using git
git clone <repository-url>
cd finance-ai

# Or download and extract the ZIP file
cd finance-ai-main
\`\`\`

#### 2. Install Dependencies
\`\`\`bash
npm install
# or
yarn install
\`\`\`

#### 3. Start Development Server
\`\`\`bash
npm run dev
# or
yarn dev
\`\`\`

The app will be available at: `http://localhost:3000`

#### 4. Test Credentials
Use these demo credentials to test:
- Email: `demo@example.com`
- Password: `password123`

Or create a new account during signup.

---

## Project Structure

\`\`\`
finance-ai/
├── app/
│   ├── layout.tsx           # Main layout with metadata
│   ├── globals.css          # Global styles & design tokens
│   ├── page.tsx             # Landing page
│   ├── login/
│   │   └── page.tsx         # Login page
│   ├── signup/
│   │   └── page.tsx         # Signup page
│   ├── dashboard/
│   │   └── page.tsx         # Main dashboard
│   └── api/
│       └── auth/            # Authentication endpoints
│           ├── login/route.ts
│           └── signup/route.ts
├── components/
│   ├── ui/                  # shadcn UI components
│   ├── dashboard-layout.tsx # Dashboard wrapper
│   ├── expense-summary.tsx  # Summary cards
│   ├── expense-chart.tsx    # Spending chart
│   ├── forecast-chart.tsx   # ML forecast chart
│   ├── budget-tips.tsx      # AI tips & alerts
│   └── recent-transactions.tsx
├── lib/
│   └── forecast-model.ts    # Lightweight ML model
├── public/                  # Static assets
└── package.json
\`\`\`

---

## Features Overview

### 1. Authentication
- Sign up and login with email/password
- Secure token-based authentication
- Protected dashboard routes

### 2. Dashboard
- Real-time expense summary (4 key metrics)
- Spending by category chart
- AI-powered forecast predictions
- Recent transactions feed
- Personalized budget tips

### 3. Expense Categorization
- Automatic categorization of transactions
- 8 predefined categories
- Smart categorization based on keywords

### 4. ML Forecasting
- Exponential smoothing algorithm
- Predicts next 2 months of expenses
- Compares actual vs predicted spending

### 5. Budget Tips Engine
- AI-generated budget recommendations
- Category analysis
- Alerts for budget overruns
- Personalized savings suggestions

---

## Key Files & Their Functions

### Authentication Flow
- `app/api/auth/signup/route.ts` - User registration
- `app/api/auth/login/route.ts` - User login
- `app/login/page.tsx` - Login UI
- `app/signup/page.tsx` - Signup UI

### Dashboard Components
- `components/dashboard-layout.tsx` - Sidebar navigation
- `components/expense-summary.tsx` - KPI cards
- `components/expense-chart.tsx` - Bar chart visualization
- `components/forecast-chart.tsx` - ML prediction chart

### ML & Logic
- `lib/forecast-model.ts` - All ML algorithms

---

## Development Commands

\`\`\`bash
# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Run linting
npm run lint
\`\`\`

---

## Customization Guide

### 1. Change App Colors
Edit `app/globals.css`:
\`\`\`css
--primary: oklch(0.485 0.15 200);      /* Main brand color */
--accent: oklch(0.6 0.18 142);         /* Accent color */
--destructive: oklch(0.577 0.245 27);  /* Error color */
\`\`\`

### 2. Update App Name
- Search & replace "FinanceAI" with your app name
- Update metadata in `app/layout.tsx`

### 3. Add More Categories
Edit `lib/forecast-model.ts`:
\`\`\`typescript
export const EXPENSE_CATEGORIES = [
  'Food & Dining',
  'Transport',
  // Add more...
]
\`\`\`

### 4. Adjust ML Forecasting
Edit `lib/forecast-model.ts`:
\`\`\`typescript
const alpha = 0.3    // Increase = more weight on recent data
const beta = 0.1     // Trend smoothing factor
const gamma = 0.1    // Seasonal adjustment
\`\`\`

---

## Environment Variables

Currently using mock authentication. To add production features:

\`\`\`
NEXT_PUBLIC_SUPABASE_URL=your-supabase-url
NEXT_PUBLIC_SUPABASE_KEY=your-supabase-key
\`\`\`

---

## Common Issues & Solutions

### Issue: "Port 3000 already in use"
\`\`\`bash
# Use a different port
npm run dev -- -p 3001
\`\`\`

### Issue: Modules not found
\`\`\`bash
# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
\`\`\`

### Issue: Styling not loading
\`\`\`bash
# Clear Next.js cache
rm -rf .next
npm run dev
\`\`\`

---

## Next Steps

1. **Add Supabase Integration** - Replace mock auth with real database
2. **Bank API Integration** - Connect to Plaid or similar
3. **Push Notifications** - Add bill reminders
4. **Export Features** - Allow CSV/PDF download
5. **Mobile App** - Convert to React Native

---

## Support & Resources

- [Next.js Docs](https://nextjs.org/docs)
- [shadcn/ui Components](https://ui.shadcn.com)
- [Tailwind CSS](https://tailwindcss.com)
- [Recharts Documentation](https://recharts.org)

---

## License

MIT License - Feel free to use and modify for your projects
