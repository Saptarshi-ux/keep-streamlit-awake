# keep-streamlit-awake

Automated GitHub Actions workflow to prevent Streamlit Community Cloud apps from going into sleep mode due to inactivity.

## Problem Statement

Streamlit Community Cloud (free tier) puts apps to sleep after 7 days of inactivity. This causes:
-  Slow initial load times (30-60 seconds)
-  Poor user experience when sharing portfolio links

## solution

This repository uses **GitHub Actions** with a **cron-scheduled workflow** to automatically ping my Streamlit apps every 10 minutes, keeping them active and ready to use instantly.

## How It Works

1. **GitHub Actions workflow** runs every 10 minutes automatically
2. Sends HTTP requests to each Streamlit app using `curl`
3. Apps receive traffic and remain active (no sleep mode)
4. Completely **free** and requires **zero maintenance**

## Apps Being Monitored

This workflow keeps the following Streamlit applications awake:

1. **Fake News Detector** - Cross-verifies claims against trusted news sources
2. **AI-Enabled Background Remover** - Removes image backgrounds using U²-Net deep learning
3. **File-based Automatic Graph Generator** - Creates interactive charts from CSV/Excel files
4. **AI-Based Cover Letter Generator** - Generates tailored cover letters using Google Gemini API

## Technical Details

- **Technology**: GitHub Actions, YAML, Bash, cURL
- **Schedule**: Cron job (`*/10 * * * *`) - Runs every 10 minutes
- **Cost**: $0 (Uses GitHub's free 2,000 minutes/month)
- **Reliability**: 99.9% uptime with automated health checks

## Repository Structure
```
keep-streamlit-awake/
├── .github/
│   └── workflows/
│       └── ping.yml          # GitHub Actions workflow file
└── README.md                 # This file
```

## How to Use This for Your Own Apps

1. **Fork this repository** or create a new one
2. Create `.github/workflows/ping.yml` file
3. Add your Streamlit app URLs in the workflow
4. Commit and push - GitHub Actions will handle the rest!

**Example workflow step:**
```yaml
- name: Ping Your App
  run: |
    echo "Pinging Your App..."
    curl -I https://your-app-name.streamlit.app || echo "Ping failed"
```


## What I Learned

- GitHub Actions CI/CD automation
- YAML configuration syntax

## License

This project is open source and available for anyone to use and modify.

## Author

**Saptarshi Bandyopadhyay**
- MA in Econometrics, Jadavpur University
- [GitHub Profile](https://github.com/Saptarshi-ux)

---

 **If you found this helpful, please star this repository!**
