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
  ## API Endpoints

### POST /expense — Create Expense
**Request:**
```json
{
  "message": "Spent 300 on pizza"
}
```
**Response:**
```json
{
  "success": true,
  "message": "Expense is saved!"
}
```

---

### GET /expense — Read All Expenses
**Request:** No body needed

**Response:**
```json
[
  {"id": 1, "Item": "Pizza", "Amount": 300, "Category": "Food"},
  {"id": 2, "Item": "Petrol", "Amount": 1200, "Category": "Transport"}
]
```

---

### PATCH /expense/:id — Update Expense
**Request:**
```json
{
  "amount": 999
}
```
**Response:**
```json
{
  "message": "The given id amount is updated"
}
```

---

### DELETE /expense/:id — Delete Expense
**Request:** No body needed

**Response:**
```json
{
  "success": true,
  "message": "Successfully deleted"
}
```

---

## Error Responses

| Status Code | Meaning |
|-------------|---------|
| 200 | Success |
| 400 | Bad Request — missing or invalid data |
| 403 | Forbidden — wrong API key |
| 404 | Not Found — expense not found |
| 500 | Server Error |
