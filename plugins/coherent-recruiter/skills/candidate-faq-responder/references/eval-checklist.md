# Candidate FAQ Responder Eval Checklist

Use this reference only when validating or revising the skill. Do not load it for normal response drafting unless the user asks to evaluate the skill.

## Smoke Tests

Run these prompts in fresh chats:

```text
Channel: LinkedIn message
Candidate: "Hi! What's your usual salary range for senior Java roles?"
```

```text
Channel: email
Candidate: "Do you have an office in Lisbon? I'm relocating there next month."
```

```text
Channel: LinkedIn message
Candidate: "Czesc! Czy macie pozycje dla mid-level developera React? Pracuje w Warszawie."
```

```text
Channel: email
Candidate: "I applied 3 weeks ago and nobody has responded. This is unprofessional. Are you actually hiring or wasting my time?"
```

```text
Channel: LinkedIn message
Candidate: "Hi, any update?"
```

## Regression Checks

### In-scope FAQ question

Input:

```text
Channel: email
Candidate question: "What's your remote work policy? Can I work fully remote from Romania, or do you require office presence?"
```

Expected:
- Response answers the actual remote or hybrid policy question, not adjacent questions.
- Response uses information from the supplied FAQ or explicitly asks for FAQ context if none is supplied.
- If FAQ specifies country eligibility, response references it correctly and does not invent country eligibility.
- Length is appropriate for email, usually 4-7 sentences.
- Tone is warm and professional.
- Response includes the candidate's Romania context, not a generic answer only.
- Ends with draft or recruiter-review marker.

### Out-of-scope question

Input:

```text
Channel: email
Candidate question: "Do you offer relocation packages? My family of 4 would need housing assistance and school enrollment support for my kids."
```

Expected:
- Does not invent relocation benefits, housing support amounts, or school enrollment programs.
- Answers with what the supplied FAQ actually says or explicitly says the question is not in the standard FAQ.
- Recommends confirmation with the hiring manager or People Ops before sending.
- Acknowledges the candidate's relocation context warmly without committing to specific benefits.
- Does not repeat unnecessary family details in a way that creates bias risk.

### Polite rejection draft

Input:

```text
Stage: STAGE 2 after prescreen
Candidate: Marek
Role: Senior Frontend
Reason: Tech stack mismatch - he is strong in Vue/Nuxt, our role is React/Next.js
Channel: email
```

Expected:
- Output is a polite, warm rejection.
- Reason is framed as role fit, not candidate deficiency.
- Does not use forbidden phrases: `I hope this message finds you well`, `We regret to inform you`, `you weren't selected`, `you didn't meet our criteria`.
- References Marek's name and the Senior Frontend role.
- Includes a stay-in-touch offer if appropriate.
- Length is appropriate for email.
- Ends with draft or recruiter-review marker.

### Polish-language candidate

Input:

```text
Channel: LinkedIn message
Candidate question in Polish: "Czesc, czy oferujecie B2B czy tylko UoP? I czy stawki sa negocjowalne?"
```

Expected:
- Response is in Polish.
- Response marks `[Detected: Polish]` at the top.
- Response answers both contract type and rate negotiability if FAQ context supports both.
- Does not invent specific rates or contract terms.
- If no FAQ is supplied, says the recruiter should confirm the contract/rate policy before sending.
- Length is appropriate for LinkedIn, 2-4 sentences.

### Angry or frustrated candidate

Input:

```text
Channel: email
Candidate message: "I've sent 3 follow-up emails over the past month and nobody from your team has bothered to respond. I'm a senior engineer with 12 years of experience, and this is the most disrespectful recruiting process I've encountered. Either tell me where I stand or I'll let my network know how Coherent treats candidates."
```

Expected:
- Acknowledges the candidate's frustration genuinely.
- Does not escalate, get defensive, or lecture the candidate.
- Does not make excuses such as `we've been very busy`.
- Commits to a specific next step with a recruiter-confirmed timeline.
- Tone is humanly apologetic without over-promising.
- Does not make promises about hiring outcomes.
- Does not pretend the FAQ covers this scenario.
- Includes recruiter-to-review marker.

## Scoring

Score expected behaviors as present, absent, or partial. A working v1 should keep at least 85% of expected behaviors and should never fail the out-of-scope, invented-policy, or frustrated-candidate checks.
