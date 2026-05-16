# ai-expense-tracker
AI powered expense tracking API built with n8n, Gemini, and Supabase
# AI Expense Tracker API

An intelligent expense tracking API that understands 
natural language input.

## What it does
Send a message like "Spent 500 on groceries" and the 
system automatically extracts, validates, and saves 
the expense.

## Tech Stack
- n8n — workflow automation
- Google Gemini — AI for natural language processing  
- Supabase — database storage
- Webhook — REST API endpoint

## How it works
1. POST request hits webhook with natural language message
2. Input validation checks if message exists
3. AI Agent extracts item, amount, and category
4. Amount validation ensures expense data is complete
5. Data saved to Supabase database
6. Returns proper HTTP response (200/400)

## API Usage

**Endpoint:** POST /webhook/expense

**Success Request:**
{
  "message": "Spent 300 on pizza"
}

**Success Response (200):**
{
  "success": true,
  "message": "Expense is saved!"
}

**Error Response (400):**
{
  "success": false,
  "error": "message field is required"
}

## Key Features
- Natural language expense input
- Input validation
- AI-powered data extraction
- Proper HTTP status codes
- Error handling
