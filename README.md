# Resume Automation

Beginner-friendly resume generation workflow that helps you:
- Build one reusable background profile
- Tailor resume content for each job description
- Generate a clean `.docx` resume in seconds

This project is designed so your template stays fixed while sections like summary, experience bullets, and project bullets are generated dynamically per application.

Feel free to use this small automation application.

Author: Purva Patel

---

## 1. What This App Does

This app takes AI-generated JSON and injects it into a Word resume template.

It updates these sections dynamically:
- Professional Summary
- Work Experience
- Projects

Your static information in `template.docx` (such as name, contact, core skills formatting, and layout) stays untouched.

---

## 2. Repository Structure

```
Resume-Automation/
├── README.md
├── requirements.txt
├── resume.py
├── resume_data.json
├── template.docx
├── background data/
│   └── background.md
├── prompts/
│   ├── starter-interview-prompt.txt
│   └── prompt.txt
└── output/
    └── .keep
```

What each item is for:
- `resume.py`: Main script that fills markers inside `template.docx`.
- `resume_data.json`: The AI output JSON consumed by the script.
- `template.docx`: Your base resume design with placeholders.
- `background data/background.md`: Your full personal background profile (master source).
- `prompts/starter-interview-prompt.txt`: Prompt to help you create your background from scratch.
- `prompts/prompt.txt`: Prompt used for each job application to generate resume-tailored JSON.
- `output/`: Generated resumes are saved here.

---

## 3. First-Time Setup (One Time)

### Step 1: Install Python dependencies

```bash
pip install -r requirements.txt
```

### Step 2: Confirm template exists

Make sure `template.docx` is present in the root folder. The script reads this file every time.

---

## 4. Start From Zero: Create Your Background Profile

If you do not already have a complete professional background document:

### Step 1: Open the interview prompt

Use:
- `prompts/starter-interview-prompt.txt`

### Step 2: Give that prompt to an AI assistant

The AI will ask you a complete set of interview questions (personal info, education, experience, projects, skills, certifications, etc.).

### Step 3: Answer fully, then collect final output

After you answer, the AI should return a structured background document.

### Step 4: Save it to your background file

Paste the final result into:
- `background data/background.md`

This becomes your reusable source profile for future applications.

---

## 5. Per Job Application Workflow (Repeat Every Time)

### Step 1: Copy the tailoring prompt

Use:
- `prompts/prompt.txt`

### Step 2: Add the target job description

Replace the placeholder job description section in the prompt with the actual job posting text.

### Step 3: Provide your background content

Give the AI your `background data/background.md` content along with the prompt.

### Step 4: Get strict JSON output

The AI should return one JSON object matching the required schema.

### Step 5: Paste JSON into `resume_data.json`

The file must contain valid JSON only.

### Step 6: Generate the resume

```bash
python resume.py resume_data.json my_resume_output.docx
```

Generated file location:
- `output/my_resume_output.docx`

---

## 6. Full Flow in One View

```
No background document yet
      ->
Use prompts/starter-interview-prompt.txt with AI
      ->
Answer questions
      ->
Save final profile to background data/background.md
      ->
For each job, use prompts/prompt.txt + job description + your background
      ->
AI returns resume JSON
      ->
Paste into resume_data.json
      ->
Run python resume.py resume_data.json output_name.docx
      ->
Receive tailored resume in output/
```

---

## 7. Privacy and Security Recommendation

Your background file can contain sensitive personal information.

Recommended best practice:
- Use a local-running AI agent/model when possible.

Why:
- Better privacy control
- Reduced risk of sharing personal career data with third-party hosted services
- Easier to keep your resume workflow fully on your own machine

If you must use a cloud AI service, avoid sharing unnecessary personal identifiers.

---

## 8. JSON Rules You Should Not Break

Before running the script, validate that:
- `resume_data.json` is not empty
- JSON is valid (no trailing commas, correct quotes)
- Required keys exist:
  - `professional_summary`
  - `work_experience`
  - `projects`
- `work_experience` bullets contain exactly 3 items per job
- `projects` bullets contain exactly 2 items per project
- `tech_stack` in projects is a comma-separated string

---

## 9. Troubleshooting

### Problem: Script fails immediately
Possible causes:
- `resume_data.json` is empty or invalid JSON
- Missing dependency (`python-docx`)

Fix:
- Recreate valid JSON using the prompt
- Run `pip install -r requirements.txt`

### Problem: Marker warning appears
If you see warnings like marker not found, your `template.docx` may not include:
- `{{PROFESSIONAL_SUMMARY}}`
- `{{WORK_EXPERIENCE}}`
- `{{PROJECTS}}`

Fix:
- Add these markers exactly in the template where content should be injected.

### Problem: Output file not where expected
All generated resumes are saved in `output/` by default.

---

## 10. Practical Tips

- Keep `background data/background.md` detailed and updated every few months.
- Keep job descriptions as complete as possible when prompting AI.
- Generate one JSON per application and keep filenames descriptive.
- Do not edit `resume.py` each time. Only update JSON input.

---

## 11. Quick Commands

Install:
```bash
pip install -r requirements.txt
```

Generate resume:
```bash
python resume.py resume_data.json my_resume_output.docx
```

---

## 12. License / Usage Note

This project is shared as a lightweight personal automation utility.

Feel free to use this small automation application and adapt it to your own resume workflow.