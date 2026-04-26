## How to run it

**Install dependencies once:**
```bash
pip install -r requirements.txt
```

**Every time you apply for a job:**
```bash
# 1. Save the AI JSON output as a file
#    e.g. paste it into: resume_data.json

# 2. Run the script
python resume.py resume_data.json my_resume_output.docx
```

---

## Full workflow in one diagram

```
Your PDF background + Job Description
            ↓
      Paste into AI prompt
            ↓
      AI outputs JSON
            ↓
   Save as resume_data.json
            ↓
   python resume.py resume_data.json output.docx
            ↓
   Word doc with your name/contact/skills intact
   + fresh summary, experience, projects injected
```

The only thing you touch each application cycle is the JSON file. The template and script never change.