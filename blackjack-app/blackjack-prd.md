# Blackjack Card Counting Trainer - Product Requirements Document

**Target Platform:** Web (Next.js 14+)
**Primary Device:** Mobile-first
**Purpose:** Educational card counting trainer with multi-player simulation

---

## Product Vision

A comprehensive blackjack card counting trainer that teaches players the Hi-Lo counting system with full assistance, featuring realistic multi-player simulation to demonstrate the advantages of card counting in real casino scenarios.

### Core Value Proposition

**For card counting learners:**
- Full assistance with count overlays and strategy recommendations always visible
- Real-time explanations of count values and optimal decisions
- Practice in a realistic multi-player environment (3 NPC players)
- Learn card counting fundamentals without pressure

**What This Is NOT:**
- Not a real-money gambling application
- Not optimized for automated play or card counting software
- Not a complete casino simulation (no side bets, insurance optional, etc.)

---

## Technology Stack

**Framework:** Next.js 14+ with TypeScript
- **100% client-side operation** - All game logic runs in the browser
- No server-side rendering for game components
- No backend API or database required

**Styling:** Tailwind CSS
- Custom casino theme
- Mobile-first responsive design

---

## Visual Design

**Casino Theme:** Modern luxury with emerald green felt, charcoal black background, gold accents
- Mobile-first responsive design (portrait primary, landscape supported)
- Touch-friendly interface with accessible controls

---

## Game Rules

**Standard Blackjack:**
- Objective: Get closer to 21 than dealer without busting
- Card values: 2-10 face value, J/Q/K = 10, Ace = 1 or 11
- Dealer hits on soft 17, stands on hard 17+
- Blackjack pays 3:2

**Player Actions:**
- **Hit:** Take another card
- **Stand:** Keep current hand
- **Double Down:** Double bet, take exactly one more card
- **Split:** Divide pairs into two hands (max 2 hands)
- **Surrender:** Forfeit half bet and end hand

**Deck Options:** 1, 2, 6, or 8 decks with appropriate penetration thresholds
- Reshuffle triggers reset running count

---

## Card Counting System: Hi-Lo

**Card Values:**
- Low Cards (2-6): +1
- Neutral Cards (7-9): 0
- High Cards (10, J, Q, K, A): -1

**Running Count (RC):**
- Cumulative count of all cards seen since last shuffle
- Display format: "RC +3" with color coding (green positive, red negative, gray neutral)
- Visible in Training/Learning modes, hidden by default in Testing mode

**True Count (TC):**
- Running count adjusted for remaining decks: TC = RC / decks remaining
- More important for betting decisions
- Example: RC +8 with 3 decks left = TC +3

**Deck Penetration:**
- Display approximate penetration in realistic buckets
- Visual: Stack of cards with red line showing position
- Updates after each hand

---

## NPC System

**Configuration:**
- 3 NPC players at table with user (4 total positions)
- All NPCs play simplified basic strategy (hit/stand only, no split/double)
- Always bet table minimum
- Decisions made automatically and instantly

**Purpose:**
- Demonstrates card counting value (more cards visible = better count accuracy)
- Simulates realistic casino environment
- Keeps player focused on their own strategy

---

## Learning System: Full Assistance Mode

**Training Mode (Always Active):**
- Count overlays (+1/0/-1) always visible on cards
- Running/True count always displayed with color coding
- Automatic strategy hints with recommended actions highlighted
- Count-based betting advice shown before each hand
- Deviation alerts when TC suggests strategy changes
- Real-time explanations of why certain plays are optimal
- No pressure, pure learning focus

**Features:**
- All assistance features enabled at all times
- Strategy recommendations based on both basic strategy and count
- Visual indicators for optimal decisions (green highlights)
- Detailed tooltips explaining card counting principles
- Session statistics tracked locally

---

## Strategy & Deviations

**Basic Strategy:**
- Mathematically optimal play without count information
- Covers hard totals, soft totals, pairs, and surrender decisions

**Count-Based Deviations (Key Examples):**
- Insurance: Take when TC ≥ +3
- 16 vs 10: Stand when TC ≥ 0
- 10 vs 10: Double when TC ≥ +4
- 12 vs 3: Stand when TC ≥ +2

**Display:**
- Automatically suggested when TC threshold reached
- Visual indicators show when deviation applies
- Tooltips explain the logic behind each deviation

---

## Betting & Bankroll

**Bankroll Management:**
- Starting: $1,000 (configurable)
- Table minimum: $5, $10, or $25 (configurable)
- Bankroll display color-coded (green = profit, red = losing)
- Bankruptcy handling with reset option

**Bet Spread (TC-Based):**
- TC ≤ 0: 1 unit
- TC +1: 1 unit
- TC +2: 2 units
- TC +3: 4 units
- TC +4: 6 units
- TC ≥ +5: 8 units

**Betting Interface:**
- Slider input with presets (1x, 2x, 4x, 6x, 8x)
- Recommended bet always highlighted based on True Count
- Visual indicator shows optimal bet spread
- Validation: min/max limits, bankroll check

---

## Animations & Visual Feedback

**Card Dealing:**
- Staggered dealing animation with smooth card flips
- Count overlays fade in after card reveal

**Win/Lose Effects:**
- Win: Green glow, chip animations
- Lose: Red flash
- Push: Gray flash
- Blackjack: Gold sparkle effect

**Reshuffle:**
- Cards return to deck with visual feedback
- Count displays reset to 0

---

## User Flow

**1. Configure Settings (Optional)**
- Deck count: 1, 2, 6, 8
- Starting bankroll
- Table minimum
- Animation speed

**2. Place Bet**
- Use slider or presets
- See recommended bet highlighted based on True Count

**3. Watch Initial Deal**
- Cards deal to NPCs, Player, Dealer (animated)
- Count overlays appear on all cards

**4. NPCs Play (Automatic)**
- Each NPC makes instant decision
- Fast progression (~1 sec per NPC)

**5. Player Turn**
- Available actions highlighted
- Recommended action highlighted in green
- Make decision: Hit / Stand / Double / Split / Surrender
- Tooltips explain why certain actions are optimal

**6. If Split:**
- Hand divides, play Hand 1 then Hand 2
- Recommended actions shown for each hand

**7. Dealer Plays**
- Hole card reveals
- Dealer auto-plays per rules

**8. Resolution**
- Win/lose/push animations
- Payouts processed
- Bankroll updates

**9. Check Penetration**
- Reshuffle if threshold exceeded
- Otherwise, proceed to next hand

---

## Success Metrics

**User Engagement:**
- Average session duration: > 10 minutes
- Hands played per session: > 20 hands
- Return rate: 40% return for second session

**Educational Effectiveness:**
- Users understand +1/0/-1 counting system
- Users can identify high vs low cards visually
- Users understand relationship between True Count and betting
- Users see connection between count and strategy deviations

**Technical Performance:**
- Fast page load on mobile devices
- Smooth animations and interactions
- Accessible design
- Works completely offline after initial load

---

## Architecture

**Client-Side Only Design:**
- All game logic executes in browser
- No server dependencies or API calls
- Complete functionality offline-capable

**Layered Structure:**

**Foundation Layer:**
- TypeScript interfaces and types
- Core constants and configuration
- Tailwind CSS casino theme

**Game Logic Layer:**
- Game rules and mechanics
- Card counting system (RC, TC, penetration)
- NPC system with basic strategy
- Hint engine with strategy recommendations

**UI Layer:**
- Game table layout and components
- Card components with animations
- Control interface (betting, actions)
- Display components (counts, bankroll, hints)

**Key Principles:**
- Separation of game logic and presentation
- Type-safe contracts between layers
- Fully functional offline

---

## Definition of Done

- [ ] All game rules implemented correctly (split, surrender, multi-hand)
- [ ] 3 NPC players with basic strategy
- [ ] Hi-Lo counting system accurate (running, true, penetration)
- [ ] Full assistance mode with all hints and overlays visible
- [ ] Count overlays visible on all cards
- [ ] Recommended actions always highlighted
- [ ] Bet recommendations always shown based on True Count
- [ ] Mobile-first UI works on mobile devices (portrait & landscape)
- [ ] Casino theme professional and polished
- [ ] Smooth animations and interactions
- [ ] TypeScript strict mode with no errors
- [ ] Session statistics persisted locally
- [ ] Reshuffle triggers at correct penetration thresholds
- [ ] Bankruptcy handled gracefully

---

**Status:** Ready for Implementation
**Architecture:** Client-side only, no server required
