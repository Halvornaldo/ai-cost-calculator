# AI Cost Savings Calculator - Frontend Design Specification

**Version:** 1.0  
**Date:** July 29, 2025  
**Document Owner:** UX/UI Design Team

## Project Overview

The AI Cost Savings Calculator is a trust-building, lead-generating web application designed for SMB owners (aged 35-55) to quantify potential AI automation savings. The design prioritizes clarity, credibility, and conversion optimization while maintaining accessibility across all devices.

## Technology Stack

- **Framework:** React 18+ with TypeScript
- **Styling:** Tailwind CSS with custom design tokens
- **Charts:** Chart.js with React-Chartjs-2 for data visualizations
- **Forms:** React Hook Form with Zod validation
- **Animation:** Framer Motion for micro-interactions
- **Icons:** Lucide React for consistent iconography
- **Build Tool:** Vite for optimal performance

## Design System Foundation

### Color Palette

```css
:root {
  /* Primary Colors - Professional Blue */
  --primary-50: #eff6ff;
  --primary-100: #dbeafe;
  --primary-500: #3b82f6; /* Main brand color */
  --primary-600: #2563eb;
  --primary-700: #1d4ed8;
  --primary-900: #1e3a8a;

  /* Success Colors - Trust-building Green */
  --success-50: #f0fdf4;
  --success-100: #dcfce7;
  --success-500: #22c55e;
  --success-600: #16a34a;
  --success-700: #15803d;

  /* Warning Colors - ROI Highlights */
  --warning-50: #fffbeb;
  --warning-100: #fef3c7;
  --warning-500: #f59e0b;
  --warning-600: #d97706;

  /* Neutral Colors - Professional Gray Scale */
  --gray-50: #f9fafb;
  --gray-100: #f3f4f6;
  --gray-200: #e5e7eb;
  --gray-300: #d1d5db;
  --gray-400: #9ca3af;
  --gray-500: #6b7280;
  --gray-600: #4b5563;
  --gray-700: #374151;
  --gray-800: #1f2937;
  --gray-900: #111827;

  /* Semantic Colors */
  --error: #ef4444;
  --info: #06b6d4;
  --background: #ffffff;
  --surface: #f9fafb;
}
```

### Typography Scale

```css
:root {
  /* Font Families */
  --font-primary: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;

  /* Font Sizes */
  --text-xs: 0.75rem;    /* 12px */
  --text-sm: 0.875rem;   /* 14px */
  --text-base: 1rem;     /* 16px */
  --text-lg: 1.125rem;   /* 18px */
  --text-xl: 1.25rem;    /* 20px */
  --text-2xl: 1.5rem;    /* 24px */
  --text-3xl: 1.875rem;  /* 30px */
  --text-4xl: 2.25rem;   /* 36px */
  --text-5xl: 3rem;      /* 48px */

  /* Line Heights */
  --leading-tight: 1.25;
  --leading-normal: 1.5;
  --leading-relaxed: 1.625;

  /* Font Weights */
  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;
}
```

### Spacing System

```css
:root {
  --space-1: 0.25rem;   /* 4px */
  --space-2: 0.5rem;    /* 8px */
  --space-3: 0.75rem;   /* 12px */
  --space-4: 1rem;      /* 16px */
  --space-5: 1.25rem;   /* 20px */
  --space-6: 1.5rem;    /* 24px */
  --space-8: 2rem;      /* 32px */
  --space-10: 2.5rem;   /* 40px */
  --space-12: 3rem;     /* 48px */
  --space-16: 4rem;     /* 64px */
  --space-20: 5rem;     /* 80px */
  --space-24: 6rem;     /* 96px */
}
```

### Breakpoints

```css
:root {
  --breakpoint-sm: 640px;   /* Mobile landscape */
  --breakpoint-md: 768px;   /* Tablet */
  --breakpoint-lg: 1024px;  /* Desktop */
  --breakpoint-xl: 1280px;  /* Large desktop */
  --breakpoint-2xl: 1536px; /* Extra large */
}
```

### Shadows & Effects

```css
:root {
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
  
  --radius-sm: 0.125rem;  /* 2px */
  --radius-md: 0.375rem;  /* 6px */
  --radius-lg: 0.5rem;    /* 8px */
  --radius-xl: 0.75rem;   /* 12px */
  --radius-2xl: 1rem;     /* 16px */
}
```

## Component Architecture

### Page Components

#### 1. Landing Page (`LandingPage`)

**Purpose:** Convert visitors to calculator users with clear value proposition

**Visual Specifications:**
- Hero section with compelling headline and social proof
- Benefit-focused copy with trust indicators
- Prominent CTA button leading to calculator
- Mobile-first responsive layout

**Props Interface:**
```typescript
interface LandingPageProps {
  testimonials: Testimonial[];
  trustBadges: TrustBadge[];
  onStartCalculator: () => void;
}
```

**Implementation Example:**
```jsx
const LandingPage: React.FC<LandingPageProps> = ({ 
  testimonials, 
  trustBadges, 
  onStartCalculator 
}) => {
  return (
    <div className="min-h-screen bg-gradient-to-br from-primary-50 to-white">
      {/* Hero Section */}
      <section className="px-4 py-12 md:py-20 max-w-7xl mx-auto">
        <div className="text-center mb-12">
          <h1 className="text-4xl md:text-5xl font-bold text-gray-900 mb-6 leading-tight">
            Discover How Much AI Can Save Your Business
            <span className="text-primary-600"> in Minutes</span>
          </h1>
          <p className="text-xl text-gray-600 mb-8 max-w-3xl mx-auto leading-relaxed">
            Get a personalized cost savings report showing exactly how AI automation 
            can reduce your operational expenses and boost productivity.
          </p>
          
          {/* Trust Indicators */}
          <div className="flex flex-wrap justify-center items-center gap-8 mb-10">
            {trustBadges.map((badge) => (
              <TrustBadge key={badge.id} {...badge} />
            ))}
          </div>

          {/* Primary CTA */}
          <Button
            size="xl"
            variant="primary"
            onClick={onStartCalculator}
            className="text-lg px-8 py-4 shadow-lg hover:shadow-xl transition-all duration-200 transform hover:-translate-y-0.5"
          >
            Calculate Your Savings Now
            <ArrowRight className="ml-3 w-5 h-5" />
          </Button>
          
          <p className="text-sm text-gray-500 mt-4">
            ✓ Free calculation ✓ No signup required ✓ Results in under 5 minutes
          </p>
        </div>

        {/* Social Proof */}
        <div className="grid md:grid-cols-3 gap-8 mt-16">
          {testimonials.map((testimonial) => (
            <TestimonialCard key={testimonial.id} {...testimonial} />
          ))}
        </div>
      </section>
    </div>
  );
};
```

#### 2. Calculator Wizard (`CalculatorWizard`)

**Purpose:** Multi-step form that collects business data and shows real-time calculations

**Visual Specifications:**
- Progress indicator showing current step (1-6)
- Consistent step layout with clear navigation
- Real-time savings preview in sidebar
- Mobile-optimized step transitions

**Props Interface:**
```typescript
interface CalculatorWizardProps {
  currentStep: number;
  totalSteps: number;
  formData: CalculatorFormData;
  savings: SavingsCalculation;
  onNext: () => void;
  onPrevious: () => void;
  onStepChange: (step: number) => void;
  onFormDataChange: (data: Partial<CalculatorFormData>) => void;
}
```

**Implementation Example:**
```jsx
const CalculatorWizard: React.FC<CalculatorWizardProps> = ({
  currentStep,
  totalSteps,
  formData,
  savings,
  onNext,
  onPrevious,
  onStepChange,
  onFormDataChange
}) => {
  return (
    <div className="min-h-screen bg-gray-50">
      <div className="max-w-7xl mx-auto px-4 py-8">
        <div className="grid lg:grid-cols-12 gap-8">
          {/* Main Form Area */}
          <div className="lg:col-span-8">
            <Card className="shadow-lg">
              {/* Progress Header */}
              <div className="p-6 border-b border-gray-200">
                <ProgressIndicator 
                  currentStep={currentStep} 
                  totalSteps={totalSteps}
                  onStepClick={onStepChange}
                />
              </div>

              {/* Step Content */}
              <div className="p-6 md:p-8">
                <AnimatePresence mode="wait">
                  <motion.div
                    key={currentStep}
                    initial={{ opacity: 0, x: 20 }}
                    animate={{ opacity: 1, x: 0 }}
                    exit={{ opacity: 0, x: -20 }}
                    transition={{ duration: 0.3 }}
                  >
                    {renderStepContent(currentStep, formData, onFormDataChange)}
                  </motion.div>
                </AnimatePresence>
              </div>

              {/* Navigation Footer */}
              <div className="p-6 border-t border-gray-200 flex justify-between">
                <Button
                  variant="ghost"
                  onClick={onPrevious}
                  disabled={currentStep === 1}
                >
                  <ArrowLeft className="w-4 h-4 mr-2" />
                  Previous
                </Button>
                
                <Button
                  variant="primary"
                  onClick={onNext}
                  disabled={!isStepValid(currentStep, formData)}
                >
                  {currentStep === totalSteps ? 'View Results' : 'Next Step'}
                  <ArrowRight className="w-4 h-4 ml-2" />
                </Button>
              </div>
            </Card>
          </div>

          {/* Savings Preview Sidebar */}
          <div className="lg:col-span-4">
            <SavingsPreview savings={savings} />
          </div>
        </div>
      </div>
    </div>
  );
};
```

#### 3. Results Dashboard (`ResultsDashboard`)

**Purpose:** Display comprehensive savings analysis with visual charts and lead capture

**Visual Specifications:**
- Hero metric showing total annual savings
- Interactive charts for different data views
- AI tool recommendations section
- Integrated email capture form

**Props Interface:**
```typescript
interface ResultsDashboardProps {
  results: CalculationResults;
  industryBenchmarks: IndustryData;
  aiRecommendations: AITool[];
  onEmailCapture: (email: string) => Promise<void>;
  onExportPDF: () => void;
  onSocialShare: (platform: string) => void;
}
```

**Implementation Example:**
```jsx
const ResultsDashboard: React.FC<ResultsDashboardProps> = ({
  results,
  industryBenchmarks,
  aiRecommendations,
  onEmailCapture,
  onExportPDF,
  onSocialShare
}) => {
  return (
    <div className="min-h-screen bg-gray-50">
      <div className="max-w-7xl mx-auto px-4 py-8">
        {/* Results Header */}
        <div className="text-center mb-12">
          <motion.div
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.6 }}
          >
            <h1 className="text-4xl md:text-5xl font-bold text-gray-900 mb-4">
              Your AI Savings Potential
            </h1>
            <div className="text-6xl md:text-7xl font-bold text-success-600 mb-2">
              ${results.annualSavings.toLocaleString()}
            </div>
            <p className="text-xl text-gray-600">
              Estimated annual cost savings with AI automation
            </p>
          </motion.div>
        </div>

        {/* Key Metrics Grid */}
        <div className="grid md:grid-cols-4 gap-6 mb-12">
          <MetricCard
            title="ROI Timeline"
            value={`${results.roiMonths} months`}
            icon={<TrendingUp />}
            trend={results.roiTrend}
          />
          <MetricCard
            title="Hours Saved"
            value={`${results.hoursSaved}/week`}
            icon={<Clock />}
            trend="positive"
          />
          <MetricCard
            title="Productivity Gain"
            value={`${results.productivityGain}%`}
            icon={<Zap />}
            trend="positive"
          />
          <MetricCard
            title="Industry Ranking"
            value={`Top ${results.industryPercentile}%`}
            icon={<BarChart />}
            trend="neutral"
          />
        </div>

        {/* Charts Section */}
        <div className="grid lg:grid-cols-2 gap-8 mb-12">
          <Card className="p-6">
            <h3 className="text-xl font-semibold mb-4">Savings Breakdown by Category</h3>
            <SavingsBreakdownChart data={results.categoryBreakdown} />
          </Card>

          <Card className="p-6">
            <h3 className="text-xl font-semibold mb-4">ROI Timeline Projection</h3>
            <ROITimelineChart data={results.roiProjection} />
          </Card>
        </div>

        {/* AI Recommendations */}
        <Card className="p-8 mb-12">
          <h3 className="text-2xl font-semibold mb-6">Recommended AI Tools</h3>
          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
            {aiRecommendations.map((tool) => (
              <AIToolCard key={tool.id} tool={tool} />
            ))}
          </div>
        </Card>

        {/* Lead Capture */}
        <EmailCaptureSection 
          onSubmit={onEmailCapture}
          incentive="Get your detailed PDF report and AI implementation roadmap"
        />
      </div>
    </div>
  );
};
```

### Core UI Components

#### Button Component

```typescript
interface ButtonProps {
  variant: 'primary' | 'secondary' | 'ghost' | 'success';
  size: 'sm' | 'md' | 'lg' | 'xl';
  disabled?: boolean;
  loading?: boolean;
  children: React.ReactNode;
  onClick?: () => void;
  className?: string;
}

const Button: React.FC<ButtonProps> = ({
  variant = 'primary',
  size = 'md',
  disabled = false,
  loading = false,
  children,
  onClick,
  className = ''
}) => {
  const baseClasses = 'inline-flex items-center justify-center font-medium rounded-lg transition-all duration-200 focus:outline-none focus:ring-2 focus:ring-offset-2';
  
  const variantClasses = {
    primary: 'bg-primary-600 text-white hover:bg-primary-700 focus:ring-primary-500 shadow-md hover:shadow-lg',
    secondary: 'bg-white text-primary-600 border border-primary-300 hover:bg-primary-50 focus:ring-primary-500',
    ghost: 'text-gray-600 hover:text-gray-900 hover:bg-gray-100 focus:ring-gray-500',
    success: 'bg-success-600 text-white hover:bg-success-700 focus:ring-success-500 shadow-md hover:shadow-lg'
  };

  const sizeClasses = {
    sm: 'px-3 py-2 text-sm',
    md: 'px-4 py-2 text-base',
    lg: 'px-6 py-3 text-lg',
    xl: 'px-8 py-4 text-xl'
  };

  return (
    <button
      className={`${baseClasses} ${variantClasses[variant]} ${sizeClasses[size]} ${disabled ? 'opacity-50 cursor-not-allowed' : ''} ${className}`}
      disabled={disabled || loading}
      onClick={onClick}
    >
      {loading && <Loader2 className="w-4 h-4 mr-2 animate-spin" />}
      {children}
    </button>
  );
};
```

#### Input Component

```typescript
interface InputProps {
  label: string;
  type?: 'text' | 'email' | 'number' | 'tel';
  placeholder?: string;
  value: string;
  onChange: (value: string) => void;
  error?: string;
  required?: boolean;
  helpText?: string;
  prefix?: string;
  suffix?: string;
}

const Input: React.FC<InputProps> = ({
  label,
  type = 'text',
  placeholder,
  value,
  onChange,
  error,
  required,
  helpText,
  prefix,
  suffix
}) => {
  return (
    <div className="space-y-2">
      <label className="block text-sm font-medium text-gray-700">
        {label}
        {required && <span className="text-error ml-1">*</span>}
      </label>
      
      <div className="relative">
        {prefix && (
          <div className="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
            <span className="text-gray-500 text-sm">{prefix}</span>
          </div>
        )}
        
        <input
          type={type}
          value={value}
          onChange={(e) => onChange(e.target.value)}
          placeholder={placeholder}
          className={`block w-full rounded-lg border ${
            error ? 'border-error' : 'border-gray-300'
          } px-3 py-2 text-gray-900 placeholder-gray-500 focus:border-primary-500 focus:ring-primary-500 ${
            prefix ? 'pl-8' : ''
          } ${suffix ? 'pr-12' : ''}`}
        />
        
        {suffix && (
          <div className="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
            <span className="text-gray-500 text-sm">{suffix}</span>
          </div>
        )}
      </div>
      
      {error && (
        <p className="text-sm text-error flex items-center">
          <AlertCircle className="w-4 h-4 mr-1" />
          {error}
        </p>
      )}
      
      {helpText && !error && (
        <p className="text-sm text-gray-500">{helpText}</p>
      )}
    </div>
  );
};
```

#### Card Component

```typescript
interface CardProps {
  children: React.ReactNode;
  className?: string;
  padding?: 'none' | 'sm' | 'md' | 'lg';
  shadow?: 'sm' | 'md' | 'lg' | 'xl';
}

const Card: React.FC<CardProps> = ({
  children,
  className = '',
  padding = 'md',
  shadow = 'md'
}) => {
  const paddingClasses = {
    none: '',
    sm: 'p-4',
    md: 'p-6',
    lg: 'p-8'
  };

  const shadowClasses = {
    sm: 'shadow-sm',
    md: 'shadow-md',
    lg: 'shadow-lg',
    xl: 'shadow-xl'
  };

  return (
    <div className={`bg-white rounded-xl border border-gray-200 ${shadowClasses[shadow]} ${paddingClasses[padding]} ${className}`}>
      {children}
    </div>
  );
};
```

### Specialized Components

#### ProgressIndicator

```typescript
interface ProgressIndicatorProps {
  currentStep: number;
  totalSteps: number;
  onStepClick?: (step: number) => void;
  showLabels?: boolean;
  stepLabels?: string[];
}

const ProgressIndicator: React.FC<ProgressIndicatorProps> = ({
  currentStep,
  totalSteps,
  onStepClick,
  showLabels = true,
  stepLabels = []
}) => {
  const progress = (currentStep / totalSteps) * 100;

  return (
    <div className="w-full">
      {/* Progress Bar */}
      <div className="relative mb-8">
        <div className="absolute top-1/2 transform -translate-y-1/2 w-full h-2 bg-gray-200 rounded-full">
          <div 
            className="h-full bg-primary-600 rounded-full transition-all duration-500 ease-out"
            style={{ width: `${progress}%` }}
          />
        </div>
        
        {/* Step Indicators */}
        <div className="relative flex justify-between">
          {Array.from({ length: totalSteps }).map((_, index) => {
            const stepNumber = index + 1;
            const isCompleted = stepNumber < currentStep;
            const isCurrent = stepNumber === currentStep;
            
            return (
              <div
                key={stepNumber}
                className={`flex flex-col items-center cursor-pointer ${
                  onStepClick ? 'hover:opacity-80' : ''
                }`}
                onClick={() => onStepClick?.(stepNumber)}
              >
                <div className={`w-8 h-8 rounded-full flex items-center justify-center text-sm font-medium transition-all duration-200 ${
                  isCompleted
                    ? 'bg-primary-600 text-white'
                    : isCurrent
                    ? 'bg-primary-100 text-primary-600 ring-2 ring-primary-600'
                    : 'bg-gray-200 text-gray-500'
                }`}>
                  {isCompleted ? (
                    <Check className="w-4 h-4" />
                  ) : (
                    stepNumber
                  )}
                </div>
                
                {showLabels && stepLabels[index] && (
                  <span className={`mt-2 text-xs font-medium text-center max-w-20 ${
                    isCurrent ? 'text-primary-600' : 'text-gray-500'
                  }`}>
                    {stepLabels[index]}
                  </span>
                )}
              </div>
            );
          })}
        </div>
      </div>
      
      {/* Step Counter */}
      <div className="text-center text-sm text-gray-500">
        Step {currentStep} of {totalSteps}
      </div>
    </div>
  );
};
```

#### SavingsPreview

```typescript
interface SavingsPreviewProps {
  savings: SavingsCalculation;
  loading?: boolean;
}

const SavingsPreview: React.FC<SavingsPreviewProps> = ({
  savings,
  loading = false
}) => {
  return (
    <Card className="sticky top-8" shadow="lg">
      <div className="text-center mb-6">
        <h3 className="text-lg font-semibold text-gray-900 mb-2">
          Your Savings Preview
        </h3>
        <p className="text-sm text-gray-600">
          Updates as you complete each step
        </p>
      </div>

      {loading ? (
        <div className="space-y-4">
          <div className="animate-pulse">
            <div className="h-8 bg-gray-200 rounded mb-2"></div>
            <div className="h-4 bg-gray-200 rounded mb-4"></div>
            <div className="h-16 bg-gray-200 rounded"></div>
          </div>
        </div>
      ) : (
        <div className="space-y-6">
          {/* Annual Savings */}
          <div className="text-center p-4 bg-success-50 rounded-lg">
            <div className="text-sm text-success-700 mb-1">Estimated Annual Savings</div>
            <div className="text-3xl font-bold text-success-700">
              ${savings.annualSavings.toLocaleString()}
            </div>
          </div>

          {/* Quick Stats */}
          <div className="space-y-3">
            <div className="flex justify-between items-center py-2 border-b border-gray-100">
              <span className="text-sm text-gray-600">Monthly Savings</span>
              <span className="font-medium text-gray-900">
                ${Math.round(savings.annualSavings / 12).toLocaleString()}
              </span>
            </div>
            
            <div className="flex justify-between items-center py-2 border-b border-gray-100">
              <span className="text-sm text-gray-600">Hours Saved/Week</span>
              <span className="font-medium text-gray-900">
                {savings.hoursSaved}
              </span>
            </div>
            
            <div className="flex justify-between items-center py-2">
              <span className="text-sm text-gray-600">ROI Timeline</span>
              <span className="font-medium text-gray-900">
                {savings.roiMonths} months
              </span>
            </div>
          </div>

          {/* Progress Indicator */}
          <div className="text-center pt-4 border-t border-gray-100">
            <p className="text-xs text-gray-500 mb-2">
              Complete all steps for detailed breakdown
            </p>
            <div className="flex space-x-1">
              {Array.from({ length: 6 }).map((_, index) => (
                <div
                  key={index}
                  className={`h-1 flex-1 rounded ${
                    index < savings.completedSteps 
                      ? 'bg-primary-600' 
                      : 'bg-gray-200'
                  }`}
                />
              ))}
            </div>
          </div>
        </div>
      )}
    </Card>
  );
};
```

## Chart Components

### SavingsBreakdownChart

```typescript
interface SavingsBreakdownChartProps {
  data: CategorySavings[];
}

const SavingsBreakdownChart: React.FC<SavingsBreakdownChartProps> = ({ data }) => {
  const chartData = {
    labels: data.map(item => item.category),
    datasets: [{
      data: data.map(item => item.savings),
      backgroundColor: [
        '#3b82f6', // Primary blue
        '#10b981', // Success green
        '#f59e0b', // Warning yellow
        '#ef4444', // Error red
        '#8b5cf6', // Purple
        '#06b6d4'  // Info cyan
      ],
      borderWidth: 2,
      borderColor: '#ffffff'
    }]
  };

  const options = {
    responsive: true,
    maintainAspectRatio: false,
    plugins: {
      legend: {
        position: 'bottom' as const,
        labels: {
          padding: 20,
          usePointStyle: true,
          font: {
            size: 12
          }
        }
      },
      tooltip: {
        callbacks: {
          label: (context: any) => {
            const value = context.parsed;
            const total = data.reduce((sum, item) => sum + item.savings, 0);
            const percentage = ((value / total) * 100).toFixed(1);
            return `${context.label}: $${value.toLocaleString()} (${percentage}%)`;
          }
        }
      }
    }
  };

  return (
    <div className="h-80">
      <Doughnut data={chartData} options={options} />
    </div>
  );
};
```

### ROITimelineChart

```typescript
interface ROITimelineChartProps {
  data: ROIProjection[];
}

const ROITimelineChart: React.FC<ROITimelineChartProps> = ({ data }) => {
  const chartData = {
    labels: data.map(point => `Month ${point.month}`),
    datasets: [
      {
        label: 'Cumulative Savings',
        data: data.map(point => point.cumulativeSavings),
        borderColor: '#22c55e',
        backgroundColor: 'rgba(34, 197, 94, 0.1)',
        fill: true,
        tension: 0.4
      },
      {
        label: 'Investment Cost',
        data: data.map(point => point.investmentCost),
        borderColor: '#ef4444',
        backgroundColor: 'rgba(239, 68, 68, 0.1)',
        fill: false,
        borderDash: [5, 5]
      }
    ]
  };

  const options = {
    responsive: true,
    maintainAspectRatio: false,
    interaction: {
      intersect: false,
      mode: 'index' as const
    },
    plugins: {
      legend: {
        position: 'top' as const
      },
      tooltip: {
        callbacks: {
          label: (context: any) => {
            return `${context.dataset.label}: $${context.parsed.y.toLocaleString()}`;
          }
        }
      }
    },
    scales: {
      y: {
        beginAtZero: true,
        ticks: {
          callback: (value: any) => `$${value.toLocaleString()}`
        }
      }
    }
  };

  return (
    <div className="h-80">
      <Line data={chartData} options={options} />
    </div>
  );
};
```

## Mobile Breakpoints and Responsive Behavior

### Mobile-First Approach

All components are designed mobile-first with progressive enhancement:

1. **Mobile (< 640px)**
   - Single column layouts
   - Full-width form elements
   - Condensed navigation
   - Touch-optimized buttons (min 44px)
   - Simplified charts and visualizations

2. **Tablet (640px - 1024px)**
   - Two-column layouts where appropriate
   - Side-by-side form sections
   - Enhanced chart interactivity
   - Expanded navigation options

3. **Desktop (> 1024px)**
   - Multi-column layouts
   - Sidebar navigation and previews
   - Full chart functionality
   - Hover states and animations

### Responsive Components

```css
/* Mobile-first responsive utilities */
.container {
  @apply px-4 mx-auto;
}

@screen sm {
  .container {
    @apply px-6 max-w-2xl;
  }
}

@screen md {
  .container {
    @apply px-8 max-w-4xl;
  }
}

@screen lg {
  .container {
    @apply px-12 max-w-6xl;
  }
}

@screen xl {
  .container {
    @apply px-16 max-w-7xl;
  }
}
```

## Trust-Building Design Elements

### 1. Visual Trust Indicators

- **Security Badges:** SSL certificates, privacy compliance logos
- **Social Proof:** Customer testimonials with photos and companies
- **Professional Design:** Clean, modern aesthetic with consistent branding
- **Progress Transparency:** Clear step indicators and completion status

### 2. Content Trust Signals

- **Clear Value Proposition:** Immediate benefit statements
- **Risk Reduction:** "No signup required" and "Free calculation" messaging
- **Authority Indicators:** Company credentials and expert endorsements
- **Realistic Expectations:** Conservative estimates with disclaimers

### 3. Interactive Trust Building

- **Real-time Feedback:** Immediate calculation updates
- **Error Prevention:** Input validation with helpful messages
- **Save Progress:** Ability to return without losing work
- **Export Options:** PDF reports for offline review

## Conversion-Optimized Form Design

### Multi-Step Strategy

1. **Progressive Disclosure:** Show only relevant fields per step
2. **Logical Flow:** Industry → Company → Tasks → Resources → Results
3. **Micro-Commitments:** Small steps build completion momentum
4. **Social Proof Integration:** Success stories between steps

### Form Optimization Techniques

```typescript
// Form validation with immediate feedback
const useFormValidation = (schema: z.ZodSchema) => {
  const [errors, setErrors] = useState<Record<string, string>>({});
  
  const validateField = (field: string, value: any) => {
    try {
      schema.shape[field].parse(value);
      setErrors(prev => {
        const newErrors = { ...prev };
        delete newErrors[field];
        return newErrors;
      });
    } catch (error) {
      if (error instanceof z.ZodError) {
        setErrors(prev => ({
          ...prev,
          [field]: error.errors[0].message
        }));
      }
    }
  };

  return { errors, validateField };
};

// Smart defaults based on industry
const getIndustryDefaults = (industry: string) => {
  const defaults = {
    retail: {
      avgHourlyWage: 15,
      commonTasks: ['inventory', 'customer-service', 'social-media']
    },
    healthcare: {
      avgHourlyWage: 25,
      commonTasks: ['scheduling', 'patient-records', 'billing']
    },
    // ... more industries
  };
  
  return defaults[industry] || defaults.general;
};
```

### Email Capture Strategy

```typescript
interface EmailCaptureProps {
  onSubmit: (email: string) => Promise<void>;
  incentive: string;
  placement: 'modal' | 'inline' | 'sidebar';
}

const EmailCaptureSection: React.FC<EmailCaptureProps> = ({
  onSubmit,
  incentive,
  placement = 'inline'
}) => {
  const [email, setEmail] = useState('');
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [isSuccess, setIsSuccess] = useState(false);

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    setIsSubmitting(true);
    
    try {
      await onSubmit(email);
      setIsSuccess(true);
    } catch (error) {
      // Handle error
    } finally {
      setIsSubmitting(false);
    }
  };

  if (isSuccess) {
    return (
      <div className="text-center p-8 bg-success-50 rounded-xl">
        <CheckCircle className="w-12 h-12 text-success-600 mx-auto mb-4" />
        <h3 className="text-xl font-semibold text-success-900 mb-2">
          Report Sent Successfully!
        </h3>
        <p className="text-success-700">
          Check your email for your detailed AI savings report and next steps.
        </p>
      </div>
    );
  }

  return (
    <div className="bg-gradient-to-r from-primary-50 to-primary-100 p-8 rounded-xl">
      <div className="max-w-2xl mx-auto text-center">
        <h3 className="text-2xl font-bold text-gray-900 mb-4">
          Get Your Detailed Report
        </h3>
        <p className="text-lg text-gray-600 mb-6">
          {incentive}
        </p>
        
        <form onSubmit={handleSubmit} className="flex flex-col sm:flex-row gap-4 max-w-lg mx-auto">
          <Input
            type="email"
            placeholder="Enter your business email"
            value={email}
            onChange={setEmail}
            required
            className="flex-1"
          />
          <Button
            type="submit"
            variant="primary"
            size="lg"
            loading={isSubmitting}
            className="sm:w-auto w-full"
          >
            Get Free Report
          </Button>
        </form>
        
        <p className="text-sm text-gray-500 mt-4">
          ✓ No spam, ever ✓ Unsubscribe anytime ✓ Your data is secure
        </p>
      </div>
    </div>
  );
};
```

## Performance Optimization

### Loading Strategy

1. **Critical CSS:** Inline above-the-fold styles
2. **Code Splitting:** Route-based component loading
3. **Image Optimization:** WebP format with fallbacks
4. **Lazy Loading:** Charts and non-critical components

### Bundle Optimization

```typescript
// Lazy load heavy components
const ResultsDashboard = lazy(() => import('./ResultsDashboard'));
const CalculatorWizard = lazy(() => import('./CalculatorWizard'));

// Chart.js tree shaking
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  ArcElement,
  Title,
  Tooltip,
  Legend,
  Filler
} from 'chart.js';

ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  ArcElement,
  Title,
  Tooltip,
  Legend,
  Filler
);
```

## Accessibility Compliance

### WCAG 2.1 AA Standards

1. **Keyboard Navigation:** All interactive elements accessible via keyboard
2. **Screen Reader Support:** Proper ARIA labels and semantic HTML
3. **Color Contrast:** Minimum 4.5:1 ratio for text
4. **Focus Management:** Clear focus indicators and logical tab order

### Implementation Examples

```typescript
// Accessible form components
const AccessibleInput: React.FC<InputProps> = ({ label, error, ...props }) => {
  const inputId = useId();
  const errorId = useId();
  
  return (
    <div>
      <label htmlFor={inputId} className="sr-only md:not-sr-only">
        {label}
      </label>
      <input
        id={inputId}
        aria-describedby={error ? errorId : undefined}
        aria-invalid={!!error}
        {...props}
      />
      {error && (
        <div id={errorId} role="alert" className="text-error">
          {error}
        </div>
      )}
    </div>
  );
};

// Skip navigation for screen readers
const SkipNavigation = () => (
  <a
    href="#main-content"
    className="sr-only focus:not-sr-only focus:absolute focus:top-4 focus:left-4 bg-primary-600 text-white px-4 py-2 rounded z-50"
  >
    Skip to main content
  </a>
);
```

## Implementation Roadmap

### Phase 1: Foundation (Weeks 1-4)
- [ ] Set up design system and tokens
- [ ] Create base components (Button, Input, Card)
- [ ] Implement responsive grid system
- [ ] Build landing page layout

### Phase 2: Calculator Core (Weeks 5-8)
- [ ] Multi-step wizard framework
- [ ] Form validation and state management
- [ ] Progress indicator component
- [ ] Savings preview sidebar

### Phase 3: Results & Visualization (Weeks 9-12)
- [ ] Chart components integration
- [ ] Results dashboard layout
- [ ] Email capture implementation
- [ ] PDF export functionality

### Phase 4: Polish & Optimization (Weeks 13-16)
- [ ] Mobile optimization
- [ ] Performance testing
- [ ] Accessibility audit
- [ ] A/B testing setup

This comprehensive design specification provides a solid foundation for building a professional, trustworthy, and conversion-optimized AI Cost Savings Calculator that meets the needs of SMB owners while achieving the business goals outlined in the PRD.