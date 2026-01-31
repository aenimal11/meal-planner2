# Family Meal Planner

AI-powered meal planning for your household. Generate weekly meal plans, get recipes, and create shopping lists.

## Features

- 🍽️ Generate customized meal plans based on dietary preferences
- 📝 Get detailed recipes on-demand
- 🛒 Auto-generated shopping lists organized by category
- 📱 Export to Apple Notes (iOS/macOS)
- ⭐ Rate and save favorite meals
- 🔄 Regenerate or adjust individual meals
- 💾 Persistent storage using localStorage

## Deployment to Vercel

### Prerequisites

1. A Vercel account (free at vercel.com)
2. An Anthropic API key from console.anthropic.com
3. Git (optional but recommended)

### Step 1: Get Your Anthropic API Key

1. Go to https://console.anthropic.com
2. Sign up or log in
3. Add a payment method (API is pay-as-you-go)
4. Add credits (minimum $5)
5. Go to "API Keys" and create a new key
6. Copy the key (starts with `sk-ant-`)

### Step 2: Deploy to Vercel

**Option A: Using Vercel CLI (Recommended)**

```bash
# Install Vercel CLI
npm install -g vercel

# Navigate to your project folder
cd meal-planner

# Deploy
vercel

# Follow the prompts:
# - Link to existing project? No
# - What's your project's name? meal-planner (or whatever you want)
# - In which directory is your code located? ./
# - Want to modify settings? No

# Add your API key as an environment variable
vercel env add ANTHROPIC_API_KEY

# Paste your API key when prompted
# Select: Production, Preview, and Development

# Redeploy with the environment variable
vercel --prod
```

**Option B: Using Vercel Dashboard**

1. Go to https://vercel.com/new
2. Import your project folder (or create a Git repo first)
3. Configure:
   - Framework Preset: Other
   - Build Command: (leave empty)
   - Output Directory: public
4. Add Environment Variable:
   - Name: `ANTHROPIC_API_KEY`
   - Value: Your API key (sk-ant-...)
5. Click "Deploy"

### Step 3: Access Your App

After deployment, Vercel will give you a URL like:
`https://meal-planner-abc123.vercel.app`

Share this URL with your household!

## Usage

1. **New Plan**: Set how many days and meal types, then generate
2. **View Recipe**: Click on any meal to get detailed cooking instructions
3. **Regenerate**: Don't like a meal? Generate a replacement
4. **Adjust**: Ask for specific changes (make it spicier, use chicken instead, etc.)
5. **Rate & Save**: After cooking, rate the meal and save favorites
6. **Export**: Send shopping lists or recipes to Apple Notes

## Cost Estimate

With Claude Sonnet 4:
- Generating a 5-day meal plan: ~$0.10-0.20
- Getting a recipe: ~$0.02-0.05
- Typical monthly usage (2-3 plans/week): $2-5

## Dietary Preferences (Currently Configured)

- Family of 5 (2 adults, 3 kids)
- Avoiding ultra-processed foods, seed oils, sugar, enriched flour
- High animal protein (2.5# beef/fish or 4.5# chicken per dinner)
- Raw milk and eggs on hand

To modify these, edit the prompts in `public/index.html`

## Troubleshooting

**"Failed to generate meal plan"**
- Check that your API key is set correctly
- Verify you have credits in your Anthropic account
- Check browser console for detailed errors

**Shopping list won't export to Notes**
- On iOS: Make sure you're using Safari
- On macOS: Grant browser permission to open Notes
- Fallback: The list is also copied to clipboard

**Plans are slow to generate**
- This is normal - generating a full plan takes 10-20 seconds
- Each meal contains detailed info and a coordinated shopping list

## Local Development

```bash
# Install dependencies
npm install

# Start backend
npm start

# Backend runs on http://localhost:3000
# Open public/index.html in your browser
```

## File Structure

```
meal-planner/
├── api/
│   └── index.js          # Express backend (proxies Claude API)
├── public/
│   └── index.html        # Frontend app (React)
├── package.json          # Dependencies
├── vercel.json          # Vercel configuration
└── README.md            # This file
```

## Security Notes

- API key is stored server-side as an environment variable
- Never commit your API key to Git
- Meal history is stored in browser localStorage (private to each user)
- No user data is sent to the backend except AI prompts

## Support

For issues with:
- Deployment: Check Vercel docs
- API costs: See console.anthropic.com
- Feature requests: This is a vibe coding project - fork and customize!

---

Built with Claude, deployed with Vercel. Pure vibe coding energy ⚡
