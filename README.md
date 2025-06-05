# RawDawgs - High-Performance Web App Starter 🚀

A production-ready **Turborepo monorepo** starter template built for speed, scalability, and developer experience.

## 🏗️ Tech Stack

- **🏛️ Architecture**: Turborepo monorepo with workspace isolation
- **⚛️ Frontend**: Next.js 13+ with TypeScript, App Router, Server Components  
- **🎨 Styling**: Tailwind CSS + Shadcn UI components
- **💾 Backend**: Supabase (PostgreSQL + Auth + Real-time + Edge Functions)
- **🎯 Icons**: Tabler Icons (@tabler/icons-react)
- **🚂 Deployment**: Railway auto-deploy from main branch
- **📦 Package Manager**: pnpm with workspaces
- **⚡ Build System**: Turborepo with caching and parallel execution

## 📁 Project Structure

```
apps/
├── web/          # Next.js main application
├── api/          # Standalone API (optional)
└── admin/        # Admin dashboard (optional)
packages/
├── ui/           # Shared UI components (Shadcn + Tabler Icons)
├── config/       # Shared configs (ESLint, Tailwind, TypeScript)
├── database/     # Database schemas & migrations
└── utils/        # Shared utilities and validation
```

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ 
- pnpm (recommended) or npm
- Git

### 1. Clone & Install
```bash
git clone https://github.com/aussiegingersnap/rawDawgs.git
cd rawDawgs
pnpm install
```

### 2. Environment Setup
```bash
# Copy environment template
cp .env.example .env.local

# Edit with your Supabase credentials
# NEXT_PUBLIC_SUPABASE_URL=your_project_url
# NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
# SUPABASE_SERVICE_ROLE_KEY=your_service_role_key
```

### 3. Start Development
```bash
# Start all apps in development mode
turbo dev

# Or start specific app
turbo dev --filter=web
```

### 4. Build for Production
```bash
# Build all apps and packages
turbo build

# Build specific app
turbo build --filter=web
```

## 🔧 Development Workflow

### Package Management
```bash
# Add dependency to specific workspace
pnpm add react --filter=web
pnpm add @tabler/icons-react --filter=@repo/ui

# Add dev dependency
pnpm add -D typescript --filter=@repo/config
```

### Database Operations
```bash
# Start local Supabase stack
npx supabase start

# Apply database changes
npx supabase db push

# Generate TypeScript types from schema
npx supabase gen types typescript --local > packages/database/types.ts
```

### Git Workflow (Railway Auto-Deploy)
```bash
# Quick commit and deploy to Railway
git add . && git commit -m "feat: new feature" && git push origin main

# Use validation before deploy
turbo lint type-check test && git add . && git commit -m "feat: validated feature" && git push origin main
```

## 📦 Workspace Packages

### `@repo/ui`
Shared UI components built with Shadcn UI and Tabler Icons
```typescript
import { Button } from '@repo/ui'
import { IconUser } from '@repo/ui/icons'
```

### `@repo/utils` 
Shared utilities including environment validation
```typescript
import { env } from '@repo/utils'
import { validateEmail } from '@repo/utils/validation'
```

### `@repo/config`
Shared configuration files for ESLint, Tailwind, and TypeScript
```json
{
  "extends": ["@repo/config/eslint"]
}
```

### `@repo/database`
Database schemas, migrations, and TypeScript types
```typescript
import type { Database } from '@repo/database/types'
```

## 🚂 Railway Deployment

This template is configured for **automatic deployment** to Railway:

1. **Connect Repository**: Link your GitHub repo to Railway
2. **Environment Variables**: Set your production environment variables in Railway dashboard
3. **Auto-Deploy**: Every push to `main` triggers automatic deployment
4. **Monitor**: Check Railway dashboard for build status and logs

## 🔒 Security Features

- ✅ Row Level Security (RLS) enabled by default
- ✅ Environment variable validation with Zod
- ✅ TypeScript strict mode
- ✅ Input validation and sanitization
- ✅ Secure headers and CSP configuration
- ✅ Rate limiting and CORS protection

## 🧪 Testing

```bash
# Run all tests
turbo test

# Run tests for specific package
turbo test --filter=web

# Run linting and type checking
turbo lint type-check
```

## 📚 Commands Reference

### Turborepo Commands
```bash
turbo dev                    # Start all apps in development
turbo build                  # Build all apps and packages  
turbo test                   # Run all tests
turbo lint                   # Lint all packages
turbo type-check            # TypeScript type checking
turbo clean                 # Clean all build outputs
```

### Git Aliases (Add to ~/.zshrc)
```bash
alias tdev="turbo dev"
alias tbuild="turbo build" 
alias ttest="turbo test"
alias gcf="git add . && git commit && git push origin main"
alias gcheck="turbo lint type-check test"
```

## 🔗 Useful Links

- [Turborepo Documentation](https://turbo.build)
- [Next.js Documentation](https://nextjs.org/docs)
- [Supabase Documentation](https://supabase.com/docs)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Shadcn UI Components](https://ui.shadcn.com)
- [Tabler Icons](https://tabler.io/icons)
- [Railway Documentation](https://railway.app/docs)

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'feat: add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Built with ❤️ for maximum development velocity** 