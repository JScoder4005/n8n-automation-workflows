# Job Scraper Bot Setup Guide

Automate your MERN stack job search with this n8n workflow that scrapes Naukri.com twice daily and sends you relevant job listings via WhatsApp.

## Features

- 🔍 Scrapes Naukri.com for MERN stack remote jobs
- 🤖 Filters jobs by keywords (React, Node.js, MongoDB, Express, Remote)
- 📱 Sends curated job list via WhatsApp
- ⏰ Runs automatically 2x daily (9 AM & 6 PM)
- 🎯 Shows top 10 most relevant jobs

## Setup Instructions

### 1. Import the Workflow

1. Open n8n at http://localhost:5678
2. Click menu → Import from File
3. Select `job-scraper-workflow.json`
4. The workflow will be imported

### 2. Configure WhatsApp Node

1. Double-click the "Send to WhatsApp" node
2. Add your WhatsApp credentials (same as weather/stock bot)
3. Set Phone Number ID
4. Set Recipient Phone Number (your number with country code)

### 3. Test the Workflow

1. Click "Execute Workflow" to test
2. Check if you receive job listings on WhatsApp
3. Verify the jobs are relevant

### 4. Activate

1. Toggle "Active" switch in top right
2. Workflow will run at 9 AM and 6 PM daily

## How It Works

```
Schedule Trigger (9 AM, 6 PM)
    ↓
Scrape Naukri.com
    ↓
Parse HTML & Extract Jobs
    ↓
Filter by MERN Keywords
    ↓
Format WhatsApp Message
    ↓
Send Notification
```

## Customization

### Change Job Keywords

Edit the "Parse Jobs" node to add/remove keywords:

```javascript
const keywords = ['react', 'node', 'mongodb', 'express', 'mern', 'javascript', 'remote', 'wfh'];
```

### Change Schedule

Edit the "Schedule Trigger" node:
- Current: `0 9,18 * * *` (9 AM & 6 PM)
- For 3x daily: `0 9,14,18 * * *` (9 AM, 2 PM, 6 PM)

### Add More Job Portals

Duplicate the workflow and change the URL to:
- LinkedIn: (requires different parsing logic)
- Indeed: `https://in.indeed.com/jobs?q=mern+stack+developer&l=Remote`
- AngelList: (requires API or different approach)

## Limitations

### Current Approach (HTML Scraping)

**Pros:**
- ✅ No login required
- ✅ Simple setup
- ✅ Works immediately

**Cons:**
- ⚠️ May break if Naukri changes HTML structure
- ⚠️ Limited to publicly visible jobs
- ⚠️ Doesn't auto-apply

### Upgrade Options

For better results, consider:

1. **Use Apify** (paid service):
   - More reliable scraping
   - Better data extraction
   - Handles pagination

2. **Browser Automation** (advanced):
   - Can login to your account
   - Access more jobs
   - Can auto-apply (risky)

3. **Premium Services**:
   - Naukri FastForward
   - Instahyre
   - Cutshort

## Troubleshooting

### No Jobs Found

- Naukri might have changed their HTML structure
- Try visiting the URL manually to verify it works
- Consider using a different job portal

### WhatsApp Not Sending

- Check if 24-hour window is open (send test message from Meta)
- Verify credentials are correct
- Check Phone Number ID

### Too Many/Few Jobs

- Adjust keywords in "Parse Jobs" node
- Add more specific filters (experience level, salary, etc.)

## Next Steps

1. **Monitor for 3 days** to see quality of jobs
2. **Refine keywords** based on results
3. **Add more job portals** (LinkedIn, Indeed)
4. **Consider upgrading** to browser automation for auto-apply

## Example Notification

```
🚀 *New MERN Stack Remote Jobs*
📅 05/12/2025

Found 5 new job(s):

1. *MERN Stack Developer - Remote*
   🏢 TechCorp India
   🔗 https://www.naukri.com/job/...

2. *Full Stack Developer (React + Node)*
   🏢 StartupXYZ
   🔗 https://www.naukri.com/job/...

...

💡 *Apply quickly to increase your chances!*
```

## Important Notes

> [!WARNING]
> **Web Scraping Considerations**:
> - Respect Naukri's terms of service
> - Don't scrape too frequently (current: 2x daily is safe)
> - HTML structure may change, requiring updates

> [!TIP]
> **Maximize Success**:
> - Apply within 24 hours of job posting
> - Customize your resume for each application
> - Follow up with recruiters on LinkedIn
> - Keep your Naukri profile updated
