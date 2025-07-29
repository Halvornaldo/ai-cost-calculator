# AI Cost Savings Calculator - CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with the AI Cost Savings Calculator project.

## Project Status

Interactive web-based calculator for SMB owners to quantify potential AI automation cost savings. Foundation complete with PRD, development plan, and UI/UX specifications. Ready for Phase 1 development.

**Key Documents:**
- `prd.md` - Complete Product Requirements Document
- `plan.md` - 16-20 week development roadmap
- `design-specification.md` - Complete UI/UX specifications and component architecture

## Project Goals

- Generate 500+ monthly qualified leads for AI course platform
- Achieve 70% calculator completion rate
- 15% conversion rate from calculator to course inquiries
- Load times <3 seconds, calculations <2 seconds

## Getting Started

**Initial Setup (when development begins):**
```bash
npm install                    # Install dependencies
npm run dev                   # Start development server
npm run build                 # Build for production
npm run test                  # Run all tests
npm run lint                  # Run linting
npm run type-check           # TypeScript validation
```

## Project Architecture

**Frontend Framework:** React with TypeScript
**Styling:** CSS Modules with design system
**State Management:** React Context + hooks
**Charts:** Chart.js or D3.js for visualizations
**Build Tool:** Vite for fast development
**Testing:** Jest + React Testing Library + Cypress

**Key Components:**
- Multi-step wizard with 6 phases
- Real-time calculation engine
- Visual results dashboard with charts
- Lead capture system
- Mobile-responsive design

## Development Workflow

**Branch Strategy:** Git Flow (main, develop, feature branches)
**Code Quality:** ESLint + Prettier + TypeScript strict mode
**Testing:** Unit tests for calculations, E2E for user flows
**Deployment:** CI/CD pipeline with staging and production environments

**Target Metrics:**
- 99.5% uptime
- Mobile-first responsive design
- WCAG 2.1 AA accessibility compliance
- 10,000+ concurrent users capacity