---
name: apply
description: Create or tailor job-application materials — cover letters, ATS-optimized resumes and resume bullets, LinkedIn role descriptions/bios, cold LinkedIn or recruiter outreach messages, sales/cold-call scripts, and recommendation letters. Use whenever the user gives a job description, asks to tailor/reformat a resume, write a cover letter, draft a LinkedIn blurb or outreach DM, or write a reference letter.
---

# Job-application kit

The user's professional background lives in `~/.claude/profile/background.md` (local, gitignored).
**Read it first** so you don't re-ask for facts already on file. If it's missing or
thin, ask for the target role + a resume, or to fill in the profile.

## First, scope the request
- **Target role matters** — the user targets more than one type of role (see the profile) and the
  keyword choices differ (e.g. data/AI engineering vs. sales). If the JD doesn't make the track
  obvious, ask which one.
- Default output is **copy-paste-ready** into a Word/Google doc. Offer a `.docx` (use the `docx`
  plugin) for resumes and formal letters.

## Cover letter
- Mirror the JD's exact keywords/requirements; map each to a concrete thing he's actually done
  (pull from the profile). No "highly motivated student" filler.
- 3–4 tight paragraphs, specific over generic.
- Add a proper header (name, contact, date, company) so it pastes cleanly into a document.

## Resume / ATS  (this is a validated spec — follow it)
- **Single column** (multi-column layouts get mangled by ATS parsers). Standard headers:
  Professional Summary · Technical Skills · Professional Experience · Selected Projects · Education.
- No tables / text boxes / graphics / icons / headers-footers. Real bullet points. Calibri 10–11pt.
  Use **tab stops** (not spacer characters) to right-align dates.
- A **dense, role-targeted Technical Skills section** with exact-string matches to the JD — ATS
  scoring favors exact matches.
- Quantified, action-verb bullets (Architected / Built / Designed / Implemented). Never duplicate
  bullets across two jobs.
- Early-career ⇒ **one page**. Build the docx, render a preview image, and verify it fits one page;
  if it spills, trim the Coursework line and Selected Projects first.
- Drop high school. Keep the school's real city in Education even if his contact city differs.

## LinkedIn
- **Role description / bio**: punchy summary of one specific role (pull the role from the profile)
  — what was built + the stack.
- **Outreach DM** (hiring manager or alumni): short, specific, attention-first. For sales roles,
  lead with drive/results, not credentials (the no-degree angle is fine).

## Recommendation letter
- Ask for: who, the relationship + years, the role/purpose, and 2–3 concrete traits or anecdotes.
- Offer a one-paragraph or a full-letter version.

## Always
- Pull facts from the profile. **Never hardcode personal data into this skill file** — it may sync
  to a public dotfiles repo. Keep personal info in `profile/` only.
- Offer to re-tailor per application (mirror each new JD's keywords).
- Never reference health, medical, or genetic information in any job material.
