# eCR Planner

A calendar planner for SUSS e-Course Registration (eCR). Pick courses, choose a class (CRN or TG) for each, and see every session and exam on a calendar before you register.

Built from `Full_Interim_Course_Schedule.pdf` (10,824 session rows, 879 courses, 1,603 classes). This is an unofficial planning aid. SUSS may change schedules without notice, so check eCR before you register.

## Features

- **Find courses**: search by course code or school, with filters for classes that fit your plan, evening and weekend classes, fully online classes, GSP100/UNE500, semester, level and language. Restricted classes are hidden unless you turn them on.
- **Pick a class**: every class shows its weekly pattern, dates, campus, exam, and how many sessions clash with your current plan. Hover a class to preview it on the calendar.
- **Clash warnings**: overlapping sessions and exams are marked in red. Back-to-back sessions at different physical campuses with under 60 minutes between them are flagged as tight travel.
- **Backup plans**: Plans A, B and C to start with. Add, rename, duplicate or delete plans.
- **Credits and exams**: credit units per course (default 5, editable) with a running total, plus an exam timetable that flags clashes and same-day exams.
- **For eCR**: a copyable list of course codes and classes, and a CSV export that imports into Google Calendar or Outlook.

Your plans are saved in your browser (`localStorage`). The hosted claude.ai version also syncs them to your account.

## Use it

Open `index.html` in a browser. Keep `schedule-data.js` in the same folder.

To host it on GitHub Pages: go to **Settings → Pages**, set the source to **Deploy from a branch**, then pick the branch and the `/ (root)` folder.

## Update the schedule

When SUSS publishes a new schedule PDF, regenerate the data file:

```sh
pip install pdfplumber
python scripts/extract_schedule.py Full_Interim_Course_Schedule.pdf schedule-data.js
```

The PDF does not list course titles or credit units, so the planner shows course codes only and assumes 5 CU until you change it.
