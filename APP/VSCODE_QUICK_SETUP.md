# VSCode Quick Setup - One Time Compilation

## Prerequisites
- Node.js 18+ installed
- VSCode installed
- Git (optional)

## One-Time Setup (Copy & Paste Commands)

### Step 1: Clone or Open Project
\`\`\`bash
# If you have a GitHub repo
git clone <your-repo-url> finance-ai
cd finance-ai

# OR if you downloaded ZIP
cd finance-ai
\`\`\`

### Step 2: Install Dependencies
\`\`\`bash
npm install
\`\`\`

### Step 3: Start Development Server
\`\`\`bash
npm run dev
\`\`\`

Output will show:
\`\`\`
> next dev

  ▲ Next.js 16.x.x
  - Local:        http://localhost:3000
  - Environments: .env.local
\`\`\`

### Step 4: Open in Browser
Navigate to: `http://localhost:3000`

## VSCode Extensions (Recommended)

Install these for better development experience:

1. **ES7+ React/Redux/React-Native snippets**
   - ID: `dsznajder.es7-react-js-snippets`

2. **Prettier - Code formatter**
   - ID: `esbenp.prettier-vscode`

3. **ESLint**
   - ID: `dbaeumer.vscode-eslint`

4. **Tailwind CSS IntelliSense**
   - ID: `bradlc.vscode-tailwindcss`

5. **Thunder Client** (API testing)
   - ID: `rangav.vscode-thunder-client`

### Quick Install:
\`\`\`bash
# Open VSCode extensions and search for extension IDs above
# Or use command line:
code --install-extension dsznajder.es7-react-js-snippets
code --install-extension esbenp.prettier-vscode
code --install-extension dbaeumer.vscode-eslint
code --install-extension bradlc.vscode-tailwindcss
code --install-extension rangav.vscode-thunder-client
\`\`\`

## Useful VSCode Shortcuts

| Action | Shortcut |
|--------|----------|
| Open File | `Ctrl+P` |
| Find Text | `Ctrl+F` |
| Find & Replace | `Ctrl+H` |
| Format Document | `Shift+Alt+F` |
| Open Terminal | `Ctrl+\`` |
| Go to Line | `Ctrl+G` |
| Toggle Sidebar | `Ctrl+B` |
| Command Palette | `Ctrl+Shift+P` |

## Development Workflow

### 1. Add New Transaction Component
\`\`\`bash
# Edit: components/add-transaction.tsx
# Then refresh browser at http://localhost:3000/dashboard
\`\`\`

### 2. Modify Dashboard
\`\`\`bash
# Edit: app/dashboard/page.tsx
# Changes auto-reload in browser (Hot Reload)
\`\`\`

### 3. Add New Expense Category
\`\`\`bash
# Edit: lib/forecast-model.ts
# Update EXPENSE_CATEGORIES array
# Then add keyword matching in categorizeExpense()
\`\`\`

### 4. Change Styling
\`\`\`bash
# Edit: app/globals.css (global styles)
# Edit: component files for component-specific styles
# Tailwind classes apply immediately
\`\`\`

## Common Development Tasks

### Test New Transaction
1. Go to http://localhost:3000/dashboard
2. Click "Add Transaction"
3. Fill in details (Amount must be in rupees)
4. Watch charts update in real-time

### Clear All Data
\`\`\`bash
# In browser console (F12):
localStorage.clear()
location.reload()
\`\`\`

### View Stored Transactions
\`\`\`bash
# In browser console (F12):
JSON.parse(localStorage.getItem("transactions"))
\`\`\`

### View Stored User Data
\`\`\`bash
# In browser console (F12):
JSON.parse(localStorage.getItem("user"))
\`\`\`

## Debugging

### Enable Debug Logging
Add console.log in components:
\`\`\`typescript
console.log("[v0] User transactions:", transactions)
console.log("[v0] Total expenses:", totalExpenses)
\`\`\`

### Check Network Requests
1. Open DevTools (F12)
2. Go to Network tab
3. Perform action (add transaction)
4. View request/response

### React DevTools
Install from Chrome Web Store for better React debugging

## Build for Production

\`\`\`bash
# Create optimized build
npm run build

# Start production server
npm start
\`\`\`

## Deployment Commands

### Deploy to Vercel
\`\`\`bash
npm i -g vercel
vercel

# For updates:
vercel --prod
\`\`\`

### Deploy to GitHub Pages
\`\`\`bash
npm run export
# Push dist folder to gh-pages branch
\`\`\`

## Troubleshooting Commands

\`\`\`bash
# Clear node_modules and reinstall
rm -rf node_modules
npm install

# Clear Next.js cache
rm -rf .next
npm run dev

# Check for build errors
npm run build

# Lint code
npm run lint

# Format code
npm run format
\`\`\`

## Environment Variables (If Needed)

Create `.env.local`:
\`\`\`
NEXT_PUBLIC_API_URL=http://localhost:3000
\`\`\`

Then restart dev server:
\`\`\`bash
# Stop: Ctrl+C
# Start: npm run dev
\`\`\`

## Next Steps

1. **Customize Categories**: Edit `lib/forecast-model.ts`
2. **Add More Features**: Create new components in `components/`
3. **Style Changes**: Update `app/globals.css` or use Tailwind classes
4. **Database**: Replace localStorage with Supabase
5. **Deployment**: Push to Vercel or your hosting provider

## Getting Help

- VSCode Issues: Check Extensions
- Component Issues: Check browser console (F12)
- Data Issues: Check localStorage (see debugging commands above)
- Next.js Docs: https://nextjs.org/docs
- Tailwind Docs: https://tailwindcss.com/docs
