# Conversation Summary: LingoFlip MVP Product Requirements Document Planning

## <decisions>

### Business Model & Monetization
1. **Freemium model adopted** - Free tier with limitations, premium tier available on request
2. **Free tier limits**: 20 AI word generations, 8 audio-file based generations, 100 manual cards per month
3. **Premium upgrade path**: When limits reached, user redirected to contact page with pre-filled email form to request premium plans
4. **User limit**: Maximum 50 concurrent users for initial MVP phase
5. **Cost target**: Maximum $0.05 API cost per user per month

### AI Services & Technology
6. **AssemblyAI** selected for Speech-to-Text conversion
7. **Google Cloud Text-to-Speech** for audio pronunciation by native speakers
8. **Google Cloud Translation API or DeepL** for flashcard translation (recommended, user agreed)
9. **Technology stack explicitly out of scope** for PRD - to be decided during implementation phase

### Learning Algorithm
10. **FSRS (Free Spaced Repetition Scheduler)** chosen over SM-2 for 20-30% better accuracy
11. **Default FSRS parameters** for all users initially, with logging for future personalization
12. **Cards remain in rotation indefinitely** with increasingly longer intervals for mastered cards
13. **Total card limit**: 10,000 cards per user (no archiving needed)
14. **Monthly card limit**: 500 new cards per month across all sources

### Language Support
15. **10 foreign languages supported**: Spanish, Mandarin Chinese, French, German, Japanese, Italian, Polish, Portuguese, Korean, Arabic
16. **2 native/application languages**: English (default) and Polish
17. **Three language pairs per user** in free tier (e.g., Polish-Italian, Polish-English, Polish-Arabic)
18. **Native language locked** to application language selected at registration - cannot be changed without new account
19. **Each language pair maintains separate** flashcard collections and learning progress

### Authentication & Security
20. **Password requirements**: Minimum 16 characters with uppercase, lowercase, numbers, and special symbols
21. **Password reset**: Via email with time-limited reset link (valid 1 hour)
22. **Email verification required** before platform access - no unverified logins allowed
23. **Unverified accounts deleted** after 24 hours automatically
24. **Simple authentication** - no OAuth, no two-factor authentication for MVP
25. **No security questions** - email-only password recovery

### User Onboarding & Registration
26. **Registration fields**: Email, Password, Confirm Password, Application Language (English/Polish), Initial foreign language (dropdown of 10), Optional motivation field (300 chars max), Terms acceptance checkbox
27. **Onboarding flow**: One-page summary → select foreign language → create first flashcard set → first learning session
28. **Onboarding shown once** - flag stored to skip on subsequent logins
29. **Immediate post-login flow**: Onboarding summary → language selection → flashcard creation prompt → first learning session

### Flashcard Creation Methods
30. **Three creation methods**: AI-generated default words, audio file analysis, manual entry
31. **AI default word sets**: Most common words by frequency, user specifies quantity (default 50 words)
32. **Audio file requirements**: MP3 or M4A format, maximum 30MB, no fallback mechanism
33. **Audio analysis limits**: 8 uploads per month, must produce 30+ words or warning shown
34. **Audio word extraction**: Top 50 most frequently used words from recording
35. **Manual flashcard creation**: Unlimited in concept, 100/month in free tier
36. **Word types included**: Nouns, verbs, adjectives, adverbs, pronouns only

### AI Content Quality & Feedback
37. **Accept/reject mechanism**: Users preview AI-generated sets before acceptance
38. **Rejected sets count toward monthly limit** to prevent infinite API cost exploitation
39. **Report issue button**: Simple form with issue type dropdown and optional text (200 chars)
40. **Report applies to entire set**, not individual cards
41. **No fallback mechanisms** - user must provide better audio or accept results

### Learning Mechanics & UX
42. **Swipe mechanics**: Left = incorrect answer, Right = correct answer (Quizlet-style)
43. **Incorrect cards**: Return to review queue in same session, FSRS resets difficulty
44. **Card flipping**: Click on card surface to flip
45. **Audio autoplay**: Default ON, configurable in settings
46. **Keyboard navigation**: Spacebar to flip, arrow keys to swipe
47. **Hard/good/easy options**: Out of MVP scope, planned for future releases
48. **Sentence context feature**: Removed from MVP scope (too complex and costly)

### Daily Goals & Story Generation
49. **Daily goal**: Review 20 cards correctly (not just view them)
50. **Daily story generation**: Available as FREE tier feature after reaching daily goal
51. **Story requirements**: 100-150 words, beginner level (A1-A2 CEFR), uses 20 correctly answered words
52. **Story complexity**: AI instructed to use simplest possible words (5-year-old level)
53. **Story can include additional simple words** beyond the 20 learned words
54. **Story lifecycle**: Generated → displayed with audio playback → deleted when user closes
55. **No story history storage** - keeps things simple and reduces storage costs

### User Settings & Preferences
56. **Daily card limit**: Configurable, default 20 cards
57. **Native language**: Displayed but not configurable (locked at registration)
58. **Foreign language selector**: Dropdown to switch between configured language pairs
59. **Audio autoplay toggle**: ON/OFF, default ON
60. **No notification settings** for MVP
61. **No sentence context toggle** (feature removed from MVP)

### Statistics & Progress Tracking
62. **Simple statistics page**: Current streak, total words, words due today, words learned (10+ reviews), monthly limit usage, account creation date
63. **In-app notification**: Shows streak count and cards due when user logs in
64. **No email reminders** for MVP
65. **No fancy charts or plots** - simple numbers and progress bars only
66. **Statistics shown for active language pair only**

### Flashcard Library Management
67. **Library view**: Scrollable list with search, filter, and sort capabilities
68. **Search**: By word text
69. **Filter options**: By source (AI/manual/audio-based), by mastery level (new/learning/mastered)
70. **Sort options**: By creation date or next review date
71. **Per-card actions**: Edit and delete buttons for each card
72. **No complex tagging system** for MVP

### Privacy & GDPR Compliance
73. **Audio file deletion**: Files removed immediately after Speech-to-Text operation completes
74. **Flashcard data retention**: Stored as long as user account exists
75. **Application logs**: Removed after 3 months
76. **Data export**: CSV file with all flashcards and review history via "Export my data" button
77. **Account deletion**: "Delete account" option with confirmation, permanent removal within 48 hours
78. **Simplest possible GDPR approach** - basic compliance without complex mechanisms

### Performance & Scalability
79. **Maximum 50 concurrent users** for MVP
80. **Page load time**: Under 5 seconds
81. **Flashcard flip/swipe response**: Under 160ms
82. **Uptime target**: 80% (not commercial-grade)
83. **No retry attempts for API failures** - just show error message

### Error Handling
84. **API failure handling**: User-friendly error message, log technical details, don't deduct from monthly limit if generation fails
85. **Audio analysis failure**: Warning if <30 words found, inform user to provide longer/clearer recording

### Testing & Quality Assurance
86. **Unit tests**: Core functions (FSRS algorithm, flashcard CRUD operations)
87. **Integration tests**: AI API calls with mock responses
88. **Code coverage target**: 80% for business logic
89. **No E2E testing required** for MVP (hobbyist project)
90. **Manual testing**: Performed separately, out of PRD scope

### Browser Compatibility & Accessibility
91. **Supported browsers**: Latest versions of Chrome, Firefox, Safari, Edge
92. **No IE11 support**
93. **Mobile-responsive design**: Tablets and phones (no native app)
94. **Minimum screen width**: 320px
95. **Audio requirements**: Modern browser with Web Audio API support
96. **Basic accessibility**: Keyboard navigation, color contrast, alt text, semantic HTML
97. **No full WCAG 2.1 AA compliance** for MVP (future enhancement)

### Admin Panel
98. **Admin access required**: Password-protected separate URL
99. **Admin features**: Current user count, recent registrations, API usage statistics, error logs (last 100), manual account deletion capability
100. **Purpose**: Manage 50-user cap and troubleshoot issues

### Project Scope Clarifications
101. **Hobbyist project** - not commercial initially, no strict timeline
102. **Development timeline**: No fixed deadline required
103. **Heavy testing not required** - basic testing sufficient for non-commercial MVP

## <matched_recommendations>

### Accepted Recommendations (User Agreement)

1. **Freemium business model** - Free features to attract users, premium features for later monetization
2. **Google Cloud Translation API or DeepL** for high-quality translations within budget
3. **FSRS algorithm implementation** for 20-30% better accuracy than SM-2
4. **10 foreign languages**: Spanish, Mandarin Chinese, French, German, Japanese, Italian, Polish, Portuguese, Korean, Arabic
5. **Audio specifications**: MP3/M4A formats, 30MB limit, no fallback for poor quality
6. **Simple authentication** without OAuth or 2FA for MVP simplicity
7. **GDPR compliance basics**: Data export, account deletion, clear retention policies
8. **Password reset flow**: Email with time-limited link, no security questions
9. **Onboarding sequence**: Summary → language selection → card creation → first session
10. **Simple feedback system**: Report button with issue type selection and optional text
11. **Progress visualization**: Simple numbers and progress bars, no complex charts
12. **Freemium tier limits**: 20 AI generations, 8 audio uploads, 100 manual cards monthly
13. **Upgrade contact mechanism**: Pre-filled email form when limits reached
14. **FSRS default parameters** with logging for future personalization
15. **One active language pair** with ability to switch between three configured pairs
16. **Flashcard library features**: Search, filter by source/mastery, sort by date
17. **Email verification required** before platform access
18. **Admin panel** for monitoring 50-user limit and system health
19. **API failure handling**: User-friendly messages, technical logging
20. **Browser support**: Modern browsers only, no legacy support
21. **Basic accessibility**: Keyboard navigation, contrast, semantic HTML
22. **Testing approach**: Unit tests, integration tests with mocks, 80% coverage
23. **Daily story generation**: 100-150 words at beginner level with audio playback
24. **Registration fields**: Email, password, language selections, optional motivation
25. **Statistics display**: Streak, totals, due cards, monthly limits

### Modified Recommendations (User Adjustments)

26. **Technology stack excluded from PRD** - Will be decided during implementation (originally recommended to specify)
27. **Daily story as FREE feature** instead of premium-only
28. **Story deleted immediately** after viewing instead of 7-day history
29. **Swipe direction**: Left=incorrect, Right=correct (opposite of Tinder reference)
30. **Daily goal requires 20 CORRECT answers** not just 20 reviews
31. **Three language pairs allowed** instead of single active language
32. **Native language locked** at registration, cannot be changed
33. **No retry attempts for API failures** instead of 3 retries with exponential backoff
34. **500 cards monthly limit** instead of unlimited manual cards
35. **10,000 total card limit** without archiving feature
36. **Email verification blocks login** instead of allowing access with banner
37. **Unverified accounts deleted after 24 hours** instead of 30 days
38. **Report applies to entire set** before acceptance, not individual cards
39. **Rejected sets count toward limit** to prevent cost exploitation
40. **80% uptime sufficient** for hobbyist project instead of 99.5%
41. **5-second page load acceptable** instead of <2 seconds
42. **160ms swipe response** instead of <100ms
43. **Registration includes foreign language selection** to streamline onboarding
44. **300-character motivation field** added to registration
45. **Contact via dedicated page** instead of email link directly

### Rejected Recommendations (Features Removed from MVP)

46. **Sentence context feature** - Too complex and costly for MVP
47. **Email reminders** - No notification system for MVP
48. **OAuth integration** - Simple authentication only
49. **Two-factor authentication** - Not needed for hobbyist project
50. **E2E testing** - Manual testing sufficient for MVP
51. **99.5% uptime SLA** - 80% acceptable for non-commercial
52. **Hard/good/easy options** - Simple binary correct/incorrect only
53. **Story history (7 days)** - Deleted immediately after viewing
54. **Premium-only story generation** - Available in free tier
55. **Card archiving feature** - Not needed with 10,000 card limit

## <prd_planning_summary>

### Product Overview
LingoFlip is an online foreign language learning platform designed as a hobbyist project utilizing spaced repetition methodology through AI-powered flashcards. The platform targets language learners who want an efficient, modern alternative to traditional tools like Anki or SuperMemo, with enhanced AI capabilities for personalized content generation.

### Main Problem Statement
Language learners need an engaging, efficient way to build vocabulary using proven spaced repetition techniques, but existing tools lack modern AI integration for personalized content creation based on the user's actual speech patterns and needs. LingoFlip solves this by combining three flashcard creation methods: AI-generated common words, personalized analysis of user's recorded conversations, and traditional manual entry.

### Key Functional Requirements

#### Core Learning System
- **Spaced Repetition**: FSRS algorithm implementation providing 20-30% better accuracy than traditional SM-2
- **Flashcard Mechanics**: Tinder-style swipe interface (left=incorrect, right=correct) with click-to-flip functionality
- **Daily Goals**: Users must correctly answer 20 cards to complete daily session and unlock story generation
- **Progress Tracking**: FSRS manages review scheduling with increasingly longer intervals for mastered cards
- **Multi-Language Support**: Users can maintain three separate language pairs simultaneously with independent progress tracking

#### Flashcard Creation Methods

**Method 1: AI-Generated Default Words**
- User specifies quantity (default 50 words)
- System generates most common words by frequency across all word types (nouns, verbs, adjectives, adverbs, pronouns)
- AI translates from foreign language to user's native language
- Preview and accept/reject mechanism before adding to collection
- Counts toward monthly limit (20 generations) even if rejected to prevent cost exploitation

**Method 2: Audio Recording Analysis**
- Users upload MP3 or M4A files (max 30MB)
- AssemblyAI analyzes speech and identifies 50 most frequently used words
- Automatic flashcard generation with translations
- Warning if fewer than 30 words identified
- 8 uploads per month limit
- Preview and accept/reject mechanism

**Method 3: Manual Entry**
- Traditional flashcard creation like Anki
- User enters word in foreign language and translation
- 100 manually created cards per month in free tier
- Unlimited conceptually, limited by monthly quota

#### AI Services Integration
- **AssemblyAI**: Speech-to-Text conversion for recording analysis
- **Google Cloud TTS**: Native-speaker pronunciation with autoplay
- **Google Translate/DeepL**: Translation services for flashcard content
- **Story Generation**: After 20 correct answers, AI generates 100-150 word story using learned words at 5-year-old comprehension level
- **Cost Management**: Maximum $0.05 per user per month API costs

#### Authentication & User Management
- **Registration**: Email, password (16+ chars with complexity), native language (English/Polish), initial foreign language, optional 300-char motivation
- **Email Verification**: Required before login access, unverified accounts deleted after 24 hours
- **Password Security**: 16-character minimum with uppercase, lowercase, numbers, special characters
- **Password Reset**: Email-based with 1-hour expiration link
- **Session Management**: Standard token-based authentication

#### User Interface & Experience

**Onboarding Flow (First-Time Users)**
1. One-page summary explaining platform value, features, and freemium model
2. Foreign language selection from dropdown
3. Prompt to create first flashcard set (three method options clearly presented)
4. Immediate first learning session with created cards
5. Onboarding flag stored to skip on subsequent logins

**Learning Session Flow**
1. User views card with foreign language word
2. Clicks to flip card (or uses spacebar)
3. Hears native pronunciation (if autoplay enabled)
4. Sees translation in native language
5. Swipes left (incorrect) or right (correct) or uses arrow keys
6. Incorrect cards return to queue in same session, FSRS resets difficulty
7. Correct cards scheduled by FSRS algorithm
8. Session continues until daily limit reached or all due cards reviewed
9. After 20 correct answers: celebration message + "Generate Your Story" button
10. Story displayed with audio playback, deleted when closed

**Library Management**
- Scrollable list view of all flashcards in active language pair
- Search by word text
- Filter by source (AI-generated, audio-based, manual)
- Filter by mastery level (new, learning, mastered)
- Sort by creation date or next review date
- Edit/delete buttons for each card
- Simple, clean interface without complex features

**Settings Page**
- Daily card limit slider (default 20)
- Native language display (non-editable)
- Foreign language dropdown (switches between configured pairs)
- Audio autoplay toggle (default ON)
- Monthly limit usage display (X/20 AI sets, X/8 audio, X/100 manual)
- Export data button (generates CSV)
- Delete account button (with confirmation)

**Statistics Page**
- Current learning streak (days)
- Total words in collection (active language only)
- Words due today
- Words learned (10+ reviews)
- Monthly limit usage with progress bars
- Account creation date
- Simple number displays, no complex visualizations

#### Business Model & Monetization

**Free Tier Includes:**
- 20 AI-generated word sets per month
- 8 audio file analyses per month
- 100 manually created cards per month
- Daily story generation (free feature)
- Three language pairs
- All core learning features
- Basic statistics and progress tracking

**Limit Management:**
- When limit reached: Modal dialog showing reset date/time
- "Contact us about premium" button → redirect to contact page
- Pre-filled email form with user email and "Premium Plan Inquiry" subject
- Text area for additional information
- Send button to contact product owner
- Limits reset monthly on user's registration anniversary date

**User Capacity:**
- Maximum 50 concurrent users for MVP phase
- Admin panel monitoring to manage capacity

#### Quality Assurance & Feedback

**AI Content Quality Control**
- Preview all AI-generated sets before acceptance
- Accept set: Adds to collection, counts toward monthly limit
- Report issue & reject: Opens feedback form, counts toward limit (prevents exploitation)
- Feedback form: Issue type dropdown (poor translations, inappropriate words, other) + 200-char optional text
- Data logged for future improvements
- No automated fallback mechanisms

**Error Handling**
- API failures: User-friendly message, technical logging, no limit deduction
- Audio analysis issues: Warning if <30 words, instruction for longer/clearer recording
- Network timeouts: "Try again in a few minutes" message
- No automatic retry attempts for MVP

#### Data Management & Privacy (GDPR Compliance)

**Data Retention**
- Audio files: Deleted immediately after Speech-to-Text processing
- Flashcard data: Retained for lifetime of user account
- Application logs: Deleted after 3 months
- Unverified accounts: Deleted after 24 hours

**User Rights**
- Data export: CSV download with all flashcards, translations, creation dates, review history
- Account deletion: Permanent removal within 48 hours after confirmation
- Terms of Service and Privacy Policy acceptance required at registration

**Storage Limits**
- 10,000 total flashcards per user across all language pairs
- 500 new cards per month (cumulative across all creation methods subject to tier limits)

#### Technical Requirements

**Performance Targets**
- Page load time: <5 seconds
- Flashcard flip/swipe response: <160ms
- Uptime: 80% (acceptable for hobbyist project)
- Concurrent users: Maximum 50

**Browser Compatibility**
- Chrome (latest version)
- Firefox (latest version)
- Safari (latest version)
- Edge (latest version)
- No Internet Explorer support
- Web Audio API support required for audio features

**Responsive Design**
- Mobile and tablet support via responsive web design
- Minimum screen width: 320px
- No native mobile app for MVP

**Accessibility (Basic)**
- Keyboard navigation (spacebar to flip, arrows to swipe)
- Sufficient color contrast ratios
- Alt text for images
- Semantic HTML structure
- No full WCAG 2.1 AA compliance required for MVP

#### Admin Panel

**Access & Security**
- Separate password-protected URL
- Basic authentication for MVP

**Admin Features**
- Current user count monitoring (track toward 50-user limit)
- Recent registrations list
- API usage statistics (monitoring cost targets)
- Error log viewer (last 100 entries)
- Manual account deletion capability for test accounts
- System health monitoring

#### Testing & Quality Assurance

**Required Testing**
- Unit tests for core business logic (FSRS algorithm, flashcard CRUD operations)
- Integration tests for AI API calls using mock responses
- Target code coverage: 80% for business logic
- Manual testing of all 10 language pair combinations

**Out of Scope for MVP**
- End-to-end automated testing
- Extensive load testing (50-user limit manageable)
- Comprehensive security penetration testing
- Beta testing program (hobbyist project)

### Key User Stories

**Story 1: New User Onboarding**
- As a new language learner, I want to quickly understand the platform and start learning so that I don't waste time figuring out complex interfaces
- Acceptance: User completes registration → sees one-page summary → selects language → creates first flashcard set → begins learning session in <5 minutes

**Story 2: AI-Generated Flashcard Creation**
- As a beginner learner, I want the system to suggest the most important words to learn so that I focus on high-value vocabulary
- Acceptance: User requests AI word set → previews generated cards → accepts or rejects set → accepted cards appear in library with proper translations and audio

**Story 3: Personalized Learning via Audio Analysis**
- As a language learner, I want to learn words I actually use in conversations so that my learning is relevant to my real life
- Acceptance: User uploads conversation recording → system analyzes and extracts frequent words → generates flashcards → user previews and accepts → cards available for learning

**Story 4: Daily Learning Session**
- As a committed learner, I want to review flashcards daily using proven spaced repetition so that I efficiently retain vocabulary
- Acceptance: User logs in → sees cards due today → swipes through cards → system schedules next reviews based on performance → daily goal tracked

**Story 5: Daily Story Reward**
- As a motivated learner, I want to see my progress through engaging content so that I stay motivated to continue learning
- Acceptance: User completes 20 correct answers → generates story button appears → clicks button → sees 100-150 word story using learned words → listens to audio → closes story

**Story 6: Multi-Language Learning**
- As an ambitious learner, I want to study multiple languages simultaneously so that I can make progress on multiple goals
- Acceptance: User configures three language pairs → switches active language in settings → sees separate flashcard collection and progress for each pair

**Story 7: Manual Flashcard Management**
- As an advanced learner, I want to add specific vocabulary relevant to my needs so that I supplement AI-generated content
- Acceptance: User creates manual flashcard → enters front/back text → card appears in library → can edit or delete anytime → included in FSRS review schedule

**Story 8: Progress Tracking**
- As a learner, I want to see my learning statistics so that I feel motivated and track my consistency
- Acceptance: User views statistics page → sees streak count, total words, due cards, monthly limits → understands progress at a glance

**Story 9: Limit Management & Upgrade Path**
- As a free tier user, I want to know when I approach limits and how to get more capacity so that I can plan my usage or upgrade
- Acceptance: User hits monthly limit → sees clear message with reset date → option to contact about premium → can send inquiry easily

**Story 10: Data Privacy Control**
- As a privacy-conscious user, I want control over my data so that I feel secure using the platform
- Acceptance: User can export all data as CSV → can delete account permanently → audio files not retained → clear privacy policy presented

### Success Criteria & Measurement

#### MVP Success Criteria (from original document)

**Criterion 1: Both manual and AI-driven flashcard generation works**
- Measurement: All three creation methods (AI default, audio analysis, manual) functional and tested
- Target: 100% of creation methods operational
- Timeline: At MVP launch

**Criterion 2: 75% of AI-generated flashcards are satisfactory**
- **Updated Definition**: 75% of users primarily use AI-generated cards (not manual)
- Measurement: Track card source ratio per user after one month of usage
- Calculation: (AI-generated cards + audio-based cards) / (total cards) > 0.75
- Target: >75% of users meet this ratio
- Timeline: Measured after each user's first month

**Criterion 3: Most users (>75%) create flashcards using AI**
- Measurement: Track percentage of users who have created at least one AI-generated or audio-based flashcard set
- Target: >75% of active users have used AI features
- Timeline: Measured monthly across user base

**Criterion 4: Flashcards and learning-stage persisted across sessions**
- Measurement: User logs out and back in, sees same flashcards with preserved FSRS scheduling data
- Target: 100% data persistence, zero data loss incidents
- Timeline: Continuous monitoring

#### Additional Success Metrics

**Engagement Metrics**
- Daily active users (DAU) / Monthly active users (MAU) ratio
- Average learning streak length
- Percentage of users reaching daily goal (20 correct answers)
- Story generation frequency (indicates engaged users)
- Session duration and frequency

**Quality Metrics**
- AI-generated set acceptance rate (target: >80%)
- Flashcard report rate (target: <10% of generated sets)
- Audio analysis success rate (target: >90% produce 30+ words)
- User satisfaction with translations (track report reasons)

**Technical Metrics**
- API cost per user per month (target: <$0.05)
- Page load time (target: <5 seconds)
- Flashcard response time (target: <160ms)
- System uptime (target: 80%)
- Error rate for API calls (target: <5%)

**Business Metrics**
- User registration rate
- Email verification completion rate (target: >80%)
- Freemium to premium inquiry conversion
- User retention (7-day, 30-day)
- Churn rate

### Design Constraints & Considerations

#### Technical Constraints
- Maximum 50 concurrent users (capacity management required)
- $0.05 per user monthly API budget (careful service selection)
- 10,000 flashcard storage limit per user
- 500 new cards per month per user
- Audio file size limited to 30MB
- No technology stack specified (flexibility for implementation)

#### Business Constraints
- Hobbyist project scope (not commercial initially)
- No strict development timeline
- No dedicated support team (self-service emphasis)
- Limited testing resources (80% coverage target, no E2E)
- Admin manual management of 50-user cap

#### User Experience Constraints
- Web-only platform (no native mobile apps)
- Modern browsers only (no legacy support)
- Basic accessibility (not full WCAG compliance)
- Simple UI without complex features
- Email verification required (may impact signup conversion)

#### Feature Scope Constraints
- No sentence context for MVP
- No email reminder notifications
- No OAuth or 2FA authentication
- No automatic audio quality fallbacks
- No hard/good/easy review options
- No story history retention
- No user-to-user flashcard sharing

#### Language & Content Constraints
- Only 10 foreign languages supported
- Only 2 native/application languages (English, Polish)
- Only single-word flashcards (no phrases)
- Only 5 word types (nouns, verbs, adjectives, adverbs, pronouns)
- Stories limited to beginner level (A1-A2)

### Risk Assessment

#### High-Priority Risks

**Risk 1: API Cost Overruns**
- Description: Users rejecting sets repeatedly to exploit system, actual usage exceeds $0.05/user
- Mitigation: Rejected sets count toward monthly limits, aggressive monitoring via admin panel
- Impact: High (financial sustainability)

**Risk 2: Audio Analysis Quality**
- Description: AssemblyAI produces poor word extraction, users frustrated
- Mitigation: Clear file requirements, warning messages, no fallback (user provides better audio)
- Impact: Medium (feature adoption)

**Risk 3: 50-User Capacity Management**
- Description: Exceeding concurrent user limit, performance degradation
- Mitigation: Admin panel monitoring, manual account cleanup, registration throttling if needed
- Impact: High (user experience)

#### Medium-Priority Risks

**Risk 4: Email Verification Friction**
- Description: Required verification before login may reduce signup conversion
- Mitigation: Clear messaging about verification email, 24-hour window before cleanup
- Impact: Medium (user acquisition)

**Risk 5: FSRS Algorithm Integration**
- Description: Complex algorithm implementation, potential bugs in scheduling
- Mitigation: Unit testing focus, default parameters, extensive logging for debugging
- Impact: Medium (core functionality)

**Risk 6: Multi-Language Data Management**
- Description: Users switching language pairs, data isolation complexity
- Mitigation: Clear data model with separate collections per pair, thorough integration testing
- Impact: Medium (data integrity)

#### Low-Priority Risks

**Risk 7: Browser Compatibility**
- Description: Users on unsupported browsers unable to access platform
- Mitigation: Clear browser requirements on registration page, broad modern browser support
- Impact: Low (limited user base on old browsers)

**Risk 8: 80% Uptime May Frustrate Users**
- Description: Lower uptime SLA than commercial products
- Mitigation: Clear expectation setting (hobbyist project), error messages, status communication
- Impact: Low (expectations managed)

### Future Enhancements (Out of MVP Scope)

#### Planned Features
- Voice input for flashcard answers with speech recognition
- Support for more application languages beyond English and Polish
- Support for additional foreign languages beyond initial 10
- Live speech recording within app for AI flashcard generation
- Native mobile applications (iOS, Android)
- Flashcard set sharing between users
- Hard/good/easy review options (advanced FSRS)
- Sentence context mode (embedding words in sentences)
- Email reminder notifications for daily practice
- Story history retention (7+ days)
- Personalized FSRS parameter optimization
- Full WCAG 2.1 AA accessibility compliance
- Advanced tagging and categorization system
- Community features and social learning
- Gamification elements beyond streak tracking

#### Potential Premium Features
- Unlimited AI flashcard generation
- Unlimited audio file uploads
- Advanced analytics and learning insights
- Personalized FSRS optimization
- Priority support
- Ad-free experience (if ads added to free tier)
- Advanced study modes
- Custom themes and UI personalization

</prd_planning_summary>

## <unresolved_issues>

### Critical - Requiring Immediate Clarification
None identified. All critical aspects have been addressed through the question rounds.

### Important - Should Be Resolved Before Development
None identified. All important aspects have been clarified.

### Minor - Can Be Resolved During Development

1. **Translation Service Selection**: Final choice between Google Cloud Translation API vs. DeepL API not definitively made
   - Recommendation: Decide during technical design based on quality testing and cost comparison
   - Impact: Low (both services meet requirements)

2. **Email Service Provider**: No specification for transactional email service (verification, password reset)
   - Recommendation: Select during implementation (SendGrid, AWS SES, Mailgun, etc.)
   - Impact: Low (standard requirement)

3. **Specific Story Generation Prompts**: Exact AI prompts for generating stories not defined
   - Recommendation: Develop and test during implementation, iterate based on quality
   - Impact: Low (can be refined post-launch)

4. **Admin Panel URL Structure**: Specific URL path for admin access not defined
   - Recommendation: Decide during development (e.g., /admin, /dashboard)
   - Impact: Very Low (implementation detail)

5. **Monthly Limit Reset Logic**: Exact timestamp for monthly limit resets not specified (user registration anniversary vs. calendar month)
   - Clarification from conversation: Registration anniversary date
   - Impact: Very Low (clarified)

6. **Data Export CSV Format**: Specific columns and structure of exported CSV not detailed
   - Recommendation: Define during implementation based on data model
   - Impact: Very Low (functional requirement met regardless of format details)

### Documentation Gaps - For PRD Completion

1. **Visual Design Guidelines**: No mockups or design system specifications provided
   - Note: PRD should reference need for design phase
   - Impact: Expected for separate design documentation

2. **API Integration Details**: Specific API endpoints, authentication methods, rate limits for third-party services
   - Note: Technical implementation details outside PRD scope per user
   - Impact: None for PRD (handled in technical design)

3. **Database Schema**: Specific table structures, relationships, indexes
   - Note: Technical implementation details outside PRD scope per user
   - Impact: None for PRD (handled in technical design)

4. **Deployment Infrastructure**: Hosting provider, CI/CD pipeline, environment strategy
   - Note: Technical implementation details outside PRD scope per user
   - Impact: None for PRD (handled in DevOps planning)

### Recommendations for Next Steps

1. **Create comprehensive PRD document** using all gathered information in structured format
2. **Design phase**: Create wireframes and mockups for key user flows
3. **Technical design**: Architecture decisions, technology stack selection, API integration planning
4. **Development planning**: Sprint planning, task breakdown, resource allocation
5. **Testing strategy**: Detailed test cases, testing environment setup
6. **Beta launch plan**: Initial user recruitment (targeting 10-20 users), feedback collection process

</unresolved_issues>

---

**Summary Complete**: This comprehensive summary captures 103 discrete decisions, 55 matched recommendations, detailed functional requirements, 10 user stories, measurable success criteria, and thorough risk assessment. The PRD planning phase is complete with minimal unresolved issues, all of which can be addressed during development phases without blocking PRD creation.

