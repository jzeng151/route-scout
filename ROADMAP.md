# Michi Roadmap

**Project:** Michi (道) — Memory Palaces of Japan
**Timeline:** 5-6 weekends for MVP (v1)
**Status:** Implementation Phase

---

## Phase 1: Foundation (Weekend 1)

**Goal:** Scaffold project, set up infrastructure, basic map rendering

### 1.1 Project Scaffold
```bash
git commit -m "feat: initialize Vite + React + TypeScript + Tailwind scaffold"
```
- Vite project creation
- React 18 + TypeScript strict mode
- Tailwind CSS configuration
- ESLint + Prettier setup
- Folder structure: `src/components`, `src/hooks`, `src/lib`, `src/types`

### 1.2 Supabase Setup
```bash
git commit -m "feat: configure Supabase client and auth"
```
- Supabase client initialization
- Environment variables setup
- Auth context provider
- Email + Google OAuth providers

### 1.3 Database Schema
```bash
git commit -m "feat: create core database schema"
```
- `personal_routes` table
- `personal_route_waypoints` table
- `personal_route_memories` table
- Row Level Security (RLS) policies
- Database migrations in `supabase/migrations/`

### 1.4 Mapbox Integration
```bash
git commit -m "feat: integrate Mapbox GL JS for map rendering"
```
- Mapbox GL JS setup
- Full-screen map component
- Access token configuration
- Basic marker rendering

### 1.5 Seasonal Theme System
```bash
git commit -m "feat: implement seasonal theme system (spring + autumn)"
```
- CSS custom properties for colors
- Season detection (`new Date().getMonth()`)
- Light/dark mode toggle
- Spring theme (plum + bamboo + washi)
- Autumn theme (maple + rice gold + tree bark)
- Theme provider component

---

## Phase 2: Walk Mode (Weekend 2)

**Goal:** Core GPS tracking and memory capture

### 2.1 Geolocation Setup
```bash
git commit -m "feat: implement GPS tracking service"
```
- Geolocation API wrapper
- Background permission request (iOS)
- 10-second polling interval
- 25-meter movement threshold
- Accuracy filtering (>50m rejected)

### 2.2 Waypoint Recording
```bash
git commit -m "feat: waypoint recording and storage"
```
- Waypoint data model
- IndexedDB caching for offline resilience
- Batch upload to Supabase
- Crash recovery (resume walk on reopen)

### 2.3 Walk Mode UI
```bash
git commit -m "feat: Walk Mode UI with map and controls"
```
- Full-screen map with current position
- Path tracing as user walks
- Start/End walk buttons
- Distance and duration display
- Battery percentage indicator

### 2.4 Memory Capture
```bash
git commit -m "feat: memory capture (notes + photos)"
```
- Note input modal
- Photo capture via Camera API
- Location tagging for each memory
- Memory list during walk

### 2.5 Photo Storage
```bash
git commit -m "feat: Supabase Storage integration for photos"
```
- Private bucket configuration
- Signed URL generation
- 2GB quota tracking
- Upload with retry logic

### 2.6 Battery Warning
```bash
git commit -m "feat: battery warning at 20% with continue/stop options"
```
- Battery API integration
- Warning modal at 20%
- Continue or stop tracking options
- Graceful walk end if battery dies

### 2.7 GPS Error Handling
```bash
git commit -m "feat: GPS loss detection and recovery"
```
- GPS loss detection
- Pause tracking when signal lost
- "Searching for signal..." toast
- Auto-resume on reconnection
- Waypoint gap handling

---

## Phase 3: Replay Mode (Weekend 2-3)

**Goal:** Animate walks and view memories

### 3.1 Replay Data Loading
```bash
git commit -m "feat: personal route data loading for replay"
```
- Route + waypoints + memories query
- Timeline computation (start/end times)
- Pattern-specific queries (detail vs list)

### 3.2 Path Animation
```bash
git commit -m "feat: animated path drawing for replay"
```
- Progressive path rendering
- Mapbox camera animation
- Speed controls (1x, 2x, 4x)
- Play/pause functionality

### 3.3 Memory Popups
```bash
git commit -m "feat: memory popups at timestamp during replay"
```
- Timestamp-based memory triggers
- Photo display inline
- Note cards with content
- Popup positioning on map

### 3.4 Timeline View
```bash
git commit -m "feat: timeline view with memory thumbnails"
```
- Chronological memory list
- Photo thumbnails
- Click-to-jump to timestamp
- Timeline scrubber

### 3.5 Playback Controls
```bash
git commit -m "feat: replay playback controls (play/pause/speed/scrub)"
```
- Play/pause button
- Speed selector
- Timeline scrubber
- Progress indicator

---

## Phase 4: Curated Routes (Weekend 3-4)

**Goal:** Editorial content and route discovery

### 4.1 Curated Routes Schema
```bash
git commit -m "feat: curated_routes database schema"
```
- `curated_routes` table
- `curated_route_stops` table
- `seasonal_themes` table
- `route_status` table

### 4.2 Nakasendo Route
```bash
git commit -m "feat: seed Nakasendo curated route"
```
- 69 post towns data
- Stop descriptions (EN + JA)
- Photos for each stop
- Difficulty and distance metadata

### 4.3 Route Discovery UI
```bash
git commit -m "feat: curated routes listing page"
```
- Route cards with thumbnails
- Filter by region, difficulty, season
- Seasonal preview based on current month
- Route detail page

### 4.4 Route Detail Page
```bash
git commit -m "feat: curated route detail page"
```
- Full route description
- Stop list with photos
- Seasonal preview
- "Start this walk" button

### 4.5 Rainy Day Backup
```bash
git commit -m "feat: rainy day backup suggestions"
```
- Backup route display
- Indoor alternatives
- Underground passage options
- "Rain expected? See options" button

### 4.6 Status Badges
```bash
git commit -m "feat: route status badges (closures/events)"
```
- Status badge on route cards
- Closure/event/warning types
- Effective date range
- Manual status updates

### 4.7 Second Curated Route
```bash
git commit -m "feat: seed second curated route (Kumano Kodo segment)"
```
- Kumano Kodo route data
- Stops and descriptions
- Photos and metadata

### 4.8 Admin Status Dashboard
```bash
git commit -m "feat: admin status dashboard for route updates"
```
- Admin-only UI
- Create/update status entries
- Route selection
- Date range picker

---

## Phase 5: Sharing (Weekend 4)

**Goal:** Share personal routes publicly

### 5.1 Share Slug Generation
```bash
git commit -m "feat: share slug generation with nanoid"
```
- Unique slug per route
- `visibility` enum (private/unlisted/public)
- Share button on personal routes

### 5.2 Public Route View
```bash
git commit -m "feat: public route viewing without login"
```
- Read-only replay for shared routes
- No authentication required
- Memory display
- "Copy to my walks" bookmark button

### 5.3 Signed URL Security
```bash
git commit -m "feat: signed URLs for shared photo access"
```
- Postgres crypto functions
- 1-hour URL expiry
- Edge Function for URL generation
- Anonymous rate limiting (IP-based, 100/hr)

### 5.4 Share UI
```bash
git commit -m "feat: share interface with visibility controls"
```
- Visibility selector (private/unlisted/public)
- Share link with copy button
- Preview of shared page
- Revoke access option

---

## Phase 6: Polish & Testing (Weekend 5-6)

**Goal:** Production-ready quality

### 6.1 Error Handling
```bash
git commit -m "feat: comprehensive error handling"
```
- Hierarchical error strategy (crash > toast > inline > silent)
- GPS loss handling
- Photo upload failure with retry
- Network error detection
- Offline queue with exponential backoff

### 6.2 Loading States
```bash
git commit -m "feat: loading states across all views"
```
- Skeleton loaders for lists
- Spinner for async operations
- Optimistic UI updates
- "Saving..." indicators

### 6.3 Responsive Mobile
```bash
git commit -m "feat: responsive mobile design"
```
- Mobile-first breakpoints
- Touch-friendly targets (44px min)
- Bottom sheet on mobile
- Full-screen map on small screens

### 6.4 Accessibility
```bash
git commit -m "feat: accessibility improvements"
```
- Keyboard navigation
- Screen reader support
- Focus management
- ARIA labels
- Skip links
- Reduced motion support

### 6.5 E2E Tests
```bash
git commit -m "test: E2E tests with Playwright"
```
- Walk mode flow
- Replay mode flow
- Sharing flow
- GPS loss recovery
- Battery warning
- Anonymous viewing

### 6.6 Performance Testing
```bash
git commit -m "test: performance testing for GPS and replay"
```
- GPS tracking battery impact
- Replay animation smoothness
- Photo upload optimization
- Map rendering performance

### 6.7 Deployment
```bash
git commit -m "chore: configure Vercel deployment"
```
- Vercel project setup
- Environment variables
- Auto-deploy on merge
- Custom domain configuration
- CI/CD with GitHub Actions

---

## v1.5 (Post-Launch)

**Goal:** Enhance based on user feedback

### v1.5 Features
- [ ] Summer + Winter seasonal themes
- [ ] Audio memory capture
- [ ] User cloud storage (Google Drive, Dropbox)
- [ ] Search functionality
- [ ] Route favorites/collections
- [ ] User profile pages

---

## v2 (Future)

**Goal:** Advanced features and community

### v2 Features
- [ ] "Walk this myself" route cloning
- [ ] Social features (comments, likes)
- [ ] User-generated curated routes
- [ ] Advanced filtering
- [ ] Offline map tile caching
- [ ] Web scraping infrastructure for live data
- [ ] Notification system
- [ ] Route recommendations

---

## Git Workflow

**Branch strategy:**
- `main` — production, auto-deployed
- `develop` — integration branch
- `feature/*` — feature branches
- `fix/*` — bugfix branches

**Commit conventions:**
- `feat:` — new feature
- `fix:` — bug fix
- `refactor:` — code refactoring
- `test:` — adding tests
- `docs:` — documentation
- `chore:` — build/config changes
- `perf:` — performance improvements

**Checkpoint flow:**
1. Create feature branch from `develop`
2. Implement feature with atomic commits
3. Each checkpoint = meaningful commit
4. PR to `develop` when phase complete
5. Merge to `main` for deployment
