# 词博士 (Ci Boshi) — English Vocabulary Master

## 1. Concept & Vision

**产品定位**: A phrase-based vocabulary learning app for China junior high students (初中生), focused on 中考 vocabulary aligned with 外研社 (Foreign Language Teaching & Research Press) textbooks. Unlike rote word-list apps, we teach *words in context* — phrases, collocations, and sentence patterns — because this is how vocabulary actually transfers to listening, speaking, reading, and writing.

**Slogan**: "记词根，会用法，中考得高分"

**Target**: Junior high students (Grade 7-9), ages 12-15, preparing for 中考 (High School Entrance Exam). Parents pay for the subscription.

**Core Learning Philosophy**:
- **Phrase-first**: "take an apple" > "apple = 苹果"
- **Retrieval practice**: test yourself, don't just re-read
- **Spaced Repetition (SRS)**: smart intervals based on forgetting curve
- **Multimodal**: listen (pronunciation), see (text + image), produce (speak/write)
- **Four skills integrated**: vocabulary → listening → speaking → reading → writing

---

## 2. Design Language

### 2.1 Visual Identity

**Color Palette**:
- Primary: `#FF6B35` (warm orange — energetic, youthful, distinct from 扇贝 blue / 百词斩 green)
- Secondary: `#004E89` (deep blue — academic trust, contrast)
- Accent: `#F7C948` (yellow — highlights, streaks, achievements)
- Background: `#FAFAFA` (off-white — easy on eyes for study)
- Card Background: `#FFFFFF`
- Text Primary: `#1A1A2E`
- Text Secondary: `#6B7280`
- Success: `#10B981`
- Error: `#EF4444`

**Typography**:
- Chinese: "PingFang SC", system-ui
- English: "Inter", sans-serif (Google Fonts)
- Numbers/Stats: "JetBrains Mono" (monospace for counts/streaks)
- Font sizes: 14px body, 18px card titles, 24px headings, 48px big numbers

**Spatial System**:
- Base unit: 8px
- Card padding: 16px
- Section gap: 24px
- Border radius: 12px (cards), 8px (buttons), 24px (pills/badges)

**Motion Philosophy**:
- Micro-interactions: 150ms ease-out (button press, toggle)
- Card transitions: 300ms ease-in-out (flip, slide)
- Page transitions: 250ms fade
- Success/error feedback: 200ms with scale pulse (1.0 → 1.05 → 1.0)
- No gratuitous animation — every motion communicates state

### 2.2 UI Components

**Flashcard**:
- Front: English word + phonetic transcription + speaker icon
- Back: Chinese translation + phrase(s) + example sentence
- Tap to flip (3D flip animation)
- Swipe right = know it / Swipe left = still learning
- States: default, flipped, correct (green glow), incorrect (red glow)

**Progress Ring**:
- Circular progress showing daily/weekly goal completion
- Center shows fraction (e.g., "12/20")

**Streak Badge**:
- Fire emoji + day count
- Animated pulse when streak increases
- Parent notification if streak breaks

**Leaderboard Item**:
- Rank number, avatar, nickname, word count, streak
- Highlight current user

**Sound Button**:
- Animated speaker icon while playing
- Replay button after playing

**Pronunciation Score**:
- Circular gauge 0-100
- Color coded: red (<60), yellow (60-80), green (>80)

---

## 3. Layout & Structure

### 3.1 App Architecture

```
首页 (Home)
├── 今日学习 (Today's Review)
│   ├── Flashcard Stack (SRS queue)
│   └── Progress Ring
├── 学习统计 (Stats)
│   ├── Words learned
│   ├── Accuracy rate
│   └── Streak
└── 发现 (Discover)
    └── 教材同步 (Textbook Sync)

学习 (Learn) — Tab 2
├── 听说 (Listening & Speaking)
│   ├── 听力练习 (Listening)
│   └── 口语练习 (Speaking)
├── 阅读 (Reading)
│   └── Reading comprehension
└── 写作 (Writing)
    └── Sentence writing practice

词库 (Word Bank) — Tab 3
├── 中考词汇 (1600 words)
├── 教材同步 (外研社 texts)
│   ├── 七年级上/下 (初一)
│   ├── 八年级上/下 (初二)
│   └── 九年级上/下 (初三)
└── 我的生词本 (Favorites)

我的 (Profile) — Tab 4
├── 学习报告 (Progress Report)
├── 设置 (Settings)
└── 家长模式 (Parent Mode)
```

### 3.2 Screen Flow

1. **Onboarding**: Select grade → Select textbook → Placement test (10 words) → Daily goal setting
2. **Daily Learning**: Open app → Review SRS queue → Learn new words (10/day) → Complete daily goal
3. **Practice Mode**: Choose skill → Complete exercises → Get score
4. **Parent Dashboard**: View child's progress → Get notifications

---

## 4. Features & Interactions

### 4.1 Core Features (MVP)

**F1: 智能背词 (Smart Vocabulary Review)**
- SM-2 algorithm for spaced repetition
- Each word appears at optimal recall interval
- User rates: "Again" / "Hard" / "Good" / "Easy" → adjusts next interval
- Daily queue: review + new words
- Minimum interval: 1 day, max: 365 days

**F2: 短语卡片 (Phrase Cards)**
- Each vocabulary word comes with 2-3 common phrases
- Example: "achieve" → "achieve success", "achieve one's goal", "achieve great progress"
- Phrases are the primary learning unit, not isolated words
- Audio for each phrase

**F3: 听力练习 (Listening Practice)**
- Play phrase/sentence audio
- Multiple choice or fill-in-blank
- Progressive difficulty (word → phrase → sentence → paragraph)
- Tracks accuracy per student

**F4: 口语练习 (Speaking Practice)**
- Listen to phrase
- Record yourself repeating
- Simple pitch/timing comparison (or AI scoring if feasible)
- No native speaker required — self对比

**F5: 教材同步 (Textbook Sync)**
- 外研社 Junior High English (Go for it! / 2024 new standard)
- Units organized by grade and semester
- Students see words in textbook order (familiar to them)
- Teachers/parents can assign unit homework

**F6: 打卡 Streak & Gamification**
- Daily login + complete review → streak++
- Streak freeze (1 per week)
- Weekly leaderboard (class/school/city)
- Badges: "3天 streak", "7天", "30天", "100天"
- Parent notification on streak break

**F7: 学习报告 (Progress Report)**
- Weekly summary: words learned, accuracy, time spent
- Weak words: frequently forgotten
- Parent view: child's progress vs class average
- Exportable as shareable image (for 朋友圈)

### 4.2 User Interactions

**Flashcard Flow**:
1. Card shows English word + speaker icon
2. Tap speaker → plays pronunciation + phrase audio
3. Tap card → flips to show Chinese + phrase + example sentence
4. Swipe right (know) or left (don't know) or tap buttons
5. Rate difficulty → SRS interval updates
6. Next card appears

**Listening Flow**:
1. Select unit/level
2. Listen to audio (phrase or sentence)
3. Choose answer or type what you heard
4. Instant feedback with correct answer
5. Score accumulated

**Speaking Flow**:
1. See phrase text + listen
2. Press and hold microphone
3. Record your pronunciation
4. Playback comparison
5. Self-rate or get AI score (future)

### 4.3 Edge Cases & Error Handling

- **Offline**: Cache today's cards locally; sync when online
- **Empty state (no words to review)**: "今日任务已完成! 🎉 明天再来"
- **Audio fails**: Show text fallback, retry button
- **Parent mode**: PIN protected, separate UI for adults
- **Wrong answer streak**: If user fails same word 3x → add to "hard words" list

---

## 5. Component Inventory

### 5.1 Core Components

| Component | States | Behavior |
|-----------|--------|----------|
| FlashCard | default, flipped, swiping-left, swiping-right, correct, incorrect | 3D flip on tap, swipe gesture |
| ProgressRing | empty, partial, complete | Animates on load and update |
| StreakBadge | active, broken, new-record | Pulse animation on increment |
| AudioButton | idle, playing, error, loading | Spinner while loading, bounce on play |
| LeaderboardRow | normal, highlighted (self), top-3 | Highlight self in accent color |
| StatCard | default | Counter animation on load |
| PhrasePill | default, playing | Speaker icon, tap to play |
| Button | default, pressed, disabled, loading | Scale down 95% on press |
| TabBar | default, active | Active has primary color + label |
| Input | default, focused, error, success | Border color change |

### 5.2 Screen Layouts

**Home Screen**:
- Top: Greeting + streak badge + settings
- Center: Large progress ring + today's count
- Middle: Today's new words preview (3 cards peek)
- Bottom: CTA button "开始学习" + Tab bar

**Learn Screen**:
- Flashcard stack centered
- Bottom: Swipe hints + difficulty buttons
- Top right: Exit/X button

**Stats Screen**:
- Weekly chart (bar chart of daily words learned)
- Key metrics: Total words, accuracy %, streak, time
- Weak words list (top 10)

**Word Bank Screen**:
- Search bar
- Segmented control: 中考词汇 | 外研社教材
- Word list (alphabetical or by unit)
- Each row: word, phonetic, master level indicator

---

## 6. Technical Approach

### 6.1 Stack

**WeChat Mini Program**:
- WeChat developer tools
- WXML + WXSS + JS (native framework)
- No external UI framework (keep lightweight)

**Backend** (for MVP, keep minimal):
- **LeanCloud** or **WeChat Cloud** (low cost, fast setup)
- User auth, progress sync, leaderboard
- SRS algorithm (can run client-side for MVP)

**Audio**:
- Use free TTS (e.g., Google TTS API, or 腾讯云TTS) for MVP
- Later: professional recordings for key phrases

**Content**:
- Scraper or manual entry for 外研社 vocabulary
- 1600 中考 words with phrases and example sentences
- Stored as JSON, loaded at runtime

### 6.2 Data Model

```
User
  - openid (WeChat unionid)
  - grade (7/8/9)
  - selected_textbook
  - daily_goal (default: 20)
  - streak (int)
  - streak_frozen (bool)
  - created_at

Word
  - id
  - word (string)
  - phonetic (string, IPA or KK)
  - translation (string)
  - phrases: [{phrase, audio_url}]
  - examples: [{sentence, audio_url}]
  - unit_id (for textbook sync)

UserWordProgress
  - user_id
  - word_id
  - ease_factor (float, SM-2)
  - interval (int, days)
  - repetitions (int)
  - next_review_date
  - last_reviewed_at
  - times_correct
  - times_incorrect

DailyRecord
  - user_id
  - date
  - new_words_learned
  - words_reviewed
  - accuracy_rate
  - time_spent_seconds
```

### 6.3 Key Algorithms

**SM-2 Spaced Repetition**:
```
After each review:
- If quality < 3 (failed): interval = 1, repetitions = 0
- If quality >= 3 (passed):
  - If repetitions == 0: interval = 1
  - If repetitions == 1: interval = 6
  - Else: interval = interval * ease_factor
  - repetitions++

ease_factor = max(1.3, ease_factor + (0.1 - (5-quality) * (0.08 + (5-quality) * 0.02)))
```

**Daily Queue**:
1. Fetch all words where next_review_date <= today → review pile
2. Fetch new_words_learned_today < daily_goal → new words (limit: daily_goal - already_learned)
3. Shuffle review pile, append new words to end
4. Present 20 cards max per session

---

## 7. Content — 外研社 Vocabulary

### 7.1 外研社 Junior High (英语 — Go for it! / 新标准)

The official 外研社 junior high English series (2024 new curriculum) has:
- **七年级上/下**: ~600 new words
- **八年级上/下**: ~700 new words
- **九年级上/下**: ~500 new words
- **Total**: ~1800 words (covers and exceeds 1600 中考 words)

For MVP, we focus on:
- 中考核心1600词 (compiled from public 中考大纲)
- These map to 外研社 units for textbook sync

### 7.2 Word Data Structure

```json
{
  "id": "word_0001",
  "word": "achieve",
  "phonetic": "/əˈtʃiːv/",
  "translation": "v. 达到；完成；实现",
  "grade": 8,
  "unit": 1,
  "phrases": [
    {"phrase": "achieve success", "translation": "取得成功", "audio": "achieve_success.mp3"},
    {"phrase": "achieve one's goal", "translation": "实现目标", "audio": "achieve_ones_goal.mp3"},
    {"phrase": "achieve great progress", "translation": "取得很大进步", "audio": "achieve_great_progress.mp3"}
  ],
  "examples": [
    {"sentence": "Hard work achieves success.", "translation": "努力工作就能成功。"},
    {"sentence": "She achieved her goal of losing weight.", "translation": "她实现了减肥的目标。"}
  ]
}
```

---

## 8. Go-to-Market Strategy

### 8.1 Social Media Channels

| Platform | Content Type | Goal | Priority |
|----------|-------------|------|----------|
| 小红书 (Red Note) | Study tips, parent testimonials, streak screenshots | Awareness, viral | ★★★★★ |
| 微信 (WeChat) | Mini program, parent groups, 朋友圈 | Distribution, retention | ★★★★★ |
| 抖音/视频号 | Short videos: "3分钟学会20个中考词" | Awareness | ★★★★ |
| 大众点评 | Parent groups, education categories | Local awareness | ★★★ |
| B站 | Learning compilations, study-with-me | Engagement | ★★★ |
| 知乎 | SEO article: "中考英语词汇备考攻略" | SEO, authority | ★★ |

### 8.2 Launch Phases

**Phase 1 (Month 1-2): 验证期**
- Landing page + WeChat group for early users
- Target: 100-200 early adopters via 小红书 posts
- Goal: validate retention and DAU metrics

**Phase 2 (Month 3-4): 口碑期**
- Refine product based on feedback
- Encourage sharing (streak screenshot → 朋友圈)
- Target: 500-1000 active users
- Start parent WeChat groups for testimonials

**Phase 3 (Month 5-6): 增长期**
- Seed in parent communities (中考志愿群, 家长帮)
- Consider 小红书 KOL collaboration
- Offer class/school leaderboard for viral
- Target: 3000-5000 active users

**Phase 4 (Month 7+): 变现期**
- Introduce subscription (¥58/月 for full features)
- Free: 20 words/day limit
- Paid: unlimited + 口语AI + 家长报告

---

## 9. MVP Scope (What to Build First)

### 9.1 Phase 1 MVP (2-3 weeks)

**Must Have**:
- WeChat Mini Program shell (tab navigation)
- Flashcard UI (front/back flip)
- SRS algorithm (client-side, no backend)
- 200 中考高频词 with phrases (seed data)
- Audio playback (TTS)
- Daily progress ring
- Streak counter
- Local storage (user progress persists)

**Nice to Have**:
- Parent mode PIN
- Leaderboard
- Data export

### 9.2 Phase 2 MVP (Week 4-6)

- Full 1600 词库
- 教材同步 (外研社 units)
- Listening exercises
- Stats/progress report page
- Cloud sync (LeanCloud)

---

## 10. Success Metrics

| Metric | Target (Month 1) | Target (Month 3) |
|--------|-----------------|-----------------|
| DAU | 50 | 500 |
| D30 Retention | 20% | 30% |
| Daily words reviewed (avg) | 15 | 20 |
| D7 Retention | 35% | 45% |
| Parent satisfaction | 4/5 | 4.5/5 |

**North Star**: 30-day recall accuracy ≥ 75% (user remembers word after 30 days)