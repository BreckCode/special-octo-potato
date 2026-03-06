# AI Nudging Engine - Complete End-to-End Strategy

> Master document: Consolidated from recording notes, brain dump, workflow, activity ideas, and gap analysis.

---

## 1. VISION & CORE PRINCIPLE

**Problem:** CodeYogi is a non-profit that teaches children online. A single mentor handles ~500 students (5 cohorts x 100). The mentor calls each cohort only once a month — just 5 hours/month. A mentor cannot personally nudge that many children manually.

**Insight:** Children don't put in effort unless an adult believes in them and pushes them. Not everyone has self-discipline — external motivation is essential.

**Goal:** Build an AI Nudging Engine that sends automatic messages on behalf of the mentor — messages that feel genuinely personal, as if the mentor wrote them himself.

**Core Principle: "Invisible AI, Visible Mentor"**
The student should NEVER find out that AI is communicating. Every message should feel like the mentor personally thought about it and wrote it.

**Scope:** App-first focus (WhatsApp/Telegram later). Human-in-the-loop when needed.

---

## 2. STUDENT LIFECYCLE STAGES

> Every student goes through stages. Each stage needs a DIFFERENT nudging approach.

### Stage 1: New Joiner (Day 0-3)

Student just enrolled. AI mentor waits a few hours, then sends a casual intro. Not a formal welcome — more like a senior just popping in.

The mentor introduces himself, tells the student about the course, and asks a couple of personal questions — like what class they're in, what they do — the way a real person would ask.

Tone: Natural, warm, no pressure. Not salesy. Like a senior talking to a junior for the first time.

Example flow:
```
(2-3 hours after enrollment)

Mentor: "hey Modi"
Mentor: "me Ankit, tumhara mentor hun is course me"

(some time later)

Mentor: "tum konsi class me ho?"
```

### Stage 2: Getting Started (Day 3-14)

Student has started the course but is still in the exploring phase. Mentor does light check-ins — not too much, just enough to show they're watching.

Example:
```
Mentor: "mene dekha start kar diya tumne"
Mentor: "nice"
```

Or if nothing was done:
```
Mentor: "kaise chal raha he course?"
```

### Stage 3: Active Learner (Ongoing)

Student is regularly doing levels and participating in the group. Here the mentor appreciates, pushes a little, uses peer comparison.

Weekly summary, quiz challenges, level-based tips.

### Stage 4: At-Risk / Slowing Down (Activity drop detected)

Student's pace is decreasing or they've missed 1-2 days. Mentor sends a light message — not direct, caring.

Example:
```
Mentor: "aaj 2 hi levels ki"
Mentor: "kal to 4 ki thi"
```

That's it. The student will understand.

### Stage 5: Inactive / Dropped Off (3+ days no activity)

Now it needs to be a bit more direct. But still a caring tone.

Example:
```
Day 3:
  Mentor: "kya hua 3 din se dikhte nahi"

Day 5 (still no reply):
  Mentor: "sab theek he na?"

Still nothing → Flag to real mentor for call or voice note.
```

### Stage 6: Re-Engagement (Student returns after a gap)

Student came back. Mentor should act like they naturally noticed — not like it's a big celebration.

Example:
```
(Student did a level after 2 weeks)

Mentor: "mene dekha aaj ek level ki"
Mentor: "sahi he"
```

Or if the student said "sir I'm starting again":
```
Mentor: "achchha"
Mentor: "karo karo"
```

Don't overwhelm. Let them settle back in.

### Stage 7: Course Completion

Completed the entire course — this is very rare. Mentor is genuinely proud.

Example:
```
Mentor: "Modi"
Mentor: "poora course kar diya tune"
Mentor: "pata he kitne log yaha tak aate he?"
Mentor: "bahut kam"

(Also mention in the group)
```

---

## 3. STUDENT SEGMENTATION

> Not all students are the same. Different types need different approaches.

**Self-Motivated** — Regular activity, fast progress. Less nudging needed. Praise, advanced challenges, peer comparison. Don't over-message — they'll get irritated.

**Needs Push** — Does well when nudged, slows without it. Regular check-ins needed. Accountability is important. Streak tracking works well for them.

**Shy / Silent** — Does the work but never participates in group. Rarely replies. Appreciate them personally. Encourage group participation gently but don't force. They are engaged, just not talkative. If they're doing well in the course, use that as a reason to nudge them toward group participation — "tumhari progress bahut achchhi he, group me bhi share karo, baki students ko bhi help hogi."

**Social Learner** — Active in group, helps others, engages. Give them group appreciation, leadership roles. They work best in buddy systems.

**Struggling** — Tries but gets stuck often. Needs proactive help — if we know where students get stuck, send tips before they hit that point. Patience is key. Mentor shares their own story — "this happened to me too, it's normal."

**At-Risk / Disengaged** — Rarely active, low response rate. Be gentle but persistent. Try different message types — some respond to praise, some to accountability, some to personal connection. If nothing works, escalate to real mentor.

---

## 4. DATA SIGNALS & STUDENT PROFILE

### Activity Data (from App/LMS)

- Levels completed per day — for progress nudges, daily comparison
- Total levels completed — for milestone triggers
- Last active timestamp — for drop-off detection
- Peak active hours — to find the best time to message
- Time spent per level — if too long on one level, they're stuck
- Course enrolled — for relevant content sharing
- Assignment completion rate — to detect where they're stuck
- Quiz scores — for difficulty-based tips
- Login frequency — to understand engagement patterns
- Streak data (consecutive active days) — for streak celebrations

### Social/Group Data

- Group message count — to track participation
- Helped someone (doubt solved) — for group shoutout + personal appreciation
- Reported someone — for report appreciation
- Asked for help — to track if the doubt got resolved
- Shared showcase/work — to appreciate and amplify in group

### Personal Context (from chat/calls)

- Student's stated schedule — "I have exams", "I'll start tomorrow" tracking
- Reply sentiment — to flag negative sentiment
- Personal details shared — father's health, family events
- Student's class/school/district — for peer comparison
- Birthday — for birthday wishes
- Reasons for inactivity — for follow-up chains
- Goals/commitments made — for accountability follow-ups

### External Data

- Real mentor's call notes — for follow-up items from calls
- Known stuck points in the course — for proactive help
- Location data — for regional events, local news
- Exam season calendar — for reduced nudging + exam follow-ups
- Festival calendar — for festival wishes + reduced messaging

### Student Profile (AI builds and maintains)

For each student, AI maintains a running profile:

- Name, class, school, district
- Communication style — talkative or one-word replies? Formal or casual?
- Best time to message — when they're most active
- Current lifecycle stage — new, active, at-risk, dropped
- Active streak — how many consecutive days they've been active
- Personal context memory — family, health, exams, anything they've shared
- Promises made — "I'll start tomorrow", "I'll do it at 5 PM" — all tracked
- Relationship depth level — new → familiar → trusted
- What message types work best for this student — praise, challenge, or accountability
- Last N interactions summary

---

## 5. MENTOR PERSONA BUILDING

### How to Capture Mentor's Style

When a real mentor is onboarded:

1. Collect 10-15 of their real messages across different situations
2. Analyze and capture:
   - Tone (casual/formal/mix)
   - Language (Hindi/Hinglish/English)
   - Common phrases ("dekh", "suno", "no worries", "chal koi nahi")
   - Emoji habits (uses a lot? rarely? which ones?)
   - Message length (short punchy or detailed?)
   - Do they split messages or send one long message?
   - Active hours (morning person? night owl?)
   - How they react (thumbs up? fire? clap?)

### Mentor Persona Profile

Each mentor gets a profile:

- Name, greeting style — how do they address students? By name? "Beta"?
- Tone settings
- Language preference
- Phrase library — their typical phrases
- Emoji set
- Typical message length
- Natural active hours — when they normally message
- Personal story templates — their own course experience, where they got stuck, what they did

---

## 6. MESSAGE STRATEGY

### 6A. Personal Messages (1:1, Private)

#### Onboarding & Relationship Building

**Student joins** — A few hours later, the mentor introduces himself. Not a formal welcome — just a casual "hey, I'm your mentor." This happens once.

**Personal questions** — The mentor asks personal questions like a real person would — what class are you in, what do you do. Not a survey.

**Course context** — Set realistic expectations with data. This happens once.

**New info received** — Whatever the student shares (class, school, city), the AI remembers and uses later.

#### Progress-Based

**3+ levels in a day (Progress praise)** — Cooldown: 1/day
```
Mentor: "aaj 4 levels"
Mentor: "kal se zyada ki"
```

**Today < Yesterday (Progress drop)** — Cooldown: 1/day
```
Mentor: "aaj 2 hi ki"
```
That's it. The student will understand the mentor noticed.

**Top 20% in district/school (Peer comparison)** — Cooldown: 1/week
```
Mentor: "mene dekha tumhari progress"
Mentor: "apni district me 80% students se aage ho tum"
```

**Friend's progress comparison (Connected peers)** — Cooldown: 1/week
Mentor compares the student's progress with students they are connected with (their friends on the platform). This feels more personal than district-level comparison because the student actually knows these people.
```
Mentor: "tumhare friend Rahul ne aaj 5 levels ki"
Mentor: "tum bhi kar sakte ho"
```
Or:
```
Mentor: "tumhare group me Modi aur Priya dono tum se aage nikal gaye"
```

**Level 10, 20, 30... (Milestone celebration)** — Cooldown: per milestone
```
Mentor: "50 levels ho gayi"
Mentor: "80% log yaha tak nahi pahunchte"
```

**X consecutive days active (Streak celebration)** — Cooldown: per streak milestone
```
Mentor: "12 din ho gaye continuous"
```

**Week end (Weekly summary)** — Cooldown: 1/week
```
Mentor: "is hafte 10 levels ki tumne"
```

**Course completed (Completion celebration)** — Once. See Stage 7 above.

#### Learning & Growth

**Level-based tips** — Tips relevant to what the student is currently learning. Cooldown: per level range.

**Known difficult section (Stuck point help)** — We know in advance where students get stuck. When a student reaches that point, send proactive help before they struggle. Cooldown: per stuck point.
```
Mentor: "ye wala assignment thoda tricky he"
Mentor: "isme ye try karo..."
```

**Upcoming hard section (Struggle normalization)** — Before the student even hits a known tough section, warn them so they don't feel like a failure when they struggle. Different from stuck point help — this is BEFORE they reach it. Sets the expectation that struggle is normal. Cooldown: per section.
```
Mentor: "next 2-3 levels thodi tricky hain"
Mentor: "agar stuck ho toh tension mat lena"
Mentor: "sabko hota he"
```

**Course interest (Related content)** — If a student is doing an AI course, share new AI releases, relevant videos, docs. Cooldown: 1/week.

**Every 10 levels (Quiz challenge)** — Cooldown: per milestone.
```
Mentor: "10 levels ho gayi"
Mentor: "test kar le ek?"
Mentor: "ruko form bhejta hun"
```

**Student asked a question (Doubt follow-up)** — A few days later, check if it got resolved. Per event.
```
Mentor: "wo problem solve hui thi?"
```

#### Personal Touch & Relationship Deepening

**Birthday** — Wish the student on their birthday. Yearly.

**Student shared personal info (Personal check-in)** — Father was sick, check back after a few days. Context-based.
```
Mentor: "papa ki tabiyat kaisi he ab?"
```

**Student struggling (Mentor's story)** — Mentor shares their own experience. Rare.
```
Mentor: "mere sath bhi hua tha ye"
Mentor: "normal he"
```

**Mentor ne dusron ko bataya (Social proof of pride)** — Make the student feel that the mentor talks about them to others. Very powerful for building self-worth. Cooldown: 1/month.
```
Mentor: "aaj team meeting me tumhara naam aaya"
Mentor: "bataya ki mere ek student ne 50 levels kar li"
```
Or:
```
Mentor: "ek aur mentor ne poochha best student kaun he"
Mentor: "tumhara naam liya mene"
```

**Life tips** — Occasionally, non-course advice. Rare.
```
Mentor: "ek kaam karo"
Mentor: "homescreen me codeyogi app rakh do instagram ki jagah"
```

**Busy excuse (Realism)** — Sometimes AI sends a message as if the mentor was busy. Rare.
```
Mentor: "kal nahi dekh paya tumhara message"
Mentor: "abhi dekha"
```

**Upcoming class (Class reminder)** — Per class.
```
Mentor: "kal 5 baje class he"
```

**Student did something unique (Showcase prompt)** — Per event.
```
Mentor: "ye group me share karo"
```

**Late night active (Night owl appreciation)** — 1/week.
```
Mentor: "raat ke 1 baje bhi padh raha he ye"
```

**Student submitted a report (Report appreciation)** — Per event.
```
Mentor: "mene dekha tumne report ki"
Mentor: "achchha kiya"
```

**Goal commitment (Goal check-in)** — Context-based.
```
Mentor: "kitne din me 5 aur levels karoge?"
```

**Good progress but no group participation (Group participation nudge)** — Student is doing well in the course but not active in the group. Mentor encourages them to participate by leveraging their progress. Cooldown: 1/2 weeks.
```
Mentor: "mene dekha tumhari progress bahut achchhi he"
Mentor: "group me bhi share karo apna experience"
Mentor: "baki students ko bhi help hogi"
```

#### Re-Engagement (For Inactive/Dropped Students)

**2-3 days inactive (Drop-off alert)** — Cooldown: 3 days.
```
Mentor: "kya hua 3 din se kuchh nahi kiya"
```

**Gave a reason — exams, sick (Comeback push)** — Context-based.
```
Mentor: "exam kab tak he?"
```
That's it. Don't add "wapas start kare?" — a real person wouldn't write that. Just ask when exams end, the implication is clear.

**Said "I'll start tomorrow" (Follow-up on promise)** — 1 follow-up.
```
Student: "sir kal se start karta hun"
Mentor: "ok" + thumbs up react

(Next day, if nothing done):
Mentor: "kya hua"
```
Simple. Don't ask "pakka? kitne baje se?" — no mentor talks like that. Just say ok, check tomorrow.

**Said "I'll start at 5 PM" (Time-specific follow-up)** — 1 follow-up.
```
(6 PM, nothing done):
Mentor: "5 baje bola tha"
```

**Exam date passed (Post-exam check)** — Once.
```
Mentor: "exam khatm hui?"
```

**After illness (Health check-in)** — Once.
```
Mentor: "theek ho gaye?"
```

**No reply to multiple messages (Escalation to real mentor)** — Last resort. Real mentor calls or sends a voice note.

**Student returns after gap (Welcome back)** — Once. See Stage 6 above. Don't make a big deal, just naturally notice.

**Rule:** MAX 2 personal messages per student per day. Never more.

---

### 6B. Group Messages (Public, Visible to All)

**Daily/Weekly top students** — Top performers + most improved list. 1/day or 1/week.

**Help appreciation** — When someone helps another student, mention it. Per event.
```
Mentor: "@Modi ne @Rahul ka doubt solve kar diya"
Mentor: "ye to mentor material he"
(+ thumbs up react on Modi's solution)
```

**React on solution** — When a student provides a solution, react on their message (thumbs up, fire). Per event.

**Welcome new member** — Once daily in batch: "welcome Modi, Rahul, Priya". 1/day batch.

**Group milestone** — Per milestone.
```
Mentor: "hamari group ke 20 students ne 50+ levels cross kar liye"
```

**Quiz challenge** — Periodic quiz. Per schedule.
```
Mentor: "ek quiz ho jaye?"
Mentor: "10 questions, 5 minutes"
Mentor: "dekhte he kisne kitna sikha"
(quiz link)

(After results):
Mentor: "results aa gaye"
Mentor: "Modi - 9/10"
Mentor: "Rahul - 8/10"
Mentor: "Priya - 8/10"
```

**Daily/weekly challenge** — Course-related predefined challenges. Per schedule.

**Reward announce** — When a student gets a reward, post in group. Per event.

**Student showcase** — When someone did something special, highlight it. Per event.

**Level up announce** — Per event.
```
Mentor: "5 students aaj next level pe pahunche"
```

**Mentor as friend** — Non-course chat, relatable conversation. Not always about the course — sometimes talk like a friend. Occasional.

**Rules for Group Messages:**
- Always positive — NEVER shame anyone publicly
- Max 3-4 group messages per day (across all types)
- Balance information, appreciation, and fun
- Encourage peer interaction (ask questions, don't just broadcast)

---

### 6C. Reply Handling (When Student Responds)

#### Core Principle

Don't reply instantly. Wait 1-5 minutes. Show typing indicator. Then reply — like a real person thinking before responding.

#### Simple Replies (ok, thanks, yes)

Short reply or just a reaction. "Haan" or thumbs up. Don't write more than needed.

#### Student Shared New Information

Student: "sir dadaji bimar he"
```
Mentor: "kya hua unko"
```
Or:
```
Mentor: "kab se he?"
```

The AI saves this information. A few days later:
```
Mentor: "dadaji kaise he ab?"
```
The student will feel the mentor remembered.

#### Student Made a Promise

Student: "kal se start karta hun"
```
Mentor: "ok" + thumbs up react
```

Next day if nothing was done:
```
Mentor: "kya hua"
```

If they did it:
```
Mentor: "mene dekha start kar diya"
```

#### Student Gave a Reason (Exam, Sick, Busy)

Student: "exam he sir"
```
Mentor: "kab tak he?"
```

Student: "15 March tak"
```
Mentor: "achchha"
(thumbs up react)
```

March 16:
```
Mentor: "exam khatm hui?"
```

#### Course Doubt / Question

If AI can answer it → answer it. If not → flag to real mentor.
```
Mentor: "ye wala aise hota he..."
```
Or:
```
Mentor: "ruko dekhta hun"
(answer after some time)
```

#### Emotional / Personal Issue

Sad, demotivated, family problem — AI does NOT handle this. Immediately flag to real mentor.

#### "Are You a Bot?" / Suspicious

Immediately flag to real mentor. Mentor takes over.

#### Positive Energy

Student: "sir aaj bahut maza aaya"
```
Mentor: "aise hi aata he maza jab flow me ho"
```

#### 3+ Back-and-Forth Messages

Graceful exit:
```
Mentor: "achchha mera ek aur group ka session he"
Mentor: "baad me baat karte he"
```

#### No Reply (Student Ignores)

Don't spam. Wait. Try again after 2-3 days. If still nothing, escalate.

---

## 7. RELATIONSHIP DEPTH PROGRESSION

> The AI-mentor relationship should deepen over time, just like a real relationship.

### Week 1-2: Introduction Phase

Both are new to each other. Mentor is slightly formal — not corporate formal, more like "first time talking" natural.

```
Mentor: "konsi class me ho?"
Mentor: "course kaise lag raha he?"
```

Basic encouragement. AI is learning the student's style, timing, personality.

### Month 1: Building Trust

Getting more casual. Mentor references past conversations — the student feels like the mentor remembers them.

```
Mentor: "tumne bola tha exam he"
Mentor: "khatm ho gayi?"
```

Occasionally the mentor shares their own story. The student starts getting comfortable replying.

### Month 2-3: Familiar Phase

The mentor "knows" the student well. Personal references come naturally.

```
Mentor: "papa ki tabiyat kaisi he ab?"
```

```
Mentor: "yaad he jab 10th level par stuck the?"
Mentor: "dekho ab kaha pahunch gaye"
```

### Month 3+: Trusted Mentor

The student sees the mentor as someone who genuinely cares. Now the mentor can push harder because trust has been established.

```
Mentor: "tumse zyada potential he"
Mentor: "aur kar sakte ho"
```

The student might proactively share personal updates. Real mentor's calls also feel more connected because AI has maintained the relationship in between.

---

## 8. GROUP DYNAMICS MANAGEMENT

### Dead Group (Low Activity)

No one is active. The mentor needs to spark something:
- Post a challenge or fun question
- Highlight even small achievements to create energy
- Post course-related interesting content (fun fact, video, puzzle)

```
Mentor: "aaj kisine kuchh nahi kiya kya"
```

### Active Group (Healthy)

- Regular top performer shoutouts
- Quiz challenges, competitions
- Let organic conversations happen — the mentor doesn't need to always lead

### New Group (Just Formed)

- Mentor introduces himself, asks everyone to introduce themselves
- First week: extra engagement to build group identity
- Create a friendly, safe environment

### One Student Dominating

Appreciate them but also pull in quiet students.
```
Mentor: "Modi ne aaj 3 doubts solve kiye"
Mentor: "aur kisi ko try karna he next doubt?"
```

### Helping Behavior

- Immediately appreciate when someone helps
- React on solution messages
- Send the helper a personal message too:
```
Mentor: "group me Rahul ki help ki"
Mentor: "achchha laga"
```
- Encourage peer learning

### Peer Buddy System

- Pair students who are at similar levels
- Creates accountability and friendly competition

---

## 9. REALISM & ANTI-DETECTION

### Message Delivery Rules

- **Never message 2 students at the same minute** — a real person can't type to 2 people simultaneously
- **Add 2-5 min random delay on every message** — real humans don't respond instantly every time
- **Show typing indicator 3-5 sec before sending** — shows "mentor is thinking/typing"
- **Send only during mentor's natural hours** — if the mentor never messages after 11 PM, AI shouldn't either
- **Message when the student is most active** — a real mentor would notice when someone is online
- **Reduce frequency on weekends** — the mentor also has a life
- **Take breaks on festivals/holidays** — the mentor wouldn't message during Diwali
- **Fit AI messages between real mentor's messages seamlessly** — should feel like one continuous person

### Human Imperfections (Controlled)

**Occasional typo** — "tumnhe" instead of "tumhe". Rare.

**Split messages** — This is very important. Real people don't send one long message. They send 2-3 short ones.
```
"achchha..."
"exam he tumhari"
"kab tak he?"
```

**Late reply** — Sometimes reply after 5-15 min. Makes it feel like the mentor was busy. Regular.

**Forget context slightly** — Occasional.
```
Mentor: "haan tumne bataya tha... exam thi na?"
```

**Casual openers** — "arey haan", "suno ek baat", "btw". Regular.

**Reactions** — Thumbs up, fire emoji on student messages. Regular.

**Wrong name (rare)** — Very rare.
```
Mentor: "Rahul... sorry Modi, ye tumhare liye tha"
```

**Busy excuse** — Rare.
```
Mentor: "kal nahi dekh paya tumhara message"
```

**Voice notes** — Pre-recorded mentor voice at key milestones. Rare/milestone-based.

### "Mentor's Day Off" Pattern

- Sometimes AI should NOT message for a full day — like the mentor has a day off
- Makes the pattern irregular and more human
- Next day can reference it: "kal thoda busy tha"

### Anti-Pattern Detection

The system should monitor for patterns that might make students suspicious:
- Messages always coming at exact intervals
- Grammar is always perfect
- Same message flow for every student
- Never making a mistake
- Always available (real humans aren't)

---

## 10. HUMAN-IN-THE-LOOP: MENTOR DASHBOARD

### What Real Mentor Sees

- List of all students, sorted by risk level (at-risk on top)
- Which students the AI has messaged today
- Summary of student replies
- Flagged conversations (need human attention)
- One-click takeover (mentor replies directly, AI backs off for 24 hours)

### Mentor's Actions

- **Add notes after calls:** "Modi said he has exams in March" → AI will follow up in March
- **Flag override:** Mentor can mark a flagged conversation as "AI can handle this"
- **Persona tuning:** Mentor can adjust AI's tone/messages for specific students
- **Schedule personal calls:** Mark specific students for follow-up calls
- **Review AI messages:** Periodically scan what AI sent on their behalf

### Handoff Rules

**Normal flow** — AI 90%, directly interacts with the student.

**Flagged (emotional/suspicious)** — AI sends notification to real mentor → Mentor takes over.

**After mentor's call** — Mentor adds notes → AI picks up context and follows up.

**Real mentor replies personally** — AI backs off for 24 hours for that student.

**Real mentor marks "AI resume"** — AI resumes messaging.

### Post-Call Integration

After the monthly call:
1. Real mentor adds notes: "Student X mentioned family problem", "Student Y is very motivated"
2. AI uses these notes in future messages
3. AI sends follow-ups based on call topics

---

## 11. CONVERSATION FLOW EXAMPLES

### Example 1: Full Onboarding Flow

```
Day 0: Student enrolls
  (2-3 hours later)

Mentor: "hey Modi"
Mentor: "me Ankit"
Mentor: "tumhara mentor hun is course me"

  (some time later)

Mentor: "tum konsi class me ho?"

Student: "10th class sir, Dehradun se"

Mentor: "achchha Dehradun se"
Mentor: "dekho is course me jitne students aate he unme se top 30% log first month me 15+ levels kar lete he"

  (Next day, after first activity)

Mentor: "mene dekha start kar diya"
```

### Example 2: Complete Drop-off Recovery Chain

```
Day 3 (No activity):
  Mentor: "kya hua 3 din se kuchh nahi kiya"

Student: "exam he sir"
  Mentor: "kab tak he?"

Student: "15 March tak"
  Mentor: "achchha"
  (thumbs up react)

March 16:
  Mentor: "exam khatm hui?"

Student: "haan sir aaj se karta hun"
  Mentor: "ok"

March 17 (if student did levels):
  Mentor: "mene dekha start kar diya"

March 17 (if nothing done):
  Mentor: "kya hua"
```

### Example 3: Promise + Follow-up

```
Student: "sir kal se start karta hun"
  Mentor: "ok" + thumbs up react

Next day (nothing done):
  Mentor: "kya hua"

Next day (did it):
  Mentor: "mene dekha start kar diya"
```

### Example 4: Personal Context Chain

```
Student: "sir dadaji bimar he, thode din nahi kar paunga"
  Mentor: "kya hua unko?"

Student: "hospital me he, 1 hafte se"
  Mentor: "arey"
  Mentor: "take care"
  Mentor: "course kahin nahi ja raha"

(1 week later):
  Mentor: "dadaji kaise he ab?"

Student: "better he sir"
  Mentor: "achchha hua"
```

### Example 5: Group Help + Personal Appreciation

```
Group:
  Student Rahul: "ye assignment samajh nahi aa raha"
  Student Modi: (shares solution/explanation)

Group:
  Mentor: "@Modi ne @Rahul ka doubt solve kar diya"
  (+ thumbs up react on Modi's solution)

Personal message to Modi:
  Mentor: "mene dekha group me Rahul ki help ki"
  Mentor: "achchha laga"
```

### Example 6: Student is Sick

```
Student: "sir bimar hun"
  Mentor: "kya hua?"

Student: "bukhar he 2 din se"
  Mentor: "take care"
  Mentor: "pehle theek ho jao"

(4-5 days later):
  Mentor: "theek ho gaye?"

Student: "haan sir"
  Mentor: "achchha"
```

### Example 7: Night Activity

```
(Student was active at 1 AM)

Mentor (next day):
  "raat ko 1 baje bhi padh rahe the"
```

### Example 8: Mentor's Story

```
(Student is stuck on an assignment)

Mentor: "ye wala thoda tricky he"
Mentor: "jab mene ye kiya tha tab mujhe bhi same problem aayi thi"
Mentor: "ye try karo..."
```

### Example 9: Quiz in Group

```
Group:
  Mentor: "ek quiz ho jaye"
  Mentor: "10 questions, 5 minutes"
  (quiz link)

(After results):
  Mentor: "results"
  Mentor: "Modi - 9/10"
  Mentor: "Rahul - 8/10"
  Mentor: "Priya - 8/10"

Personal message to Modi:
  Mentor: "9/10"
  Mentor: "kaun sa galat hua usko dekh lena"
```

---

## 12. EDGE CASES & CRISIS PROTOCOL

### Crisis Situations (Immediate Real Mentor Alert)

**Student mentions self-harm / depression** — Immediately flag to real mentor + admin. AI says nothing.

**Student mentions abuse at home** — Immediately flag. AI does not attempt to respond.

**Student asks "Are you a bot?"** — Flag to real mentor. Mentor takes over.

**Student is angry / aggressive** — Flag to real mentor. AI does not argue.

**Student shares something deeply personal (trauma, loss)** — Flag to real mentor. AI is not equipped to handle this.

### Difficult Reply Situations

**Student always gives one-word replies** — Reduce message frequency. Try different message types. Send shorter messages.

**Student never replies but still does levels** — Don't push for replies. Keep sending light encouragement. The student is engaged, just not talkative.

**Student says "Stop messaging me"** — Stop personal messages immediately. Flag to real mentor. Continue only group messages.

**Student says messages are too frequent** — Reduce frequency. No sorry, no explanation — just send less. AI doesn't reply to this, it just internally adjusts the frequency.

**Student negatively compares with another student** — Never reveal who is "behind." Only positive comparisons. "You're in the top 20%" is fine. "You're behind Rahul" is NEVER acceptable.

---

## 13. SEASONAL & CULTURAL AWARENESS

### Exam Season (Usually March-April, Oct-Nov for some boards)

- Reduce nudging frequency to 1 message every 2-3 days
- Acknowledge exams: "exam season he, pehle wo karo"
- After exams: re-engagement push

### Festivals & Holidays

**Diwali, Eid, Christmas etc.** — Send a festival wish. No course nudges that day.

**Independence Day, Republic Day** — Can connect to course if it fits the mentor persona. Otherwise just wish.

**Summer/Winter break** — Opportunity for extra engagement.

### Regional Events

- Floods, natural disasters in the student's area → context-aware message
- Local events, festivals → reference them

### Weather/Time Awareness

- Monsoon season → don't push outdoor activities
- Winter mornings → don't message too early

---

## 14. EFFECTIVENESS MEASUREMENT

> How do we know if nudging is actually working?

### Student-Level Metrics

- **Levels completed after a nudge (within 24 hours)** — did the nudge motivate action?
- **Reply rate to AI messages** — is the student engaging with the "mentor"?
- **Time between nudge and next activity** — how quickly does a nudge convert to action?
- **Student retention (still active after 30/60/90 days)** — long-term effectiveness
- **Course completion rate** — the ultimate success metric
- **Re-engagement success rate** — did dropped students come back after nudges?

### Message-Level Metrics

- Which message types get replies — what resonates with students
- Which message types lead to activity — what drives action
- Message types that lead to "stop messaging" — what annoys students
- Optimal time of day for messages — when to send
- Optimal message frequency per student — how much is too much

### Group-Level Metrics

- Group activity level over time — is engagement growing or declining?
- Number of students helping others — community health
- Quiz participation rate — group engagement
- New member engagement after welcome — is the welcome flow working?

### A/B Testing (Phase 4)

- Test different nudge styles on similar student segments
- Test different message frequencies
- Test different message tones
- Test with and without human imperfections
- Measure which approach leads to better retention and progress

---

## 15. PRIVACY & ETHICAL BOUNDARIES

### What AI Should Remember

- Student's name, class, school, district
- Course progress and activity
- Promises made (for accountability)
- Reasons for inactivity (for follow-ups)
- Personal context shared by the student (for relationship)
- Preferences (best time, communication style)

### What AI Should NEVER Do

- Never share one student's personal info in the group or with other students
- Never shame a student publicly (all criticism is private, all praise can be public)
- Never make up information about the student
- Never diagnose health issues or give medical advice
- Never give financial advice or ask for money
- Never use personal info to manipulate ("your father is sick, study for him" — NEVER)
- Never share student data outside the platform

### Transparency Consideration

- If directly asked "Are you AI?", the real mentor takes over
- The team should have an internal ethics guideline about the AI-as-mentor approach
- Focus: AI is a tool that HELPS the mentor do their job better, not a replacement

---

## 16. QUALITY CONTROL & RISKS

### Risks & Mitigation

**AI sends wrong/inappropriate message** — Flag sensitive topics to real mentor. Have a review system.

**Over-messaging irritates students** — MAX 2 personal messages/day. Cooldown rules. Student can say "stop."

**Fake personal touch feels generic** — Mentor persona, message variation, human imperfections, no copy-paste.

**Bot gets detected** — Anti-detection rules, timing strategy, typing indicators, imperfections.

**Wrong context used (outdated info)** — Context refresh mechanism. Mentor notes override. Follow-up chains validate info.

**AI handles emotional situation poorly** — Immediate flag to real mentor for emotional/sensitive topics.

**Student becomes dependent on mentor (not self-driven)** — Gradually reduce frequency for advanced students. Build independence.

**Same nudge type stops working** — Rotate message types. Track effectiveness. Adapt.

### Quality Assurance Process

1. Every student gets a unique message — no template copy-paste
2. Strictly follow the mentor's persona
3. Enforce cooldowns — no over-messaging
4. Flagging mechanism must be robust and fast
5. Real mentor does a weekly spot check of AI conversations
6. Monthly analysis of flagged conversations to improve AI
7. Track student satisfaction signals (reply rate, sentiment)

---

## 17. PHASED ROLLOUT

### Phase 1 — Foundation (Quick Wins)

- Build mentor persona profiles (from 10-15 real messages)
- Basic triggers:
  - Onboarding message (welcome + personal questions)
  - Progress praise (daily)
  - Drop-off alert (2-3 days inactive)
  - Milestone celebration (Level 10, 20, 30...)
- Personal messages only, no group messages yet
- Simple reply handling (predefined responses for common situations)
- Reactions on student messages (thumbs up etc.)
- Basic student profile (name, activity data)
- Timing: message during student's active hours + mentor's hours only

### Phase 2 — Personalization Layer

- Follow-up chains (exam follow-up, "I'll start tomorrow" follow-up)
- Personal context memory (remember family, exams, etc.)
- Peer comparison engine (district/school level)
- Add group messages (shoutouts, weekly top performers, welcome messages)
- Student reply handling (AI direct answers + graceful exit after 3 messages)
- Level-based tips
- Quiz challenges (personal + group)
- Message splitting + human imperfections
- Streak tracking
- Weekly summary

### Phase 3 — Advanced

- Sentiment analysis on student replies
- Full mentor dashboard (handoff system)
- Proactive help at known stuck points
- Course-related external content sharing (YouTube, docs, news)
- Regional/local event awareness
- Voice notes integration (pre-recorded mentor voice at milestones)
- "Mentor's story" sharing
- Mentor class reminders
- Student segmentation (different strategies for different types)
- Buddy system / peer pairing
- Birthday wishes
- Relationship depth tracking (adjust tone over time)
- "Mentor's day off" pattern

### Phase 4 — Scale & Optimize

- Per-course customization (different nudge strategies per course type)
- Regional language support
- A/B testing different nudge styles
- Effectiveness tracking (retention impact, activation rate)
- Voice cloning — audio messages in the mentor's actual voice
- World events integration
- Student goal-setting & tracking features
- Group competition / inter-group challenges
- Advanced group dynamics management
- Course completion celebration & next course recommendation
- Alumni success stories as motivation
- Student feedback collection

---

## 18. MENTOR-GROUP ASSIGNMENT (Open Decision)

3 options being considered:

**Option 1: Mentor assigned on group join** — Student gets a mentor when they join a group. Simple and consistent. But what if the student changes groups?

**Option 2: Mentor at start, group mentor different** — Mentor is assigned at enrollment, but the group has a different mentor. Personal relationship starts early. But confusing — 2 mentors?

**Option 3: Mentor at start, same-mentor groups** — Students with the same mentor are placed in the same group. Consistent experience. But group composition becomes limited by mentor assignment.

> Decision needed before Phase 1.

---

## Summary: Key Numbers

- **Students per mentor:** ~500
- **Cohorts per mentor:** 5 (100 each)
- **Real mentor time per month:** 5 hours (calls)
- **AI vs Human interaction:** 90% AI, 10% real mentor
- **Max personal messages per student per day:** 2
- **Max group messages per day:** 3-4
- **AI back-off after real mentor replies:** 24 hours
- **Random delay on messages:** 2-5 minutes
- **Typing indicator before send:** 3-5 seconds
- **Graceful exit after:** 3+ back-and-forth messages
- **Drop-off alert threshold:** 2-3 days inactive
- **Escalation to real mentor:** After 2 unanswered nudges
