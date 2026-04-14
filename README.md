# Michi (道)

**Memory Palaces of Japan**

Route planning apps treat routes as disposable logistics. You optimize, you execute, you forget.

But walking in Japan is different. It's the 7-Eleven coffee at dawn, the shrine priest waving you through, the clouds parting over Fuji, the cicadas at that one turn. These aren't waypoints — they're memories.

---

## What

Michi treats walked routes as **keepsakes**, not just plans.

**Discover** curated walking paths through Japan's most meaningful places — Shikoku's 88 temples, Nakasendo's post towns, Kumano Kodo's forest shrines. Seasonal themes shift with the calendar: plum blossoms in spring, maple leaves in autumn.

**Capture** your journey as you walk. GPS tracking records your path. Photos and notes mark the moments that matter. The walk becomes a spatial memory palace.

**Revisit** later. Animate through your journey. Photos appear where you took them. Notes pop up at each location. It's not a photo album — it's reliving the walk.

**Share** with others. Send someone your "Kyoto Dawn Walk" and they experience it as you did. Or walk it themselves, following your path and seeing your markers along the way.

---

## Philosophy

**Japan is the product.**

This isn't a generic travel app that happens to feature Japan. Every design decision, every curated route, every seasonal theme is Japan-specific. The name Michi (道) means "path, way, journey" in Japanese. That's not branding — that's what the app is about.

**Routes are artifacts, not disposable.**

Most route planners treat your journey like a problem to be solved. Find the fastest path, execute it, discard it. Michi treats your walked routes as keepsakes — things worth saving, revisiting, sharing. A walk through Kyoto's back streets at dawn is something you did. It's part of your story.

**Walking is the only mode.**

No transit suggestions. No "would you like to take the train instead?" If you want to take the train, take the train. Michi is for walking — the slow, intentional kind where you notice things. The 7-Eleven coffee. The cat in the window. The unexpected view.

**Seasons matter.**

Japan changes with the calendar. Plum wine and bamboo in spring. Maple red and rice gold in autumn. The app shifts with it. Seasonal themes auto-cycle based on the month. A route you walked in cherry blossom season looks different when you revisit it in November. That's the point.

**Depth over breadth.**

One truly great curated route is better than ten mediocre ones. Nakasendo's 69 post towns, each with stories. The Kumano Kodo's spiritual paths, walked for centuries. These aren't generic tourist attractions. They're places people have been walking for a thousand years.

---

## Features

### Curated Routes
- Nakasendo: The mountain path between Kyoto and Edo, 69 post towns
- Kumano Kodo: Three pilgrimage routes through sacred mountains
- More routes added based on partnerships with tourism boards and pilgrimage organizations

### Walk Mode
- GPS tracking with waypoint recording
- Photo and note capture at any point
- Battery warnings at 20%
- GPS loss detection and recovery
- Crash recovery — resume your walk if the app closes

### Replay Mode
- Animated journey through your walked route
- Photos and notes appear as you "walk" through the timeline
- Playback controls: play/pause, speed adjustment, timeline scrubber
- Timeline view with all memories chronologically

### Sharing
- Generate unlisted links to your walked routes
- Viewers see the full replay without login
- "Copy to my walks" saves a bookmark, not a clone
- Signed URLs protect photo access

### Seasonal Themes
- Spring: Plum wine + bamboo + washi cream
- Autumn: Maple red + rice gold + tree bark
- Auto-detects season from device calendar
- Manual override available
- Light and dark mode variants

### Rainy Day Backups
- Indoor alternatives for each curated route
- Underground passage options
- "Rain expected? See options" button on route details

### Route Status
- Manual closure and event updates
- Shrine/temple closure notices
- Festival information
- Weather warnings

---

## Tech Stack

**Frontend**
- Vite + React + TypeScript
- Tailwind CSS
- Mapbox GL JS

**Backend**
- Supabase (Auth + Postgres + Row Level Security)
- Edge Functions for secure data proxying

**Platform**
- Web app, responsive for mobile
- No native app

---

## Scope

**Japan-only, permanently.**

Michi is not a global travel app waiting to happen. It's a Japan walking app. If we expand to Korea or Taiwan someday, those will be separate products with their own names, their own curated routes, their own cultural identity.

Depth over breadth.

---

## Status

**In Development — v1 MVP targeting 5-6 weekends**

See [ROADMAP.md](./ROADMAP.md) for the full implementation plan.
See [ARCHITECTURE.md](./ARCHITECTURE.md) for technical details.
See [DESIGN-DOC.md](./DESIGN-DOC.md) for the complete design specification.

---

## License

MIT

---

*"The path is the goal."*
