## n8n-trip-planer-with-llm

##Overview
This n8n workflow automates a personalized “travel tips” flow, starting with a new request in Airtable, generating AI-powered trip suggestions, fetching relevant images, formatting everything into a stylish HTML page, and notifying the user—all with approval and feedback built in.

![image](https://github.com/user-attachments/assets/275746ac-44f1-42c9-b6b1-95eb096e35cb)

## 🗺️ Flow Summary

### **Airtable Trigger**
Watches an Airtable table for new records (travel requests).  
Each request includes a **Location** and **User Email**.

---

### **Groq (Llama 3) AI Suggestion**
The workflow sends the *Location* and any extra user requests to Groq’s Llama 3 model.  
The AI returns three must-see attractions (**title**, **short description**, **coordinates** in string format).

---

### **Image Fetch via Unsplash**
For each attraction, a search is performed on Unsplash to get a relevant photo (1 per attraction).

---

### **Data Merging**
Merges the AI’s JSON results with their corresponding Unsplash image URLs.

---

### **HTML Page Generation**
Generates a modern, mobile-friendly HTML page that lists the suggested attractions with descriptions, images, and map links (Google, OSM, Waze).  
Includes an **Approve / Reject** button for user feedback.

---

### **Send Email to User**
The user receives the generated HTML page via email.

---

### **Approval & Feedback Flow**
- User can **Approve** or **Reject** the suggestions via a form link.
- On approval: workflow updates Airtable with a public link to the HTML preview (hosted on GitHub Pages).
- On rejection: workflow saves the feedback and updates the request status in Airtable.

---

### **GitHub Integration (for Approval)**
If approved, the HTML page is pushed to a GitHub repository (using GitHub Actions or Pages for publishing).

---

### **Technologies Used**
- n8n: No-code workflow automation.

- Airtable: Collects travel requests.

- Groq (Llama 3): Generates attraction recommendations.

- Unsplash API: Fetches attraction images.

- GitHub: Stores and publishes HTML results.

- SMTP: Sends the result to the user’s email.

### **Customization Points**
- AI Prompt: Easily edit the AI instructions for different languages, formats, or details.

- Email Templates: Fully customizable HTML and style for branded emails.

- Approval Logic: Add additional steps (like Slack, SMS) as needed.

### **Security Note**
Never commit API keys or credentials to public repos.
Replace all placeholders (like YOUR-KEY) with real secrets using environment variables or the n8n credential manager.
