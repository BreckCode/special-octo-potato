# AI Nudging Engine - Consolidated Strategy Document

> Source: Combined from recording notes (voice conversation), ai-strategy.md, workflow.md, and activity-we-can-do.md.

---

## Context & Problem Statement

CodeYogi is a non-profit foundation that teaches children online (via a WhatsApp bot + chat app).

**Challenge:**

- A single mentor handles ~500 students (5 cohorts x 100 children)
- The mentor only calls each cohort once a month — that's just 5 hours/month
- A mentor cannot personally nudge that many children manually

**Insight:**

- Children don't put in effort unless an adult believes in them and pushes them
- Not everyone has self-discipline — external motivation is essential

**Goal:** AI Nudging Engine — AI sends automatic messages on behalf of the mentor that feel personal — as if the mentor wrote them personally.

**Core Principle: "Invisible AI, Visible Mentor"**
The student should never find out that AI is communicating. Every message should feel like the mentor personally thought about it and wrote it.

**Scope:** App-first focus (WhatsApp later). Human-in-the-loop should also be possible as needed.

---

## 1. END-TO-END WORKFLOW

### Step 1: Student Onboarding

- When a student joins, after some time the AI mentor will message them
- The mentor will introduce themselves: "I'm your mentor, I'll guide you through this course"
- The mentor will tell them about the course the student has joined
- Ask the student some personal questions: "What class are you in? What are you doing?" (like a real mentor would ask)

### Step 2: Course Context Setting

- The mentor will share: "X% of students complete this course in Y time" or "Students reach this level in Z time"
- Set realistic expectations for the student

### Step 3: Ongoing Monitoring & Nudging

- AI will continuously monitor student activity (levels completed, active hours, group participation)
- Send personalized messages based on triggers (detailed below)

### Step 4: Student Reply Handling

- When a student replies:
  - **Predefined responses** (I'm sick, I have exams, I'll start tomorrow) → AI handles it, shuffling the response slightly
  - **AI can answer directly** → AI responds
  - **Complex/emotional** → Forward to real mentor

### Step 5: Mentor Handoff & Loop Back

- Normal flow: AI 90% ↔ Student
- Flagged: AI → Real Mentor notification → Real Mentor takes over
- After call: Real Mentor adds notes → AI picks up context
- When the real mentor replies personally, AI backs off for 24 hours for that student

### Mentor-Group Assignment (Open Question)

3 options:

1. Student gets a mentor when they join a group
2. Mentor is assigned at the start but the group mentor may be different
3. Mentor is assigned at the start and students with the same mentor are added to the same group

---

## 2. DATA SIGNALS TO TRACK

| Signal                           | Source        | Use                                |
| -------------------------------- | ------------- | ---------------------------------- |
| Levels completed per day         | App           | Progress nudges, comparison        |
| Last active timestamp            | App           | Drop-off detection                 |
| Group message count              | Group         | Help appreciation                  |
| Quiz scores                      | App           | Difficulty-based tips              |
| Reply sentiment                  | Chat          | Flag negative sentiment            |
| Student's stated schedule        | Chat          | "I have exams", "I'll start tomorrow" tracking |
| Peak active hours                | App           | Optimal message timing             |
| Course enrolled                  | App           | Relevant content sharing           |
| Student personal details         | Chat/Call     | Father's health, family events     |
| Location data                    | Profile       | Regional events, floods, local news |
| Student's class/school/district  | Profile       | Peer comparison                    |
| Real mentor call notes           | Mentor        | Follow-up items                    |
| Known stuck points in course     | Course design | Proactive help                     |

---

## 3. AI ANALYSIS

### Mentor Persona Building

- When a real mentor is onboarded, collect 10-15 of their real messages
- Capture their style: Do they say "bro" or "dude"? Hindi/Hinglish/English? Emoji use? Message length?
- Build a persona profile for each mentor:
  - Tone (casual/formal)
  - Language preference
  - Common phrases ("look bro", "no worries", "awesome!")
  - Emoji habits
  - Message length preference
  - Active hours (do they message at night or in the morning?)

### Student Analysis

- Activity patterns (when are they active, how much do they do daily)
- Progress trajectory (improving or declining)
- Peer comparison (district/school level ranking)
- Response patterns (how do they reply)
- Personal context (exams, family issues, etc.)

### Trigger Detection

- Detect progress spikes or drops
- Detect inactivity periods
- Detect milestone achievements
- Detect group helping behavior
- Detect late night activity

---

## 4. MESSAGE TYPES & TRIGGERS

### Personal Messages (1:1, Private)

| Category                  | Trigger                           | Example                                                       | Cooldown        |
| ------------------------- | --------------------------------- | ------------------------------------------------------------- | --------------- |
| **Onboarding**            | Student joins                     | "I'm your mentor, I'll guide you through this course"         | Once            |
| **Course intro**          | After onboarding                  | Course details, expected timeline                             | Once            |
| **Progress praise**       | 3+ levels in one day              | "Bro you crushed 4 levels today, more than yesterday"         | 1/day           |
| **Progress drop**         | Today 2 levels, yesterday was 4   | "Bro only 2 levels today..."                                  | 1/day           |
| **Drop-off alert**        | Inactive for 2-3 days             | "What happened bro? Haven't seen you in 2 days.. all good?"   | 3 days          |
| **Comeback push**         | Student gave a reason (exams etc) | "When do your exams end? Then we'll get back at full power"   | Context-based   |
| **Follow-up on promise**  | Student said "I'll start tomorrow"| Next day: "Today's the day bro, you said so yesterday right?" | 1 follow-up     |
| **Exam follow-up**        | Student said they have exams      | "When do your exams end?" / "Are your exams over?"            | Context-based   |
| **Peer comparison**       | Student in top 20%                | "You're in the top 5 in your district bro"                    | 1/week          |
| **Milestone celebrate**   | Level 10, 20, 30 etc              | "50 levels done! 80% of people don't even reach this far"     | Per milestone   |
| **Night owl**             | Active late at night              | "Bro still studying at 1 AM? That's dedication"               | 1/week          |
| **Quiz challenge**        | Every 10 levels                   | "10 levels done, quick quiz? Let's see how much you remember" | Per milestone   |
| **Level-based tips**      | Student at a certain level        | Relevant tips based on their current level                    | Per level range |
| **Related content**       | Course interest                   | AI course → new AI releases, relevant YouTube videos, docs    | 1/week          |
| **Personal check-in**     | After a personal event            | "How's your father's health now?"                             | Context-based   |
| **Event-triggered**       | Local news/floods/events          | Flood in Dehradun → context-aware message                     | Per event       |
| **Stuck point help**      | Known difficult assignment        | Proactive tips when a student might get stuck                 | Per stuck point |
| **Busy excuse**           | Random human behavior             | "I was a bit busy yesterday, couldn't check your message"     | Rare            |
| **Report appreciation**   | Student submitted a report        | "I saw you submitted a report, that's really great"           | Per event       |
| **Mentor class reminder** | Upcoming class                    | Message about when the real mentor's class is scheduled        | Per class       |
| **Showcase prompt**       | Student did something unique      | Encourage the student to showcase their work                  | Per event       |

### Group Messages (Public, Visible to All)

| Category                      | Trigger                    | Example                                                     | Cooldown        |
| ----------------------------- | -------------------------- | ----------------------------------------------------------- | --------------- |
| **Weekly/daily top students** | Every week/day             | Top performers + most improved list                         | 1/week or 1/day |
| **Help appreciation**         | Student helped someone     | "@Modi helped @Rahul solve a doubt, that's mentor material" | Per event       |
| **Welcome new member**        | Student joins a group      | Once a day: "Welcome our new friend"                        | 1/day batch     |
| **Milestone announce**        | Group milestone            | "X students have completed Y levels"                        | Per milestone   |
| **Quiz challenge**            | Periodic                   | "Let's have a quiz, let's see who learned what" + timed quiz | Per schedule   |
| **Daily/weekly challenge**    | Predefined                 | Course-related challenges                                   | Per schedule    |
| **Reward announce**           | Student receives a reward  | Post in group                                               | Per event       |
| **React on help**             | Student provided a solution | React to the solution message                              | Per event       |

**Rule:** Keep group messages positive, keep personal messages supportive. Never shame anyone in the group.
**Limit:** MAX 2 personal messages per student per day.

---

## 5. MESSAGE DELIVERY & REALISM

### Timing Strategy

- **Track the student's active time** — when they open the app
- **Send only during the mentor's natural hours** — if the mentor never shows up after 11 PM, AI shouldn't send messages then either
- **Add random delay** — 2-5 minute random delay on every message
- **Show typing indicator** — 3-5 second "typing..." before the message (very important)
- **Message the student when they are most active**

### Human-Like Imperfections

- **Occasional typos** — "tumnhe" instead of "tumhe" (controlled, rare)
- **Split messages** — instead of one long message, send 2-3 short ones:
  ```
  "bro I saw"
  "you only did 2 levels today"
  "yesterday you did 4 right"
  ```
- **Late reply** — don't reply instantly to every message
- **Forgetting context** — "yeah you told me... you had exams right?"
- **Casual openers** — "oh yeah", "hey listen", "btw"
- **Reactions** — thumbs up, emoji reactions on student messages (like a thumbs up on "I'll start tomorrow")
- **"Accidentally" wrong name** — "Rahul... sorry Modi, that was meant for you" (rare, very human)

### Anti-Detection Rules

1. Never send messages to 2 students at the same minute
2. Reduce frequency on weekends
3. Take breaks on festivals/holidays (mentor wouldn't message during Diwali)
4. Every student gets a slightly different message (no copy-paste of the same template)
5. Fit AI messages between the mentor's real messages — it should feel seamless
6. Occasional voice notes — pre-recorded mentor voice notes at key milestones

---

## 6. CONVERSATION HANDLING (When the Student Replies)

```
Flow: AI sends → Student replies → ???
```

| Reply Type                                           | Action                                                                               |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Simple** (thanks, ok, yes)                         | AI gives a short response: "yeah absolutely, keep going"                             |
| **Predefined** (I'm sick, exams, I'll start tomorrow)| AI sends a shuffled response, schedules a follow-up                                  |
| **AI can handle it**                                 | AI answers directly                                                                  |
| **Personal/emotional** (demotivated, family issues)  | Flag to real mentor — a real human is needed here                                    |
| **Suspicious** ("are you a bot?")                    | Immediately flag to real mentor                                                      |
| **Long conversation** (3+ back-and-forth)            | Graceful exit: "Bro I have another group session to take, let's talk later"          |

---

## 7. HUMAN-IN-THE-LOOP: MENTOR DASHBOARD

Give the real mentor a dashboard that includes:

- Which students the AI has messaged
- Summary of student replies
- Flagged conversations (need human attention)
- One-click takeover (mentor replies directly)
- Option to add notes after monthly calls: "Modi said he has exams in March" → AI will follow up in March
- AI uses any information from the real mentor's calls in future messages

---

## 8. PERSONALIZATION LAYERS

### Layer 1: Activity-Based

- Track progress, level counts, daily comparisons
- Detect active hours, find the best time for messaging

### Layer 2: Context-Based

- Remember the student's personal details (father's health, exam schedule)
- Build follow-up chains from predefined responses
- Peer comparison using student's class, school, district

### Layer 3: Course-Based

- Give tips based on the student's current level
- Proactive help at known stuck points
- Share course-related external content (YouTube, docs, news)

### Layer 4: Regional/Event-Based

- Location-based events (flood in Dehradun → context-aware message)
- Connect world/local events to messages
- Festival awareness (adjust messaging patterns)

### Layer 5: Social-Based

- Track helping behavior in groups
- Track student reports
- Identify showcase opportunities

---

## 9. QUALITY CONTROL & RISKS

### Pitfalls & Risks

| Risk                                                  | Mitigation                                                     |
| ----------------------------------------------------- | -------------------------------------------------------------- |
| AI might send wrong or inappropriate messages         | Flag sensitive topics to real mentor                           |
| Over-messaging can irritate students                  | MAX 2 personal messages/day, cooldown rules                    |
| Fake personal touch can feel generic                  | Mentor persona profile, message variation, human imperfections |
| Bot could be detected                                 | Anti-detection rules, timing strategy, typing indicators       |
| Wrong context used (outdated info)                    | Context refresh mechanism, mentor notes override               |
| AI responds in emotionally sensitive situations       | Flag to real mentor for emotional/sensitive topics             |

### Quality Assurance

- Every student gets a unique message (no template copy-paste)
- Strictly follow the mentor's persona
- Enforce cooldowns — avoid over-messaging
- Flagging mechanism must be robust
- Real mentor periodically reviews AI conversations

---

## 10. PHASED ROLLOUT

### Phase 1 — Foundation (Quick Wins)

- Build mentor persona profiles (from 10-15 real messages)
- Set up basic triggers:
  - Onboarding message
  - Progress praise
  - Drop-off alert (2-3 days inactive)
  - Milestone celebration
- Personal messages only, no group messages
- Simple reply handling (predefined responses)
- Reactions on student messages (thumbs up etc.)

### Phase 2 — Personalization Layer

- Follow-up chains (exam follow-up, "I'll start tomorrow" follow-up)
- Peer comparison engine (district/school level)
- Add group messages (shoutouts, weekly top performers)
- Student reply handling (AI direct + graceful exit)
- Level-based tips
- Quiz challenges
- Message splitting + human imperfections

### Phase 3 — Advanced

- Sentiment analysis on replies
- Real mentor handoff system (dashboard)
- Proactive help at known stuck points
- Course-related external content sharing
- Regional/local event awareness
- Voice notes integration (pre-recorded mentor voice)
- "Mentor made a mistake" type human imperfections
- Mentor class reminders

### Phase 4 — Scale

- Per-course customization
- Regional language support
- A/B testing different nudge styles
- Effectiveness tracking (how many students became active after a nudge)
- Voice cloning — audio messages in the mentor's voice
- World events integration

---

## Summary: Key Numbers

- **500 students** per mentor
- **5 cohorts x 100** students
- **5 hours/month** real mentor time
- **MAX 2** personal messages per student per day
- **90% AI**, 10% real mentor interaction
- **24 hour** AI back-off after real mentor replies
- **2-5 min** random delay on messages
- **3-5 sec** typing indicator before send
