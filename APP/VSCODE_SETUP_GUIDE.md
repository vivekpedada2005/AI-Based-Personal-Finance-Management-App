# FinanceAI - VSCode Setup & Implementation Guide

## One-Time Setup in VSCode

### Step 1: Clone & Install

\`\`\`bash
# Navigate to your projects folder
cd ~/Desktop  # or your preferred location

# Download the project
git clone <your-repo-url> finance-ai
cd finance-ai

# Install dependencies
npm install
\`\`\`

### Step 2: Environment Setup

Create a `.env.local` file in the root directory:

\`\`\`env
# Database (optional - for future Supabase integration)
NEXT_PUBLIC_SUPABASE_URL=your_url_here
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_key_here

# App URL
NEXT_PUBLIC_APP_URL=http://localhost:3000
\`\`\`

### Step 3: Start Development Server

\`\`\`bash
npm run dev
\`\`\`

Visit `http://localhost:3000` in your browser.

---

## Project Structure

\`\`\`
finance-ai/
├── app/
│   ├── page.tsx                 # Landing page
│   ├── layout.tsx               # Root layout
│   ├── globals.css              # Theme & design tokens
│   ├── login/page.tsx           # Login page (with forgot password)
│   ├── signup/page.tsx          # Signup page (with salary input)
│   ├── dashboard/page.tsx       # Main dashboard
│   └── api/
│       └── auth/
│           ├── login/route.ts   # Login API
│           ├── signup/route.ts  # Signup API
│           ├── forgot-password/route.ts  # Password reset API
│           └── transactions/import/route.ts  # Bank transaction import
├── components/
│   ├── dashboard-layout.tsx     # Sidebar navigation
│   ├── salary-overview.tsx      # Salary & savings cards
│   ├── expense-summary.tsx      # KPI summary cards
│   ├── expense-chart.tsx        # Spending by category
│   ├── forecast-chart.tsx       # 6-month expense forecast
│   ├── savings-prediction.tsx   # 3-month savings forecast
│   ├── budget-tips.tsx          # AI savings recommendations
│   ├── recent-transactions.tsx  # Transaction history
│   └── ui/                      # shadcn/ui components
├── lib/
│   ├── forecast-model.ts        # ML forecasting algorithms
│   └── utils.ts                 # Utility functions
└── public/                      # Static assets

\`\`\`

---

## Test Credentials

Login with these demo accounts:

\`\`\`
Email: demo@example.com
Password: password123
Salary: $5,000/month

Email: test@example.com
Password: password123
Salary: $4,500/month
\`\`\`

---

## Key Features Overview

### 1. Authentication System
- **Files:** `app/login/page.tsx`, `app/signup/page.tsx`, `app/api/auth/*`
- **Features:**
  - Email/password login
  - User registration with salary setup
  - Forgot password recovery
  - Session management via localStorage

### 2. Transaction Analysis
- **Files:** `app/api/transactions/import/route.ts`, `lib/forecast-model.ts`
- **Features:**
  - Automatic bank transaction import simulation
  - Smart expense categorization (8 categories)
  - Transaction analysis by category
  - Real transaction display in dashboard

### 3. ML-Based Forecasting
- **File:** `lib/forecast-model.ts`
- **Algorithm:** Exponential smoothing with trend analysis
- **Outputs:**
  - 6-month expense predictions
  - 3-month savings forecasts
  - Savings rate calculations

### 4. Personalized Recommendations
- **Function:** `generateSavingsTips()` in `lib/forecast-model.ts`
- **Features:**
  - Salary-based savings analysis
  - Category-specific spending alerts
  - Smart budget recommendations
  - Goal progress tracking

### 5. Interactive Dashboard
- **Components:** All files in `components/`
- **Features:**
  - Real-time salary overview
  - Category breakdown charts
  - Savings goal progress tracking
  - Transaction history
  - AI-generated tips and alerts

---

## Common Tasks & Commands

### Development

\`\`\`bash
# Start dev server
npm run dev

# Build for production
npm run build

# Run production build
npm run start

# Lint code
npm run lint
\`\`\`

### Adding New Features

#### Add a New Page

1. Create file: `app/new-feature/page.tsx`
2. Wrap in `DashboardLayout` component
3. Add route to sidebar in `components/dashboard-layout.tsx`

#### Add a New Component

1. Create file: `components/my-component.tsx`
2. Use shadcn/ui components
3. Import in dashboard page

#### Modify Transaction Categories

Edit `EXPENSE_CATEGORIES` and `categorizeExpense()` in `lib/forecast-model.ts`

#### Adjust Forecast Algorithm

Modify alpha, beta, gamma parameters in `predictExpenses()` function (higher = more responsive)

---

## VSCode Extensions (Recommended)

Install these extensions for better development experience:

\`\`\`
- ES7+ React/Redux/React-Native snippets
- Tailwind CSS IntelliSense
- Next.js snippets
- Prettier - Code formatter
- Thunder Client (API testing)
- GitLens
\`\`\`

### Quick Extensions Install

\`\`\`bash
# In VSCode terminal
code --install-extension dsznajder.es7-react-js-snippets
code --install-extension bradlc.vscode-tailwindcss
code --install-extension avraammosshe.next-js
code --install-extension esbenp.prettier-vscode
code --install-extension rangav.vscode-thunder-client
code --install-extension eamodio.gitlens
\`\`\`

---

## Debugging Tips

### Debug Console Logs

Add to any component/API route:

\`\`\`typescript
console.log("[DEBUG] Message here", variableName)
\`\`\`

Open DevTools (F12) to see console logs.

### Check Authentication Status

In browser console:

\`\`\`javascript
// Check if logged in
localStorage.getItem("user")
localStorage.getItem("token")

// Clear session (logout)
localStorage.clear()
\`\`\`

### Test API Routes

Use Thunder Client extension or curl:

\`\`\`bash
# Test login
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"demo@example.com","password":"password123"}'

# Test transactions import
curl http://localhost:3000/api/transactions/import
\`\`\`

---

## Customization Guide

### Change Theme Colors

Edit `app/globals.css`:

\`\`\`css
:root {
  --primary: oklch(0.485 0.15 200);  /* Teal */
  --accent: oklch(0.6 0.18 142);      /* Green */
  --destructive: oklch(0.577 0.245 27.325);  /* Red */
}
\`\`\`

### Modify Default Salary

Edit `app/api/auth/login/route.ts`:

\`\`\`typescript
salary: 5000  // Change this value
\`\`\`

### Adjust Forecast Sensitivity

Edit `lib/forecast-model.ts`:

\`\`\`typescript
const alpha = 0.3  // 0.1-0.9 (higher = more responsive)
const beta = 0.1   // Trend sensitivity
const gamma = 0.1  // Seasonal sensitivity
\`\`\`

### Change Budget Multiplier

In `components/expense-chart.tsx`:

\`\`\`typescript
budget: Math.round((categoryTotals.get(category) || 0) * 1.2)  // 1.2 = 20% buffer
\`\`\`

---

## Deployment

### Deploy to Vercel (Recommended)

\`\`\`bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Follow prompts to connect your GitHub repo
\`\`\`

### Environment Variables on Vercel

1. Go to vercel.com dashboard
2. Select your project
3. Settings > Environment Variables
4. Add all variables from `.env.local`

---

## Future Enhancements

- [ ] Real Plaid bank integration
- [ ] Supabase authentication
- [ ] PostgreSQL database
- [ ] Notifications & bill reminders
- [ ] Mobile app (React Native)
- [ ] Export transactions to CSV/PDF
- [ ] Budget optimization AI
- [ ] Multi-user family accounts
- [ ] Investment portfolio tracking
- [ ] Credit score monitoring

---

## Troubleshooting

### Port 3000 Already in Use

\`\`\`bash
# Find process on port 3000
lsof -i :3000

# Kill it
kill -9 <PID>

# Or use different port
npm run dev -- -p 3001
\`\`\`

### Module Not Found Errors

\`\`\`bash
# Clear node_modules and reinstall
rm -rf node_modules pnpm-lock.yaml
npm install
\`\`\`

### Login Not Working

\`\`\`bash
# Clear browser storage
localStorage.clear()
sessionStorage.clear()

# Reload and try again
\`\`\`

### Changes Not Reflecting

\`\`\`bash
# Stop dev server (Ctrl+C)
# Hard refresh browser (Ctrl+Shift+R)
# Restart dev server
npm run dev
\`\`\`

---

## Performance Optimizations

### Already Implemented

- Server components for non-interactive sections
- Client components only where needed
- Image optimization with Next.js Image
- CSS-in-JS with Tailwind
- Lightweight ML model (no TensorFlow/PyTorch)
- Efficient data fetching with SWR

### Recommended Additions

\`\`\`bash
# Add image optimization
npm install next-image-export-optimizer

# Add caching
npm install swr

# Add analytics
npm install @vercel/analytics
\`\`\`

---

## Support & Resources

- **Next.js Docs:** https://nextjs.org/docs
- **Tailwind CSS:** https://tailwindcss.com/docs
- **shadcn/ui:** https://ui.shadcn.com
- **Recharts:** https://recharts.org

---

**Happy coding!** 🚀
