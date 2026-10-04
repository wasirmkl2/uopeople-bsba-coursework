---
inclusion: always
---

# Quiz Answer Bank Workflow

When the user sends quiz/exam questions to be answered for any course in this repo, follow
this process. (This mirrors the workflow used in the household's other UoPeople repo.)

**Quiz answer bank content may be freely shared/mirrored between this repo and the
household's other UoPeople repo (`uopeople-bscs-coursework`)** — this is an explicit
exception to the assignment/discussion no-cross-referencing policy elsewhere in this repo's
steering (see `assignment-writing-rules.md` and `student-profile-saira.md`), which exists for
academic-integrity reasons around graded original writing. Quiz questions and their verified
answers are reference material, not graded submissions, so no such concern applies here — the
user has confirmed sharing this content between repos is fine, with no restrictions.

## Where the answer bank lives

Each course gets its own verified answer bank at:

`Term_N/<Course folder name>/Exams/uopeople-verified-quiz-answers.md`

Create this file the first time quiz questions come in for a course that doesn't have one
yet, using the structure described below.

Existing answer banks in this repo:

- **ENGL 1102-01:** `Term_02/ENGL 1102-01 English Composition 2 - AY2027-T1/Exams/uopeople-verified-quiz-answers.md`
  (Units 1–3 finished; content has been mirrored to/from the household's other UoPeople repo
  where the same course is shared.)

## Answering process — sourcing order for every new question

1. **That course's own `uopeople-verified-quiz-answers.md` file**, if one already exists —
   check for an exact or near-exact match (same question, same or reordered options) before
   doing anything else.
2. **The course's actual assigned Readings** (unit reading HTML pages, textbook
   chapters/sections named in them, video transcripts) — read the real material directly,
   don't answer from general recollection of the subject.
3. **The open internet**, only if steps 1–2 don't resolve it — and say explicitly when an
   answer relies on this step rather than the course's own materials. Course-specific quiz
   keys can diverge from the strict/standard textbook definition of a concept; when that
   happens, note it as a trap for that specific question rather than silently overriding it.

## Logging rule — confirm before logging, every time, no exceptions

**Do not write a new answer into any `uopeople-verified-quiz-answers.md` file until the user
has explicitly confirmed the real result of that specific question** (told you it scored
correct or incorrect on an actual quiz/self-quiz attempt). Do not log answers that are only
the assistant's own reasoning and haven't been confirmed yet — present them in chat first,
wait for the user's confirmation of the batch, and only then write them to the file.

When the user does confirm a batch, log each item with the right label:
- **CONFIRMED CORRECT** — user confirmed this scored correct.
- **CONFIRMED WRONG** — user confirmed this scored incorrect (note what the actual correct
  answer turned out to be, if known, so the trap is documented for next time).
- **REASONED (unconfirmed)** — only used if explicitly asked to log a not-yet-graded guess
  for future reference; never the default.

If a previously logged CONFIRMED entry is later contradicted by a new result (e.g., the
option set changes, or the same question is later confirmed with the opposite answer),
correct that entry in place and note both the old and new answer so the trap stays visible,
rather than leaving the outdated line standing unexplained.

## Repo push behavior for this file type

Unless the user says otherwise, commit and push updates to these answer-bank files directly
to `main` (this differs from the assignment/discussion branch-and-PR workflow in Section 7
of `assignment-writing-rules.md`, since answer banks are reference notes rather than graded
submissions) — but only once the user has said it's fine to push, and only after the
confirm-before-log rule above has already been followed for the content being pushed.



## Efficiency rule — extract PDF text before reading, don't over-verify clean matches

**Never read a `.pdf` reading file directly with a raw file-read tool.** Raw reads return
the undecoded PDF byte stream (compressed binary), which is not usable text and tends to
blow past output limits after burning a large number of tokens for zero signal. Before
reading any assigned-reading PDF for source-checking, extract its text first (e.g. a short
Python snippet using `pypdf`: install if missing, then `PdfReader(...).pages[i].extract_text()`
joined across pages) and read/search that extracted text instead of the PDF file itself.

**Don't multiply verification steps once a question is already resolved.** If the course's
own `uopeople-verified-quiz-answers.md` file or the assigned Readings give an unambiguous,
exact/near-exact match for a question, answer from that and stop — do not also run
redundant web searches "just to be sure" for questions with no ambiguity. Reserve extra
web verification (multiple searches, cross-checking several sources) for cases where:
- the assigned readings are silent or unclear on the question, or
- the question smells like a potential course-specific trap (absolute/unusual wording,
  an option set that doesn't cleanly match the textbook's own phrasing, a question type
  similar to a previously-logged trap in this file).

Getting a generic question right isn't evidence the sourcing process was unnecessary — the
bank-first → readings → web order exists specifically to catch the cases where this course's
quiz key diverges from the standard/generic answer (see the Unit 1 Q6 functional-relationship
trap as the concrete precedent, noted in the ENGL 1102-01 answer bank in the other UoPeople
repo). The point is to spend verification effort where divergence risk is real, not to verify
every question to the same depth regardless of how clear-cut it is.
