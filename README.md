
# 🚀 LinkedIn Lead Generation Workflow (n8n + Google Custom Search + AI)

This project automates the discovery and evaluation of high-quality leads from LinkedIn using **n8n**, **Google Custom Search API**, **OpenAI (or Gemini)**, and **Google Sheets**.

---

## 📌 Objective

To identify potential clients such as **Founders, CTOs, CEOs, and Product Heads** who are looking for software development services (e.g., building MVPs, outsourcing, hiring dev teams).

---

## 🛠️ Workflow Summary

This automation performs the following steps:

### 1. **Search LinkedIn Profiles via Google Custom Search API**
- Query:  
  ```
  site:linkedin.com/in/ "Founder" AND "MVP" AND "hiring"
  ```
- Extracts results from LinkedIn profile links that contain relevant keywords.

---

### 2. **Filter Relevant Fields**
- From the Google Search API response, only the following fields are extracted:
  - `title` (name or role from LinkedIn)
  - `snippet` (description summary)
  - `link` (LinkedIn URL)

---

### 3. **Process Each Lead Individually**
- Each result is looped **one by one** using n8n logic (Function Node or SplitInBatches).
- This allows personalized AI evaluation per lead.

---

### 4. **Score the Lead using Google Gemini (or OpenAI)**
- An AI Agent is prompted like so:

  > "You are a CEO of a software services company. Based on the following title and description, rate this lead from 1 to 10 and explain why."

- **Structured Output Required**:
  ```json
  {
    "score": 8,
    "reason": "Looking to outsource MVP development"
  }
  ```

---

### 5. **Apply Conditional Filtering**
- If the `score >= 7`, the lead is considered **qualified**.

---

### 6. **Store Qualified Leads to Google Sheets**
- Final data written includes:
  - Name (title)
  - Description (snippet)
  - LinkedIn Profile Link
  - AI Score
  - AI Reason
  - Date and Source (optional)

---

## 🧰 Tools Used
| Tool         | Purpose                              |
|--------------|---------------------------------------|
| **n8n**      | No-code workflow automation           |
| **Google Custom Search API** | Discover LinkedIn profiles      |
| **OpenAI / Gemini** | Score and evaluate leads using AI |
| **Google Sheets**   | Save qualified leads              |

---

## 📝 Example Lead in Google Sheet

| Name                           | Description                              | Link                       | Score | Reason                             |
|--------------------------------|------------------------------------------|----------------------------|-------|------------------------------------|
| John Smith | Founder at SaaSCo | [linkedin.com/in/johnsmith](#) | 9     | Actively hiring for MVP dev work |

---

