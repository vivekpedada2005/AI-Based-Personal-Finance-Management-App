# VSCode Setup & Commands

## Installation

### 1. Install VSCode
- Download from [code.visualstudio.com](https://code.visualstudio.com)
- Install Node.js 18+

### 2. Recommended Extensions

Open VSCode and install these extensions:

1. **ES7+ React/Redux/React-Native snippets**
   - Command: `ext install dsznajder.es7-react-js-snippets`

2. **Tailwind CSS IntelliSense**
   - Command: `ext install bradlc.vscode-tailwindcss`

3. **Prettier - Code formatter**
   - Command: `ext install esbenp.prettier-vscode`

4. **TypeScript Vue Plugin**
   - Command: `ext install Vue.volar`

5. **ESLint**
   - Command: `ext install dbaeumer.vscode-eslint`

6. **Postman**
   - Command: `ext install Postman.postman-code-snippets`

### 3. VSCode Settings

Create `.vscode/settings.json`:

\`\`\`json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "files.exclude": {
    "**/.next": true,
    "**/node_modules": true
  },
  "search.exclude": {
    ".next": true,
    "node_modules": true
  }
}
\`\`\`

---

## Essential VSCode Commands

### Terminal Commands

\`\`\`bash
# Open integrated terminal
Ctrl + ` (backtick)

# Start dev server
npm run dev

# Build project
npm run build

# Open in browser
Ctrl + Shift + P, type: "Open in Default Browser"
\`\`\`

### Editor Shortcuts

\`\`\`bash
# Format document
Shift + Alt + F

# Go to file
Ctrl + P

# Find and replace
Ctrl + H

# Toggle sidebar
Ctrl + B

# Open terminal
Ctrl + `

# Create new file
Ctrl + N

# Save file
Ctrl + S

# Go to line
Ctrl + G

# Comment line
Ctrl + /
\`\`\`

### Debug Commands

\`\`\`bash
# Open debug console
Ctrl + Shift + Y

# Add breakpoint
F9

# Start debugging
F5

# Step over
F10

# Step into
F11
\`\`\`

---

## File Organization in VSCode

### Project Explorer Structure

\`\`\`
finance-ai/
├── .vscode/
│   └── settings.json          ← VSCode configuration
├── app/
│   ├── api/                   ← API routes
│   ├── dashboard/
│   ├── login/
│   ├── signup/
│   ├── layout.tsx
│   ├── page.tsx
│   └── globals.css
├── components/
│   ├── ui/                    ← shadcn components
│   └── custom/                ← Your components
├── lib/
│   └── forecast-model.ts      ← ML utilities
├── public/                    ← Static assets
├── .gitignore
├── package.json
├── tsconfig.json
└── next.config.mjs
\`\`\`

---

## Workflow Tips

### Quick Editing Pattern

1. **Edit Component**
   \`\`\`bash
   # Press Ctrl+P to open file search
   # Type "expense-summary" to find component
   # Edit and save (Ctrl+S)
   # Preview updates in browser (auto-refresh)
   \`\`\`

2. **Add New Page**
   \`\`\`bash
   # Create new file: Ctrl+N
   # Save to: app/new-page/page.tsx
   # Edit content and check localhost:3000/new-page
   \`\`\`

3. **Update Styles**
   \`\`\`bash
   # Open globals.css
   # Edit color tokens
   # Changes apply globally (auto-refresh)
   \`\`\`

### Fast Navigation

\`\`\`bash
# Search all components
Ctrl + Shift + F

# Search symbol in file
Ctrl + Shift + O

# Go to specific line
Ctrl + G

# Jump to error
Ctrl + Shift + M
\`\`\`

---

## Common Workflows

### Workflow 1: Add a New Dashboard Component

\`\`\`bash
# 1. Create component file
components/my-component.tsx

# 2. Write component
export function MyComponent() {
  return <div>...</div>
}

# 3. Import in dashboard
import { MyComponent } from '@/components/my-component'

# 4. Add to dashboard page
<MyComponent />

# 5. Format with Prettier
Shift + Alt + F
\`\`\`

### Workflow 2: Debug a Component

\`\`\`bash
# 1. Add console.log to component
console.log("[v0] Debug:", variable)

# 2. Open browser dev tools
F12

# 3. Check Console tab for logs

# 4. Remove logs when done
\`\`\`

### Workflow 3: Style Updates

\`\`\`bash
# 1. Open globals.css
Ctrl + P → type "globals"

# 2. Update color token
--primary: oklch(0.485 0.15 200);

# 3. Save
Ctrl + S

# 4. Browser auto-refreshes
\`\`\`

---

## Performance Tips

### 1. Use Fast Refresh
- Edit saves automatically trigger component re-render
- State is preserved across edits

### 2. Open Only Needed Files
- Use Ctrl+P for quick file search
- Don't keep 10+ tabs open

### 3. Monitor Build Speed
- Watch npm run dev output
- Should compile in <3 seconds for changes

### 4. Check Console for Errors
- F12 opens DevTools
- Check Console tab for warnings

---

## Debugging Guide

### Enable Chrome DevTools

\`\`\`bash
# Press F12 to open DevTools
# Tabs to know:
# - Elements: Inspect HTML/CSS
# - Console: View logs and errors
# - Network: Monitor API calls
# - Application: View localStorage/cookies
\`\`\`

### Common Debugging Checks

\`\`\`typescript
// 1. Check if user is logged in
console.log("[v0] User:", localStorage.getItem('user'))

// 2. Monitor API responses
console.log("[v0] API Response:", data)

// 3. Check component props
console.log("[v0] Props:", props)

// 4. Verify state changes
console.log("[v0] State:", state)
\`\`\`

---

## Production Ready Checklist

Before deploying:

\`\`\`bash
# 1. Run build
npm run build

# 2. Check for errors
npm run lint

# 3. Test auth flow
# - Sign up
# - Login
# - Navigate dashboard
# - Logout

# 4. Test responsive design
# - F12 → Device toolbar
# - Test mobile/tablet/desktop

# 5. Check performance
# - DevTools Lighthouse
\`\`\`

---

## Deploy to Vercel

\`\`\`bash
# 1. Install Vercel CLI
npm i -g vercel

# 2. Login to Vercel
vercel login

# 3. Deploy
vercel

# 4. Follow prompts and your app is live!
\`\`\`

---

## Keyboard Shortcut Cheatsheet

| Action | Shortcut |
|--------|----------|
| Open Command Palette | Ctrl + Shift + P |
| Quick File Open | Ctrl + P |
| Find | Ctrl + F |
| Find & Replace | Ctrl + H |
| Format Document | Shift + Alt + F |
| Toggle Comment | Ctrl + / |
| Go to Line | Ctrl + G |
| Show Terminal | Ctrl + ` |
| Split Editor | Ctrl + \ |
| Focus Terminal | Ctrl + J |
| Debug Console | Ctrl + Shift + Y |
| Source Control | Ctrl + Shift + G |
| Extensions | Ctrl + Shift + X |

---

## Next Level Tips

1. **Use Emmet Abbreviations**
   - Type `.container.flex` and press Tab
   - Expands to `<div class="container flex"></div>`

2. **Multi-cursor Editing**
   - Hold Ctrl and click to place multiple cursors
   - Type to edit all at once

3. **Code Snippets**
   - Create custom snippets in `.vscode/snippets.json`
   - Reuse common patterns

4. **Git Integration**
   - Ctrl + Shift + G to open Source Control
   - Commit, push, pull directly from VSCode

---

For more help, visit the VSCode docs: https://code.visualstudio.com/docs
