# Michi Architecture

**Project:** Michi (道) — Memory Palaces of Japan
**Tech Stack:** TypeScript Full-Stack
**Last Updated:** 2026-04-14

---

## Tech Stack

### Frontend

| Category | Technology | Purpose |
|----------|------------|---------|
| **Framework** | Vite 5.x | Build tool and dev server |
| **UI** | React 18 | Component framework |
| **Language** | TypeScript 5.x | Type safety (strict mode) |
| **Styling** | Tailwind CSS 3.x | Utility-first CSS |
| **Maps** | Mapbox GL JS 3.x | Map rendering and animation |
| **Routing** | React Router 6.x | Client-side routing |
| **State** | React Context + hooks | Global state management |
| **Forms** | React Hook Form | Form validation |
| **Drag & Drop** | @dnd-kit | List reordering |
| **File Handling** | JSZip | KMZ unzipping |
| **Sanitization** | DOMPurify | HTML sanitization for KML |
| **Testing** | Vitest + React Testing Library | Unit/integration tests |
| **E2E** | Playwright | End-to-end tests |

### Backend

| Category | Technology | Purpose |
|----------|------------|---------|
| **Backend** | Supabase | Auth + Database + Storage |
| **Database** | PostgreSQL 15 | Relational data |
| **Auth** | Supabase Auth | Email + Google OAuth |
| **Storage** | Supabase Storage | Photo storage (private bucket) |
| **Edge Functions** | Deno | Serverless functions (KML proxy, share proxy) |
| **Security** | Row Level Security (RLS) | Database-level access control |

### Deployment

| Category | Technology | Purpose |
|----------|------------|---------|
| **Frontend** | Vercel | Hosting and CI/CD |
| **Backend** | Supabase Cloud | Managed backend |
| **Domain** | Vercel Custom Domain | michi.app (planned) |
| **CI/CD** | GitHub Actions | Type-check + tests on PR |

### External APIs

| API | Usage | Limits |
|-----|-------|--------|
| Mapbox GL JS | Map rendering | 100K loads/month free |
| Mapbox Optimization API | Route optimization | 25 waypoints max |
| Mapbox Geocoding API | Search autocomplete | Included with loads |
| Google Maps KML | Curated route import (via proxy) | Rate-limited |

---

## Folder Structure

```
route-scout-c/
├── .github/
│   └── workflows/
│       └── ci.yml              # GitHub Actions for type-check + tests
│
├── public/
│   └── favicon.ico
│
├── src/
│   ├── components/             # React components
│   │   ├── ui/                # Reusable UI components
│   │   │   ├── Button.tsx
│   │   │   ├── Input.tsx
│   │   │   ├── Modal.tsx
│   │   │   ├── Toast.tsx
│   │   │   └── ...
│   │   ├── map/               # Map-related components
│   │   │   ├── MapView.tsx    # Full-screen map container
│   │   │   ├── MapMarker.tsx  # Individual markers
│   │   │   ├── RoutePath.tsx  # Animated route line
│   │   │   └── MemoryPopup.tsx # Memory cards on map
│   │   ├── walk/              # Walk Mode components
│   │   │   ├── WalkMode.tsx   # Main walk interface
│   │   │   ├── WalkControls.tsx # Start/End/pause
│   │   │   ├── MemoryCapture.tsx # Add note/photo
│   │   │   └── BatteryWarning.tsx # Low battery alert
│   │   ├── replay/            # Replay Mode components
│   │   │   ├── ReplayMode.tsx # Main replay interface
│   │   │   ├── PlaybackControls.tsx # Play/pause/speed
│   │   │   ├── Timeline.tsx   # Memory timeline
│   │   │   └── TimelineScrubber.tsx # Scrub through replay
│   │   ├── routes/            # Curated Routes components
│   │   │   ├── RouteList.tsx  # Browse routes
│   │   │   ├── RouteCard.tsx  # Route preview card
│   │   │   ├── RouteDetail.tsx # Full route page
│   │   │   ├── RouteStops.tsx # Stop list
│   │   │   └── StatusBadge.tsx # Closure/event badges
│   │   ├── auth/              # Authentication components
│   │   │   ├── LoginForm.tsx
│   │   │   ├── SignupForm.tsx
│   │   │   └── AuthProvider.tsx
│   │   └── layout/            # Layout components
│   │       ├── Header.tsx
│   │       ├── Sidebar.tsx
│   │       └── MobileNav.tsx
│   │
│   ├── hooks/                  # Custom React hooks
│   │   ├── useGeolocation.ts  # GPS tracking
│   │   ├── useBattery.ts      # Battery status
│   │   ├── useCamera.ts       # Photo capture
│   │   ├── useSupabase.ts     # Supabase client
│   │   ├── useAuth.ts         # Auth state
│   │   ├── useOffline.ts      # Offline detection
│   │   └── useTheme.ts        # Seasonal theme
│   │
│   ├── lib/                    # Utility libraries
│   │   ├── supabase.ts        # Supabase client config
│   │   ├── mapbox.ts          # Mapbox token and config
│   │   ├── storage.ts         # IndexedDB wrapper
│   │   ├── gps.ts             # GPS utilities
│   │   ├── photo.ts           # Photo upload utilities
│   │   └── theme.ts           # Theme color utilities
│   │
│   ├── services/               # API/business logic
│   │   ├── walk/              # Walk Mode services
│   │   │   ├── tracking.ts    # GPS tracking logic
│   │   │   ├── waypoints.ts   # Waypoint storage
│   │   │   └── memories.ts    # Memory storage
│   │   ├── replay/            # Replay services
│   │   │   ├── animation.ts   # Path animation
│   │   │   └── timeline.ts    # Timeline computation
│   │   ├── routes/            # Curated routes
│   │   │   └── queries.ts     # Route data queries
│   │   └── share/             # Sharing
│   │       └── signedUrls.ts  # Signed URL generation
│   │
│   ├── types/                  # TypeScript types
│   │   ├── database.ts        # Supabase generated types
│   │   ├── routes.ts          # Route types
│   │   ├── walk.ts            # Walk mode types
│   │   ├── replay.ts          # Replay types
│   │   └── theme.ts           # Theme types
│   │
│   ├── styles/                 # Global styles
│   │   ├── globals.css        # Tailwind + custom
│   │   └── themes.css         # Seasonal theme variables
│   │
│   ├── pages/                  # Route components
│   │   ├── Home.tsx           # Landing page
│   │   ├── Walk.tsx           # Walk mode
│   │   ├── Replay.tsx         # Replay mode
│   │   ├── Routes.tsx         # Curated routes list
│   │   ├── RouteDetail.tsx    # Route detail
│   │   ├── Shared.tsx         # Public shared route
│   │   └── Admin.tsx          # Admin dashboard
│   │
│   ├── App.tsx                # Root component
│   ├── main.tsx               # Entry point
│   └── vite-env.d.ts          # Vite types
│
├── supabase/                   # Supabase configuration
│   ├── migrations/            # Database migrations
│   │   ├── 001_initial_schema.sql
│   │   ├── 002_personal_routes.sql
│   │   ├── 003_curated_routes.sql
│   │   └── 004_rls_policies.sql
│   ├── functions/             # Edge Functions
│   │   ├── kml-proxy/index.ts
│   │   └── share-proxy/index.ts
│   └── seed.sql               # Initial data seeding
│
├── tests/                      # Test files
│   ├── unit/                  # Vitest unit tests
│   │   ├── hooks/
│   │   ├── services/
│   │   └── utils/
│   ├── integration/           # React Testing Library
│   │   └── components/
│   └── e2e/                   # Playwright E2E tests
│       ├── walk.spec.ts
│       ├── replay.spec.ts
│       └── share.spec.ts
│
├── .env.example                # Environment variables template
├── .env.local                  # Local env (gitignored)
├── .gitignore
├── package.json
├── pnpm-lock.yaml             # or bun.lockb / yarn.lock
├── tsconfig.json
├── tsconfig.node.json
├── vite.config.ts
├── tailwind.config.js
├── postcss.config.js
├── playwright.config.ts
├── vitest.config.ts
└── README.md
```

---

## Data Flow Diagrams

### Walk Mode Flow

```
User clicks "Start Walk"
    ↓
Request GPS permission
    ↓
Start GPS polling (10s or 25m movement)
    ↓
Record waypoints → IndexedDB (cache)
    ↓
User adds memory → Capture location + content
    ↓
Photo upload → Supabase Storage → Get signed URL
    ↓
Save memory → personal_route_memories table
    ↓
User clicks "End Walk"
    ↓
Batch upload waypoints → personal_route_waypoints
    ↓
Create personal_route entry
    ↓
Navigate to Replay Mode
```

### Replay Mode Flow

```
User opens personal_route
    ↓
Query: route + waypoints + memories
    ↓
Compute timeline (min/max timestamps)
    ↓
User clicks "Replay"
    ↓
Start animation loop
    ↓
For each timestamp:
    - Draw path segment
    - Check for memory at timestamp
    - Show memory popup if exists
    - Update progress indicator
    ↓
Animation complete → Show share button
```

### Share Flow

```
User clicks "Share"
    ↓
Set visibility = 'unlisted' or 'public'
    ↓
Generate unique share_slug (nanoid)
    ↓
Copy URL: michi.app/shared/{slug}
    ↓
Sharee opens URL (no auth)
    ↓
Edge Function validates slug
    ↓
Query route via public_personal_routes view
    ↓
Generate signed URLs for photos (1-hour expiry)
    ↓
Render read-only replay
```

---

## Security Model

### Authentication
- Email/password via Supabase Auth
- Google OAuth via Supabase Auth
- JWT tokens stored in httpOnly cookies
- Session refresh handled by Supabase client

### Row Level Security (RLS)

| Table | Owner Read | Owner Write | Public Read | Anon Read |
|-------|-----------|-------------|-------------|-----------|
| personal_routes | ✓ | ✓ | ✗ | ✗ |
| personal_route_waypoints | ✓ | ✓ | ✗ | ✗ |
| personal_route_memories | ✓ | ✓ | ✗ | ✗ |
| curated_routes | ✓ | ✓ | ✓ | ✓ |
| public_personal_routes (view) | ✓ | ✗ | ✓ (unlisted) | ✓ (unlisted) |

### Edge Function Security

**kml-proxy:**
- JWT validation required
- `mid` parameter regex validation
- 5MB response size limit
- Content-Type validation (reject HTML)
- Rate limit: 10/hour, 50/day per user

**share-proxy:**
- Share slug validation
- Visibility check before returning data
- Signed URL generation with Postgres crypto
- 1-hour URL expiry
- IP-based rate limiting for anonymous: 100/hour

### Storage Security
- Private bucket for user photos
- Signed URLs for temporary access
- 2GB quota per user (free tier)
- User cannot access others' photos

---

## Performance Considerations

### GPS Tracking
- 10-second polling (balance: accuracy vs battery)
- 25-meter movement threshold (reduce redundant points)
- >50m accuracy filtering (exclude poor GPS)
- IndexedDB caching (offline resilience)

### Replay Animation
- Pre-compute timeline on load
- Use absolute timestamps for consistency
- Progressive path rendering (not all at once)
- Memory popup throttling (max 1 per 500ms)

### Data Queries
- Pattern-specific queries (JOIN for detail, simple for list)
- Indexed columns: `(personal_route_id, recorded_at)`
- Pagination for routes list
- Lazy loading for memories (>100)

### Photo Storage
- Resize before upload (max 1920px width)
- WebP format with JPEG fallback
- Progressive loading (blur-up placeholder)
- CDN caching via Supabase Storage

---

## Offline Strategy

### What Works Offline
- View last-viewed route (from IndexedDB)
- Add/edit stop notes (optimistic)
- Mark/unmark pinned (optimistic)
- Reorder stops (optimistic)

### What Doesn't Work Offline
- Map tiles (show "Offline mode" banner)
- GPS tracking (pauses, resumes when online)
- Route optimization (disabled)
- Import new KMLs (disabled)
- Upload photos (queued, retry when online)

### Sync Strategy
- IndexedDB is primary store
- Queue operations when offline
- Flush queue on reconnect
- Conflict resolution: last-write-wins by `updated_at`

---

## Testing Strategy

### Unit Tests (Vitest)
- GPS utilities (accuracy filtering, distance calc)
- Timeline computation (start/end, memory ordering)
- Theme detection (month to season mapping)
- Storage utilities (IndexedDB wrappers)

### Integration Tests (React Testing Library)
- Walk Mode (start, add memory, end)
- Replay Mode (playback, speed controls, timeline)
- Auth flows (login, signup, logout)
- Error states (GPS loss, upload fail)

### E2E Tests (Playwright)
- Complete walk cycle (start → walk → memories → end → replay)
- GPS loss and recovery
- Battery warning flow
- Share route and view anonymously
- Seasonal theme switching

### Security Tests
- RLS policy violations (owner vs others)
- Anonymous access boundaries
- Edge Function rate limiting
- Signed URL expiry

---

## Environment Variables

```bash
# Vite
VITE_MAPBOX_TOKEN=pk.xxx          # Mapbox public token
VITE_SUPABASE_URL=https://xxx     # Supabase project URL
VITE_SUPABASE_ANON_KEY=xxx        # Supabase anon key

# Supabase (via dashboard)
SUPABASE_SERVICE_ROLE_KEY=xxx     # For Edge Functions only
```

---

## Deployment Pipeline

```
git push to feature branch
    ↓
Open PR
    ↓
GitHub Actions runs:
  - TypeScript type-check
  - Vitest unit tests
  - React Testing Library tests
    ↓
PR approved and merged to develop
    ↓
Deploy to Vercel (preview)
    ↓
Merge develop to main
    ↓
GitHub Actions:
  - Full test suite (including E2E)
  - Build production bundle
    ↓
Auto-deploy to Vercel (production)
```
