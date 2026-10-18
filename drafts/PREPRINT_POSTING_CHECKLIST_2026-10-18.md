# arXiv posting checklist — Paper 1 preprint (MoralCircle / APS)

Updated 18 Oct 2026. Replaces `ARXIV_SUBMISSION.md` (which described the
APS 1 paper, a different manuscript with a different claim). arXiv rules below
were read on 18 Oct 2026 from:

- Submission overview: https://info.arxiv.org/help/submit/index.html
- Schedule and availability: https://info.arxiv.org/help/availability.html
- Licences: https://info.arxiv.org/help/license/index.html
- Endorsement: https://info.arxiv.org/help/endorsement.html
- Metadata (title, abstract, authors, comments): https://info.arxiv.org/help/prep.html

**Why we post:** a Neuromatch project (Duarte, with Street and Keeling of Kim et al. 2026) is working on the same relation between mind attribution and moral-status attribution across kinds of entity. The arXiv announcement date is the public timestamp that establishes priority for the route design and the Ladak replication.

## 0. What must be true before anyone clicks

- [ ] OSF preregistration filed 20 Oct, before any new model call; the registration URL is pasted into the abstract, Section 3 and Section 8 of the manuscript.
- [ ] Every `[RESULT]` placeholder in `PREPRINT_PAPER1_DRAFT_2026-10-18.md` is filled, or the section is cut. arXiv moderation rejects obviously incomplete papers, and a placeholder in the announced version cannot be edited back out (replacements get a new version number; v1 stays visible).
- [ ] `[UNRESOLVED]` entity-set marker resolved (frozen 30 vs route-balanced 36). Same text as the OSF filing.
- [ ] No number from the team's own human study anywhere in the PDF, including figures and the appendix. Search the final PDF for "31", "N = 31", "convenience".
- [ ] The word "bias" appears only inside cited titles. Search the PDF.
- [ ] Reference list: every `[title]` and `[initial]` slot filled from the DOI landing page; `[verify]` items resolved or removed.
- [ ] Canary string present in the released invented-entity file; the held-back descriptions are NOT in the PDF or the repo.
- [ ] Joe has approved the author line, the order of authors, and the correspondence email.
- [ ] FAccT 2027 anonymity: check the call. If FAccT 2027 requires anonymised submission, confirm the CFP's preprint policy before posting. Most recent FAccT CFPs allow preprints but ask authors not to advertise them; read the exact 2027 wording and save a copy with the date. [CFP wording to confirm]

## 1. Timing — land the announcement on or right after 3 Nov 2026

arXiv's schedule (US Eastern; from the availability page, read 18 Oct 2026):

| Submitted between | Announced |
|---|---|
| Mon 14:00 → Tue 14:00 | Tue 20:00 |
| Tue 14:00 → Wed 14:00 | Wed 20:00 |
| Wed 14:00 → Thu 14:00 | Thu 20:00 |
| Thu 14:00 → Fri 14:00 | Sun 20:00 |
| Fri 14:00 → Mon 14:00 | Mon 20:00 |

No announcements on Friday or Saturday. 3 Nov 2026 is a Tuesday. Chiba is UTC+9; US Eastern is UTC−5 after 1 Nov 2026 (DST ends that day), so 14:00 ET = **04:00 JST the next morning**.

- **Plan A (announcement on 3 Nov ET):** complete the final "Submit Article" step **between Mon 2 Nov 14:00 ET and Tue 3 Nov 14:00 ET**, i.e. between **04:00 JST Tue 3 Nov and 04:00 JST Wed 4 Nov**. Announced Tue 3 Nov 20:00 ET = Wed 4 Nov 10:00 JST. The submission timestamp is the moment of the final submit step, and that timestamp is the date arXiv shows under "Submission history". Target: submit the preprint in the same sitting as the FAccT submission on 3 Nov JST.
- **Plan B (buffer for a hold):** quality checks can take 1–4 days and arXiv says sometimes longer. If the paper is held, it announces when released, not on the planned day. To protect the date, submit the arXiv version **as early as the results are final**, even a day or two before the FAccT deadline; the submission-history timestamp is what records priority, and it predates the announcement. Do not wait for a FAccT-formatted PDF if a clean preprint PDF exists first.
- Unsubmitting to fix an error before announcement resets the clock to the resubmission time. Preview carefully once; do not churn.
- arXiv IDs are assigned at announcement, so the ID will begin `2611.` even though the paper is submitted on 3 Nov (or `2610.` if it announces before midnight ET on 31 Oct).
- No arXiv holiday falls between 27 Oct and 6 Nov 2026 (next listed: Thu 26 Nov).

## 2. Account and endorsement

- [ ] Tuba's arXiv account uses the **university email** (s26Z1001YJ@chibatech.ac.jp). arXiv says an institutional address speeds endorsement and can auto-endorse.
- [ ] cs.CY is a new category for this account, so an **endorsement request is likely** on first submission. Do this the week of 20 Oct, not on 3 Nov: start a new submission, pick cs.CY, and if the form asks for endorsement it generates a request link. Send the link to Joe (or another established cs.CY/cs.CL/cs.AI arXiv author). One positive endorsement per category is needed; cross-lists can also require endorsement.
- [ ] Alternative that avoids the issue: Joe submits from his own account, which may already be endorsed for these categories, with Tuba as first author in the metadata. The submitter does not have to be the first author. Decide this with Joe on or before 20 Oct.

## 3. File to upload

- [ ] One PDF, produced from Markdown → HTML → PDF (not from LaTeX; arXiv rejects PDFs it can tell were built from TeX source and asks for the source instead). If the FAccT version is built in the ACM LaTeX template, upload the **LaTeX source**, not that PDF.
- [ ] All figures embedded; arXiv does not accept papers with omitted figures or external links in place of figures.
- [ ] File names: only `a-z A-Z 0-9 _ + - . , =`; case-sensitive.
- [ ] Front page: title, authors with affiliation, the line "Preprint. Submitted to ACM FAccT 2027. Preregistered on OSF on 20 October 2026: <URL>", and the licence statement matching what is chosen below. No copyright line that contradicts the arXiv licence.
- [ ] Under 16 MB total is not an arXiv rule, but keep the PDF small; large figure PDFs slow the preview.

## 4. Metadata (copy-paste; ASCII only — arXiv rejects curly quotes, long dashes and ligatures pasted from a PDF)

- **Title:** [the title chosen from the three candidates; no all-caps, no Unicode]
- **Authors:** Tuba Ali (Chiba Institute of Technology, Narashino, Japan), Joe Austerweil (Chiba Institute of Technology, Narashino, Japan)
  — "Firstname Lastname", no honorifics or degrees; affiliations in parentheses, city and country at most. If Joe's primary affiliation differs, use his; confirm with him.
- **Primary category:** cs.CY (Computers and Society)
- **Cross-lists:** cs.CL (Computation and Language), cs.AI (Artificial Intelligence)
- **MSC / ACM class:** leave blank unless Joe wants an ACM CCS code.
- **Abstract:** plain text, under 1,920 characters, no "Abstract" word, no markdown, no section symbols (write "Sec. 4"), retype any dash as `-` and quotes as `"`. Copy from the manuscript once every [RESULT] is filled and trim to length.
- **Comments field** (frozen after announcement; write it once, carefully):
  `[N] pages, [M] figures, [K] tables. Submitted to ACM FAccT 2027. Preregistered on OSF (20 Oct 2026) before data collection: <OSF URL>. Models only; no human-subjects data. Code, prompts and model outputs: <repo URL>. Part of the invented-entity benchmark is held back and carries a canary string.`
  Do not put a copyright statement in Comments. Do not put author roles in the Authors field; if needed, roles go here.
- **Report number / journal ref / DOI:** leave blank now. Add the ACM DOI as a journal-ref later if accepted; that edit does not create a new version.

## 5. Licence

arXiv licences are **irrevocable per version**. Options and the recommendation:

- **Recommended: arXiv.org perpetual, non-exclusive licence 1.0.** Gives arXiv distribution rights only and keeps every venue option open. ACM FAccT allows preprints of submitted work under this licence; it does not require CC-BY on the preprint.
- **CC BY 4.0** is fine if Joe prefers open reuse; many publishers accept CC-BY preprints, and ACM's open-access route permits it. It is a one-way door: a later version can be more open, not less.
- **Avoid** CC0 (gives up copyright; conflicts with some publisher agreements) and the ND/NC variants unless a funder requires them.
- If Chiba Institute of Technology or a funder has an open-access mandate, check it before 3 Nov; a mandate can require CC BY. [Funder / institutional OA policy to confirm with Joe]

## 6. Click-through, in order

1. Log in with the university-email account. Start a new submission; agree to the licence chosen above.
2. If asked for endorsement, stop and send the request link (Section 2). Resume when endorsed.
3. Upload the PDF (or LaTeX source). Wait for the preview; open it and check every figure and the reference list rendered.
4. Enter the metadata from Section 4. Paste the abstract into a plain-text editor first to strip Unicode.
5. Preview the abstract page. Check authors, categories and the Comments field letter by letter; Comments cannot be edited after announcement.
6. Click the final "Submit Article" step inside the window from Section 1. Note the exact time and the submission ID in the deviation log.
7. Save the confirmation email. The timestamp in it is the priority record.

## 7. After announcement

- [ ] Put the arXiv ID in the repo README, the OSF registration's "related links", the paper's data-availability line and the FAccT submission's supplementary material if the CFP permits a non-anonymous preprint link; otherwise hold it until the camera-ready.
- [ ] Post the arXiv link in #who-matters-to-ai with the date and time of announcement.
- [ ] Register the DOI arXiv assigns (10.48550/arXiv.<id>) in the lab's publication list.
- [ ] Do **not** replace the version before the FAccT decision unless there is an error of fact; each replacement is a new timestamped version and the Comments field of v1 stays as written.
- [ ] If FAccT accepts: add journal-ref and ACM DOI; post the camera-ready as v2 under the same licence or a more open one.
- [ ] CogSci / AIES / AI & Ethics all accept papers with arXiv preprints; the preprint forecloses nothing.

## 8. Things that can delay or sink the post

- Endorsement not sorted before 3 Nov (fix: Section 2, week of 20 Oct).
- A PDF that arXiv detects as TeX-generated (fix: upload source, or build from HTML).
- Unicode in the title or abstract field ("Bad character(s)" error at the final step).
- A placeholder left in the PDF; moderators can hold a paper that looks unfinished.
- A copyright statement on the front page that contradicts the licence.
- Submitting after 14:00 ET on 3 Nov pushes the announcement to Wed 4 Nov 20:00 ET; submitting after 14:00 ET on Thu 5 Nov pushes it to Sun 8 Nov.
