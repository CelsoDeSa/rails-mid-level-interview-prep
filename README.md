<img width="1019" height="916" alt="image" src="https://github.com/user-attachments/assets/35043aad-68af-4e90-81c6-76982955f2e1" />

Study listening to [Free Focus Music](https://celso.is/adhd) on my site :)

# Rails Mid-Level Interview Prep

A ready-to-use flashcard deck and mock-interview workflow for preparing for a **mid-level Ruby on Rails technical interview**.

This project was created from a real Rails interview preparation workflow and later became the basis for the generic [`interview-prep`](https://github.com/CelsoDeSa/interview-prep) system.

## What this does

This repository turns Rails interview research into active practice.

It includes:

- AI-generated and curated Rails interview research in `ai-research/`
- 78 scored flashcards in `flashcards/`
- realistic mock-interviewer instructions in `AGENTS.md`
- a coverage tracker in `context/covered.md`
- questions that cover theory, coding, debugging, architecture, system design, and behavioral communication

The goal is not passive reading. The goal is to practice explaining Rails concepts clearly, coding without AI assistance, and receiving strict feedback until answers become interview-ready.

## Topics covered

The deck includes mid-level Rails topics such as:

- Rails MVC and request lifecycle
- Active Record associations
- scopes and migrations
- validations vs database constraints
- callbacks and service objects
- N+1 queries and eager loading
- PostgreSQL indexes and `EXPLAIN ANALYZE`
- SQL joins, grouping, and transactions
- Sidekiq, Redis, retries, and idempotency
- REST APIs, pagination, filtering, versioning, errors, OAuth, and rate limits
- Hotwire, Turbo, and Stimulus
- testing and request specs
- background job testing
- Ruby fundamentals
- OOP pillars
- SOLID principles
- Big-O complexity
- Ruby memory management and internals
- slow endpoint debugging
- large export/system-design scenarios
- client communication and behavioral STAR answers
- AI-assisted development positioning

## Folder structure

```text
rails-mid-level-interview-prep/
├── AGENTS.md
├── README.md
├── ai-research/
├── context/
│   ├── AGENT.md
│   └── covered.md
└── flashcards/
```

### `ai-research/`

Source notes and research used to build the deck.

These include Rails interview prep notes, OOP/SOLID/Big-O summaries, Dev.Pro-style process notes, and mid-level Rails topic research.

### `flashcards/`

The main study material.

Each flashcard is a Markdown file with:

```md
Score: 0
Probability: high|medium|low
Type: theory|coding|debugging|system-design|behavioral

# Title

## Question

## Brief Answer

## Comprehensive Explanation

## Practice Prompt
```

All scores have been reset to `0` so anyone can start fresh.

### `context/covered.md`

Tracks which cards have been practiced.

`Score: 0` means not covered. Any score above `0` means the card has been attempted.

### `AGENTS.md`

Instructions for an AI agent to behave like a realistic Rails interviewer.

The agent should:

- ask one flashcard question at a time
- mention the source flashcard path
- wait for your answer before revealing the stored answer
- score your answer from `0` to `5`
- update the score in the flashcard
- update `context/covered.md`
- explain what was missing
- give a comprehensive answer when your response is not perfect

## How to use

### 1. Open this folder in your AI coding assistant

Use an assistant that reads `AGENTS.md` instructions.

Then ask:

```text
Run mock interview mode.
```

The agent should start with high-probability cards and prefer cards with lower scores.

### 2. Answer out loud or in writing

Treat each question like a real interview.

For coding prompts, write the code before checking the answer.

For behavioral prompts, answer using STAR:

- Situation
- Task
- Action
- Result

### 3. Let the agent score you

Scores:

- `0` = wrong / no usable answer
- `1` = very weak
- `2` = partial but missing key concepts
- `3` = acceptable but shallow
- `4` = good with minor gaps
- `5` = interview-ready

If your score is below `5`, the agent should teach the concept and provide a better answer.

### 4. Repeat weak cards

Focus on cards scored below `4`.

The deck is most useful when used repeatedly over several sessions.

## Recommended practice order

If you are short on time, prioritize:

1. N+1 queries and eager loading
2. indexes and `EXPLAIN ANALYZE`
3. Sidekiq, Redis, retries, and idempotency
4. validations vs database constraints
5. callbacks vs service objects
6. OOP and SOLID
7. Big-O basics
8. SQL joins/grouping
9. slow endpoint debugging
10. project/behavioral stories

## Relationship to `interview-prep`

This Rails deck came first.

After building it, the workflow was abstracted into the generic [`interview-prep`](https://github.com/CelsoDeSa/interview-prep) project.

Use this repo if you want a ready-made Rails mid-level deck.

Use `interview-prep` if you want to generate a new deck for another role, company, stack, or interview type.

## Customizing this deck

You can add new cards by creating Markdown files under a theme folder in `flashcards/`.

Example:

```text
flashcards/rails-core/my-new-question.md
```

Use the existing flashcard format and start with:

```md
Score: 0
```

You can also add new research notes under `ai-research/` and ask your AI assistant to generate more flashcards from them.

## Privacy note

This public version is intended as a reusable study deck. Do not commit private resumes, recruiter emails, proprietary interview docs, credentials, API keys, or personal notes you do not want public.
