# AI Nudging Engine Strategy

## Core Principle: "Invisible AI, Visible Mentor"

Student ko kabhi pata nahi chalna chahiye ki AI bol raha hai. Har message esa lage jaise mentor ne personally socha aur likha.

---

## 1. MENTOR PERSONA BUILDING

**Problem:** AI ka message robotic lagta hai
**Solution:**

- Jab real mentor onboard ho, uske **10-15 real messages collect karo** (WhatsApp/chat history se)
- Uski **style capture karo**: kya wo "bhai" bolta hai ya "yaar"? Hindi me likta hai ya Hinglish? Emoji use karta hai ya nahi? Lambe messages bhejta hai ya chhote?
- Har mentor ka ek **persona profile** banao:
  - Tone (casual/formal)
  - Language (Hindi/Hinglish/English)
  - Common phrases ("dekh bhai", "chal koi nahi", "mast!")
  - Emoji habits
  - Message length preference
  - Active hours (raat ko bolte hai ya subah?)

**Result:** AI us mentor ki style me likhe, student ko difference na pata chale

---

## 2. MESSAGE TIMING STRATEGY

**Problem:** AI message galat time pe bheje to fake lagega
**Solution:**

- **Student ka active time track karo** - jab wo app kholte hai, group me type karte hai
- **Mentor ke natural hours me hi bhejo** - agar mentor raat 11 baje ke baad kabhi online nahi aata, to AI bhi 11 ke baad na bheje
- **Random delay rakho** - exact intervals pe message aaye to bot lagega. 2-5 min ka random delay har message me
- **Typing indicator dikhao** - message bhejne se pehle 3-5 sec ka "typing..." dikhao (bohot important for realism)
- **Read receipts ka smart use** - mentor ne message "dekha" 10 min pehle lekin reply 10 min baad aaya - ye human behavior hai

---

## 3. NUDGE CATEGORIES & TRIGGERS

Har nudge ka ek **trigger**, **template**, aur **cooldown** hona chahiye:

| Category                | Trigger                           | Example                                                                 | Cooldown      |
| ----------------------- | --------------------------------- | ----------------------------------------------------------------------- | ------------- |
| **Progress praise**     | Student ne 3+ levels ek din me ki | "bhai aaj to tune 4 levels maar diye, kal se jyada ki aaj"              | 1/day         |
| **Drop-off alert**      | 2 din se inactive                 | "kya hua bhai? 2 din se dikhaa nahi.. sab theek?"                       | 3 days        |
| **Comeback push**       | Student ne reason diya (exam etc) | "exam kab khatam ho rahi? fir wapas aate hai full power se"             | context-based |
| **Peer comparison**     | Student top 20% me                | "tu apne district me top 5 me aa gaya hai bhai"                         | 1/week        |
| **Group shoutout**      | Student ne kisi ki help ki        | Group me: "@Modi ne @Rahul ki doubt solve ki, ye dekho mentor material" | per event     |
| **Milestone celebrate** | Level 10, 20, 30 etc              | "50 levels done! 80% log yahan tak nahi pahuchte"                       | per milestone |
| **Night owl**           | Late night active                 | "bhai 1 baje bhi padh raha hai? dedication"                             | 1/week        |
| **Quiz challenge**      | Har 10 levels                     | "10 levels ho gaye, ek quick quiz? dekhte hai kitna yaad hai"           | per milestone |
| **Re-engagement**       | Student ne bola "kal se karunga"  | Next day: "aaj ka din hai bhai, kal bola tha na?"                       | 1 follow-up   |

**Important:** Ek student ko ek din me MAX 2 personal messages. Zyada hua to annoying lagega.

---

## 4. HUMAN-LIKE IMPERFECTIONS (Sabse Important)

AI ko **perfect nahi** hona chahiye. Real humans:

- **Typo karte hain kabhi kabhi** - "tumnhe" instead of "tumhe" (controlled, rare)
- **Message split karte hain** - ek lambi message ki jagah 2-3 chhoti:
  ```
  "bhai dekha maine"
  "aaj 2 hi levels ki tune"
  "kal to 4 ki thi na"
  ```
- **Late reply karte hain** - har message ka instant reply nahi aata
- **Context bhoolte hain kabhi** - "haan wo tumne bataya tha... exam thi na?"
- **Casual start karte hain** - "are haan" "achha sun" "btw"
- **Voice notes occasionally** - pre-recorded mentor voice notes key milestones pe (real mentor se record karwa lo 10-15)

---

## 5. GROUP vs PERSONAL MESSAGE STRATEGY

**Group me (public, sab dekhein):**

- Weekly top performers announce
- Quiz challenges
- Student ki help ko appreciate
- Milestones celebrate
- "aaj ka challenge" type posts

**Personal me (1:1, private):**

- Drop-off alerts
- Personalized progress feedback
- Exam/break follow-ups
- Tips based on level
- Sensitive topics (struggling student)

**Rule:** Group me positive, Personal me supportive. Kabhi group me shame mat karo.

---

## 6. CONVERSATION HANDLING (Jab Student Reply Kare)

Ye sabse tricky part hai:

```
Flow:
AI bheje -> Student reply kare -> ???

Option A: AI reply kare (risky - zyada conversation = zyada chance of getting caught)
Option B: "seen" kare, reply na kare (natural - mentor busy hai)
Option C: Short reply de aur close kare ("haan bilkul, keep going")
```

**Strategy:**

- **Simple replies** (thanks, ok, haan): AI handle kare with short response
<!-- - **Personal/emotional replies** (demotivated, family issues): **FLAG to real mentor** - yahan real human chahiye -->
- **Suspicious replies** ("kya tu bot hai?"): Immediately flag to real mentor
- **Long conversations (3+ back-and-forth)**: Graceful exit - "achha bhai mujhe ek aur group ka session lena hai, baad me baat karte hai"

---

## 7. REAL MENTOR + AI HANDOFF

```
Normal flow:    AI 90% <-> Student
Flagged:        AI -> Real Mentor notification -> Real Mentor takes over
After call:     Real Mentor notes -> AI picks up context
```

- Real mentor ko ek **dashboard** do jisme:
  - Kon se students ko AI ne message kiya
  - Student ke replies ka summary
  - Flagged conversations (need human attention)
  - One-click takeover (mentor khud reply kare)
- Jab real mentor khud reply kare, AI **24 hour ke liye back off** kare us student se
- Monthly call ke baad, mentor notes daale: "Modi ne bola exam hai March me" -> AI March me follow-up karega

---

## 8. DATA SIGNALS TO TRACK

| Signal                    | Source | Use                           |
| ------------------------- | ------ | ----------------------------- |
| Levels completed per day  | App    | Progress nudges               |
| Last active timestamp     | App    | Drop-off detection            |
| Group message count       | Group  | Help appreciation             |
| Quiz scores               | App    | Difficulty-based tips         |
| Reply sentiment           | Chat   | Flag negative sentiment       |
| Student's stated schedule | Chat   | "exam hai", "kal se" tracking |
| Peak active hours         | App    | Optimal message timing        |
| Course enrolled           | App    | Relevant content sharing      |

---

## 9. ANTI-DETECTION RULES

1. **Kabhi 2 students ko same minute me message mat bhejo** - human ek time pe ek ko likhta hai
2. **Weekend pe frequency kam karo** - mentor bhi rest karta hai
3. **Festival/holidays pe break lo** - Diwali pe mentor message nahi karega
4. **Har student ko slightly different message** - same template copy-paste mat karo
5. **Mentor ke real messages ke beech AI messages fit karo** - agar mentor ne subah 10 baje real message kiya, to AI dopahar 3 baje bheje, seamless lagega
6. **Kabhi kabhi "galti se" wrong student ka naam likh do aur turant correct karo** - "Rahul... sorry Modi, tere liye tha ye" (rare, but very human)

---

## 10. ROLLOUT PLAN

**Phase 1 - Foundation:**

- Mentor persona profiles banao
- Basic triggers setup (progress praise, drop-off alert)
- Personal messages only, group nahi

**Phase 2 - Expand:**

- Group messages add karo (shoutouts, quizzes)
- Peer comparison engine
- Student reply handling

**Phase 3 - Advanced:**

- Sentiment analysis on replies
- Real mentor handoff system
- Voice notes integration
- "Mentor ne galti ki" type human imperfections

**Phase 4 - Scale:**

- Per-course customization
- Regional language support
- A/B testing different nudge styles
- Effectiveness tracking (nudge ke baad kitne students active hue)

---
