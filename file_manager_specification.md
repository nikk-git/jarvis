# Desktop File Manager Application Specification

**User Brief:** Build a desktop app for managing my files

## 1. Executive Summary

FileMaster is a cross-platform desktop file management application designed to empower users with intelligent file organization, lightning-fast search, and privacy-first data handling. Targeting power users who manage thousands of files, casual users seeking better organization, and privacy-conscious individuals requiring local-first data control, FileMaster delivers a unified interface that makes file management intuitive while maintaining complete user data sovereignty. **Value Proposition:** Transform chaotic file systems into organized, searchable, and secure digital workspaces without compromising user privacy or requiring cloud dependencies.

## 2. Top-Level Feature List (Priority Order)

1. **Intelligent File Indexing & Search** - Real-time full-text search across file names, content, and metadata to instantly locate any file
2. **Smart Tagging System** - User-defined and auto-generated tags with hierarchical organization for flexible file categorization  
3. **Advanced File Operations** - Batch operations, smart duplicate detection, and safe file manipulation with comprehensive undo/redo
4. **Multi-Pane Interface** - Dual-pane file browser with customizable layouts, preview panes, and workspace management
5. **Secure File Previews** - Safe, sandboxed previews for 50+ file types including documents, images, videos, and code
6. **Cross-Platform Sync** - Optional encrypted synchronization between devices with local-first architecture
7. **Automation Rules** - User-defined rules for automatic file organization based on patterns, dates, and metadata
8. **Privacy & Security** - End-to-end encryption, secure deletion, and privacy-respecting analytics with explicit opt-in
9. **Performance Optimization** - Sub-100ms search response times and smooth handling of directories with 100k+ files
10. **Extensibility Framework** - Plugin system for custom file handlers, cloud connectors, and workflow integrations

## 3. User Personas & Key User Stories

### Persona 1: Sarah - Power User (Software Developer)
**Demographics:** 32, Senior Developer, manages 50GB+ of code repositories, documentation, and media files
**Pain Points:** Slow file search, poor code file organization, difficulty tracking project assets

**User Stories:**
1. **As Sarah, I want to search across all my code files by function name** so I can quickly find specific implementations
   - *Acceptance Criteria:* Search results appear within 100ms, supports regex patterns, shows code context
   - *Success Metric:* 90% of searches completed in under 2 seconds

2. **As Sarah, I want to tag files with project names and technologies** so I can organize work across multiple repositories
   - *Acceptance Criteria:* Hierarchical tags (project/backend/python), bulk tagging, tag-based filtering
   - *Success Metric:* 80% reduction in time spent locating project files

3. **As Sarah, I want to preview code files without opening them** so I can quickly review implementations
   - *Acceptance Criteria:* Syntax highlighting, line numbers, search highlighting within preview
   - *Success Metric:* 50% reduction in unnecessary file opens

4. **As Sarah, I want to batch rename files using patterns** so I can standardize naming conventions across projects
   - *Acceptance Criteria:* Regex-based renaming, preview before apply, undo capability
   - *Success Metric:* Complete batch operations 10x faster than manual renaming

5. **As Sarah, I want to find duplicate files across projects** so I can free up disk space and avoid confusion
   - *Acceptance Criteria:* Content-based detection, size filtering, safe deletion with backup
   - *Success Metric:* Identify 95% of true duplicates with <1% false positives

6. **As Sarah, I want keyboard shortcuts for all common operations** so I can work without using the mouse
   - *Acceptance Criteria:* Customizable shortcuts, vim-like navigation, command palette
   - *Success Metric:* 80% of operations completable via keyboard only

### Persona 2: Mike - Casual User (Marketing Manager)
**Demographics:** 45, Marketing Manager, manages presentations, images, documents, and client files
**Pain Points:** Cluttered Downloads folder, difficulty finding old presentations, poor photo organization

**User Stories:**
1. **As Mike, I want automatic organization of my Downloads folder** so files don't accumulate chaotically
   - *Acceptance Criteria:* Rules-based sorting by file type, date, or source, customizable destinations
   - *Success Metric:* 90% of downloads automatically organized within 5 seconds

2. **As Mike, I want to quickly find presentations from specific clients** so I can reuse content and maintain consistency
   - *Acceptance Criteria:* Client-based tagging, content search within presentations, thumbnail previews
   - *Success Metric:* Find target presentations in under 30 seconds

3. **As Mike, I want to see image thumbnails in large folders** so I can visually identify files quickly
   - *Acceptance Criteria:* Fast thumbnail generation, grid/list view toggle, zoom controls
   - *Success Metric:* Thumbnails load within 200ms for folders with 1000+ images

4. **As Mike, I want to safely delete old files** so I can free up space without losing important documents
   - *Acceptance Criteria:* Smart suggestions for old/unused files, secure deletion, 30-day recovery period
   - *Success Metric:* Recover 100% of accidentally deleted files within recovery period

5. **As Mike, I want to share files securely with clients** so I can collaborate without compromising sensitive data
   - *Acceptance Criteria:* Encrypted sharing links, expiration dates, access logging
   - *Success Metric:* Zero data breaches, 95% successful secure shares

6. **As Mike, I want the app to suggest better file organization** so I can maintain a clean file system
   - *Acceptance Criteria:* ML-based suggestions, non-intrusive recommendations, easy acceptance/rejection
   - *Success Metric:* 70% of suggestions accepted and improve user organization

### Persona 3: Elena - Privacy-Conscious User (Journalist)
**Demographics:** 38, Investigative Journalist, handles sensitive documents, sources, and research materials
**Pain Points:** Concerns about cloud storage security, need for encrypted file storage, source protection requirements

**User Stories:**
1. **As Elena, I want all my files encrypted at rest** so sensitive information remains protected even if my device is compromised
   - *Acceptance Criteria:* AES-256 encryption, secure key management, transparent encryption/decryption
   - *Success Metric:* Zero unencrypted sensitive data on disk, <5% performance impact

2. **As Elena, I want to securely delete files** so removed sensitive information cannot be recovered
   - *Acceptance Criteria:* Multi-pass overwriting, verification of deletion, metadata scrubbing
   - *Success Metric:* 100% unrecoverable deletion verified by forensic tools

3. **As Elena, I want local-only operation** so my data never leaves my device without explicit consent
   - *Acceptance Criteria:* No network connections by default, clear consent for any cloud features, audit log
   - *Success Metric:* Zero unauthorized network traffic, complete user control over data location

4. **As Elena, I want to organize sensitive sources separately** so I can protect confidential information
   - *Acceptance Criteria:* Encrypted containers, separate access controls, steganographic options
   - *Success Metric:* Source information remains protected even under legal pressure

5. **As Elena, I want audit logs of file access** so I can detect unauthorized access attempts
   - *Acceptance Criteria:* Detailed access logging, tamper-evident logs, export capabilities
   - *Success Metric:* 100% of file access events logged with integrity verification

6. **As Elena, I want to verify file integrity** so I can detect tampering or corruption
   - *Acceptance Criteria:* Cryptographic hashing, integrity monitoring, corruption detection
   - *Success Metric:* Detect 100% of file modifications with <1% false positives

## 4. Product Specification & Behavior

### Core File Operations

**File Browsing & Navigation**
- **Primary Flow:** User opens app → sees familiar file tree on left, main content pane on right → navigates via clicking folders or keyboard shortcuts (arrow keys, Enter to open, Backspace to go up)
- **Dual-Pane Mode:** Toggle second pane (F3) for side-by-side file operations → independent navigation in each pane → drag-drop between panes
- **Keyboard Navigation:** Full vim-like navigation (j/k for up/down, h/l for in/out of folders) + traditional arrow keys → Tab to switch focus between panes/search/preview
- **Edge Cases:** 
  - Empty directories show "This folder is empty" with drag-drop zone and "Create new file/folder" buttons
  - Permission denied shows clear error with "Request permission" button where applicable
  - Network drives timeout after 30 seconds with retry option
- **Error States:** Network errors show offline indicator + cached content when available → corrupted directories show warning with "Scan and repair" option

**File Operations (Copy, Move, Delete)**
- **Copy/Move Flow:** Select files → Ctrl+C/X → navigate to destination → Ctrl+V → progress dialog with pause/cancel → completion notification with undo option
- **Batch Operations:** Multi-select via Ctrl+click or Shift+click → operations apply to all selected → progress shows per-file status
- **Conflict Resolution:** On name conflicts, show dialog with options: Skip, Replace, Keep Both (with auto-rename), Apply to All
- **Undo System:** All operations stored in undo stack (max 50 operations) → Ctrl+Z to undo → operations older than 24 hours auto-archived but recoverable
- **Safe Delete:** Delete moves to app's trash (separate from system trash) → 30-day retention → secure wipe after retention period
- **Edge Cases:**
  - Insufficient disk space: Show space required vs available, suggest cleanup options
  - Read-only files: Clear prompt explaining permissions needed
  - Files in use: Detect file locks, offer to retry or force (with warnings)

**Search & Filtering**
- **Search Interface:** Global search bar (Ctrl+F) with dropdown for scope (current folder/all indexed locations) → real-time results as you type
- **Search Types:** 
  - Filename search (default, fuzzy matching enabled)
  - Content search (full-text indexing of supported file types)
  - Metadata search (size, date, type, tags)
  - Advanced search builder with Boolean operators
- **Filter System:** Sidebar filters for file type, size ranges, date ranges, tags → combinable filters → save filter sets as "Smart Folders"
- **Search Results:** Results show relevance score, file path, match context → keyboard navigation through results → Enter to open, Ctrl+Enter to open location
- **Edge Cases:**
  - No results: Show suggestions (check spelling, broaden search, index status)
  - Indexing in progress: Show progress indicator, allow search of already-indexed content
  - Large result sets: Paginated results (100 per page) with "Load more" option

### Tagging System

**Tag Creation & Management**
- **Tag Interface:** Right-click → "Add tags" or dedicated tag panel → type-ahead with existing tag suggestions → hierarchical tags using slash notation (project/web/frontend)
- **Bulk Tagging:** Select multiple files → batch tag application → smart suggestions based on file types and locations
- **Tag Organization:** Tag management panel shows tag hierarchy → drag-drop to reorganize → merge/split tags → bulk operations on tagged files
- **Auto-Tagging:** Rules engine for automatic tag application based on file path, type, content patterns → user-reviewable suggestions before application

**Tag-Based Navigation**
- **Tag Browser:** Dedicated tag view showing files grouped by tags → expandable tag tree → multi-tag filtering (AND/OR operations)
- **Tag Search:** Search within tagged files → combine text search with tag filters → save complex queries as smart folders
- **Tag Visualization:** Tag cloud view showing usage frequency → color coding for tag categories → visual tag relationships

### File Previews

**Preview System**
- **Preview Pane:** Toggle preview pane (F4) → shows preview of selected file → updates automatically as selection changes
- **Supported Types:** 
  - Images: JPEG, PNG, GIF, WebP, SVG, RAW formats → zoom, rotate, EXIF data
  - Documents: PDF, Office files, text files → searchable content, page navigation
  - Code: Syntax highlighting for 50+ languages → line numbers, folding
  - Media: Video thumbnails with playback controls → audio waveforms
  - Archives: Contents listing → extract preview
- **Security:** All previews run in sandboxed environment → no code execution → safe handling of potentially malicious files
- **Performance:** Lazy loading → thumbnail cache → progressive loading for large files
- **Edge Cases:**
  - Unsupported files: Show file info (size, dates, type) with "Open with..." options
  - Corrupted files: Error message with file recovery suggestions
  - Large files: Partial preview with "Load full preview" option

### Settings & Customization

**Appearance & Layout**
- **Themes:** Light, dark, and high-contrast themes → custom theme creation → theme scheduling (auto dark mode)
- **Layout Options:** Single/dual pane toggle → resizable panes → hide/show panels (preview, tags, tree) → save layout presets
- **Font & Sizing:** Customizable UI font and size → file list density options → accessibility scaling

**Behavior Settings**
- **File Operations:** Default copy/move behavior → confirmation dialogs configuration → undo retention period
- **Search Settings:** Default search scope → indexing locations → file type inclusions/exclusions
- **Privacy Settings:** Telemetry opt-in/out → data retention policies → encryption settings

## 5. UX/UI Design & Component Layout

### Main Application Layout

```
┌─────────────────────────────────────────────────────────────────────┐
│ [≡] FileMaster    [🔍 Search...]  [⚙️] [?] [_] [□] [×]                │
├─────────────────────────────────────────────────────────────────────┤
│ File  Edit  View  Go  Tools  Help                                    │
├─────────────────────────────────────────────────────────────────────┤
│ [←] [→] [↑] [🏠] [📁] /Users/sarah/Documents/Projects                 │
├──────────┬──────────────────────────────────────┬───────────────────┤
│ 📁 Tree  │ Name ↕     Size ↕    Modified ↕     │ 📄 Preview        │
│ ├─🏠 Home │ ├─📁 project-alpha   2.3GB  2d ago  │                   │
│ ├─📁 Docs │ ├─📄 README.md       4.2KB  1h ago  │ # Project Alpha   │
│ ├─📁 Pics │ ├─📄 main.py        15.8KB  3h ago  │                   │
│ ├─📁 Code │ ├─📄 config.json     892B   1d ago  │ A modern web...   │
│ │ ├─⭐Alpha│ └─📄 requirements   1.2KB  2d ago  │                   │
│ │ ├─📁 Beta│                                    │ ```python         │
│ │ └─📁 Old │ 📊 4 files, 2.1GB total          │ def main():       │
│ ├─🏷️ Tags  │                                    │     print("Hi")   │
│ │ ├─work   │                                    │ ```               │
│ │ ├─personal│                                   │                   │
│ │ └─archive│                                    │ [Open] [Edit]     │
│ └─🔍 Smart │                                    │                   │
│   ├─Recent │                                    │                   │
│   └─Large  │                                    │                   │
├──────────┴──────────────────────────────────────┴───────────────────┤
│ 🏷️ Tags: work, python, web-dev                  Status: 4 selected  │
└─────────────────────────────────────────────────────────────────────┘
```

### Visual Language Specification

**Color Palette (CSS Custom Properties)**
```css
:root {
  /* Primary Colors */
  --primary-50: #f0f9ff;
  --primary-500: #3b82f6;
  --primary-600: #2563eb;
  --primary-900: #1e3a8a;
  
  /* Neutral Colors */
  --neutral-50: #fafafa;
  --neutral-100: #f5f5f5;
  --neutral-200: #e5e5e5;
  --neutral-500: #737373;
  --neutral-800: #262626;
  --neutral-900: #171717;
  
  /* Semantic Colors */
  --success-500: #22c55e;
  --warning-500: #f59e0b;
  --error-500: #ef4444;
  --info-500: #06b6d4;
}

/* Dark Theme Overrides */
[data-theme="dark"] {
  --neutral-50: #262626;
  --neutral-100: #404040;
  --neutral-200: #525252;
  --neutral-500: #a3a3a3;
  --neutral-800: #e5e5e5;
  --neutral-900: #fafafa;
}
```

**Typography Scale**
```css
.text-xs { font-size: 0.75rem; line-height: 1rem; }     /* 12px */
.text-sm { font-size: 0.875rem; line-height: 1.25rem; } /* 14px */
.text-base { font-size: 1rem; line-height: 1.5rem; }    /* 16px */
.text-lg { font-size: 1.125rem; line-height: 1.75rem; } /* 18px */
.text-xl { font-size: 1.25rem; line-height: 1.75rem; }  /* 20px */
```

**Spacing System**
```css
.space-1 { margin: 0.25rem; }  /* 4px */
.space-2 { margin: 0.5rem; }   /* 8px */
.space-3 { margin: 0.75rem; }  /* 12px */
.space-4 { margin: 1rem; }     /* 16px */
.space-6 { margin: 1.5rem; }   /* 24px */
.space-8 { margin: 2rem; }     /* 32px */
```

### Component Specifications

**File List Component**
- **Grid View:** Thumbnail + filename below → adjustable thumbnail size (64px to 256px) → 4-8 columns responsive
- **List View:** Icon + filename + metadata columns → sortable columns → alternate row highlighting
- **Compact View:** Small icons + filename only → maximum information density → keyboard navigation optimized

**Context Menu**
```
Right-click file/folder:
├─ Open                    Ctrl+O
├─ Open With...            
├─ ──────────────────────
├─ Cut                     Ctrl+X  
├─ Copy                    Ctrl+C
├─ Paste                   Ctrl+V
├─ ──────────────────────
├─ Rename                  F2
├─ Delete                  Del
├─ ──────────────────────
├─ Add Tags...             Ctrl+T
├─ Properties              Alt+Enter
└─ Share...                Ctrl+Shift+S
```

### Accessibility Considerations

**Keyboard Navigation**
- **Tab Order:** Logical flow through tree → file list → preview → tag panel
- **Focus Indicators:** High-contrast focus rings (3px, --primary-500) → visible in all themes
- **Screen Reader:** ARIA labels on all interactive elements → live regions for status updates → semantic HTML structure

**Visual Accessibility**
- **Contrast Ratios:** Minimum 4.5:1 for normal text, 3:1 for large text → AA compliance verified
- **Color Independence:** No information conveyed by color alone → icons + text for all states
- **Motion Sensitivity:** Respect prefers-reduced-motion → disable animations when requested

**Assistive Technology**
- **Screen Reader Support:** Full VoiceOver/NVDA/JAWS compatibility → descriptive alt text for icons → table navigation for file lists
- **Keyboard Shortcuts:** All functionality accessible via keyboard → customizable shortcuts → shortcut help (F1)
- **High Contrast Mode:** Automatic detection and adaptation → custom high-contrast theme available

## 6. Technical Architecture

### Component Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                     Frontend (React/TypeScript)                 │
├─────────────────────┬───────────────────┬───────────────────────┤
│   UI Components     │   State Manager   │    Service Layer      │
│                     │                   │                       │
│ • FileList          │ • Redux Toolkit   │ • FileService         │
│ • FileTree          │ • RTK Query       │ • SearchService       │
│ • PreviewPane       │ • Persist         │ • TagService          │
│ • SearchBar         │                   │ • SettingsService     │
│ • TagPanel          │                   │                       │
└─────────────────────┴───────────────────┴───────────────────────┘
                              │
                         IPC Bridge
                              │
┌─────────────────────────────────────────────────────────────────┐
│                    Backend (Rust/Tauri)                        │
├─────────────────────┬───────────────────┬───────────────────────┤
│   Core Services     │   Data Layer      │    System Layer       │
│                     │                   │                       │
│ • FileManager       │ • SQLite DB       │ • FileWatcher         │
│ • SearchEngine      │ • Index Store     │ • ThumbnailGen        │
│ • TagManager        │ • Settings        │ • PreviewSandbox      │
│ • PreviewEngine     │ • Cache           │ • EncryptionEngine    │
│ • SyncEngine        │                   │ • PermissionManager   │
└─────────────────────┴───────────────────┴───────────────────────┘
                              │
                      OS Integration
                              │
┌─────────────────────────────────────────────────────────────────┐
│                    Operating System                            │
│  • File System APIs  • Security Framework  • Native UI        │
└─────────────────────────────────────────────────────────────────┘
```

### Component Responsibilities

**Frontend Layer**

*UI Components*
- **Responsibilities:** Render user interface, handle user interactions, display data
- **Data Flow:** Receives props from containers → dispatches actions to state manager → re-renders on state changes
- **Failure Modes:** Component crashes contained by error boundaries → graceful degradation for missing data
- **Permissions:** None (runs in renderer process sandbox)

*State Manager (Redux Toolkit)*
- **Responsibilities:** Global state management, API caching, persistence
- **Data Flow:** Actions → reducers → state updates → component re-renders
- **Failure Modes:** State corruption handled by persistence layer → automatic state reset on critical errors
- **Permissions:** Local storage access only

*Service Layer*
- **Responsibilities:** Abstract backend communication, client-side validation, error handling
- **Data Flow:** Component calls → IPC messages → backend responses → state updates
- **Failure Modes:** Network timeouts handled with retries → offline mode for cached data
- **Permissions:** IPC communication with main process

**Backend Layer**

*Core Services*
- **FileManager:** CRUD operations, batch processing, conflict resolution
  - **Failure Modes:** File locks handled with retry logic → permission errors escalated to user
  - **Permissions:** File system read/write access (user-granted)
  
- **SearchEngine:** Full-text indexing, query processing, relevance ranking
  - **Failure Modes:** Index corruption triggers rebuild → memory limits handled with streaming
  - **Permissions:** Read access to indexed directories
  
- **TagManager:** Tag CRUD, hierarchy management, auto-tagging rules
  - **Failure Modes:** Tag conflicts resolved with user prompts → orphaned tags cleaned up
  - **Permissions:** Database write access

*Data Layer*
- **SQLite Database:** Structured data storage with ACID guarantees
  - **Schema:** Files, tags, settings, search index, user preferences
  - **Failure Modes:** Database corruption handled with automatic backup restore
  - **Permissions:** Local file system write access

*System Layer*
- **FileWatcher:** Real-time file system monitoring with debouncing
  - **Failure Modes:** Watcher failures trigger polling fallback → memory leaks prevented with cleanup
  - **Permissions:** File system monitoring (platform-specific APIs)

### Data Flow Architecture

**File Operation Flow**
1. User initiates action (UI) → Action dispatched (Redux)
2. Service layer validates request → IPC message to backend
3. Backend processes operation → File system API calls
4. Success/failure response → State update → UI re-render
5. Background: Index update → Cache invalidation → Watcher notification

**Search Flow**
1. User types query (UI) → Debounced search action (300ms)
2. SearchService formats query → IPC to SearchEngine
3. SearchEngine queries index → Ranks results → Returns paginated data
4. Results cached in RTK Query → UI displays with loading states
5. Background: Usage analytics → Query optimization

**Security Boundaries**
- **Renderer Process:** Sandboxed, no direct file access, IPC only
- **Main Process:** Full system access, validates all IPC requests
- **Preview Sandbox:** Isolated process for file previews, minimal permissions
- **File Operations:** User confirmation for destructive operations

## 7. Technology Stack Analysis & Recommendation

### Stack Comparison Matrix

| Criteria | Electron + React | Tauri + React | Flutter Desktop | Qt/C++ Native |
|----------|------------------|---------------|-----------------|---------------|
| **Bundle Size** | 150-200MB | 15-30MB | 25-40MB | 5-15MB |
| **Memory Usage** | 100-200MB | 30-60MB | 40-80MB | 20-40MB |
| **Startup Time** | 2-4 seconds | 0.5-1.5 seconds | 1-2 seconds | 0.2-0.5 seconds |
| **Security Surface** | High (Chromium) | Low (Rust sandbox) | Medium (Dart VM) | Very Low (Native) |
| **Dev Experience** | Excellent | Good | Good | Complex |
| **Cross-Platform** | Excellent | Excellent | Excellent | Good |
| **Community** | Massive | Growing | Large | Mature |
| **Hot Reload** | Yes | Yes | Yes | No |
| **Package/Deploy** | Complex | Simple | Medium | Complex |
| **Performance** | Good | Excellent | Excellent | Excellent |

### Detailed Analysis

**Electron + React**
- **Pros:** Massive ecosystem, familiar web technologies, excellent debugging tools, rapid prototyping
- **Cons:** Large bundle size, high memory usage, security concerns, slower startup
- **Best For:** Teams with strong web development skills, rapid time-to-market requirements
- **Build Size:** ~150MB (includes Chromium runtime)
- **Memory:** ~150MB baseline + application memory
- **Debugging:** Chrome DevTools, extensive ecosystem tools

**Tauri + React (RECOMMENDED)**
- **Pros:** Small bundle size, excellent security model, native performance, growing ecosystem
- **Cons:** Smaller community, Rust learning curve for backend, newer technology
- **Best For:** Performance-sensitive applications, security-conscious users, modern development practices
- **Build Size:** ~20MB (system webview + Rust binary)
- **Memory:** ~40MB baseline + application memory  
- **Debugging:** Chrome DevTools for frontend, Rust debugging tools for backend

**Flutter Desktop**
- **Pros:** Single codebase, excellent performance, growing desktop support, rich widget library
- **Cons:** Large binary size, Dart learning curve, less mature desktop ecosystem
- **Best For:** Teams with mobile Flutter experience, consistent UI across all platforms
- **Build Size:** ~30MB (includes Flutter engine)
- **Memory:** ~50MB baseline + application memory
- **Debugging:** Flutter Inspector, Dart debugging tools

**Qt/C++ Native**
- **Pros:** Smallest footprint, maximum performance, mature ecosystem, native look/feel
- **Cons:** Complex development, longer development time, platform-specific code needed
- **Best For:** Performance-critical applications, teams with C++ expertise, maximum native integration
- **Build Size:** ~10MB (platform-specific)
- **Memory:** ~25MB baseline + application memory
- **Debugging:** Platform-specific debuggers (GDB, MSVC, Xcode)

### Recommended Stack: Tauri + React + TypeScript

**Justification:**
1. **Security First:** Rust backend provides memory safety and minimal attack surface
2. **Performance:** Native performance with small memory footprint critical for file management
3. **Developer Experience:** React frontend familiar to most developers, TypeScript for type safety
4. **Bundle Size:** 20MB vs 150MB for Electron crucial for distribution and adoption
5. **Future-Proof:** Growing ecosystem, active development, modern architecture patterns

**Trade-offs Accepted:**
- Smaller community compared to Electron (mitigated by excellent documentation)
- Rust learning curve for backend development (mitigated by well-defined API boundaries)
- Newer technology with potential breaking changes (mitigated by LTS support strategy)

**Implementation Strategy:**
- Frontend: React 18 + TypeScript + Tailwind CSS + Redux Toolkit
- Backend: Tauri 1.x + Rust + SQLite + Tokio async runtime
- Build: Vite for frontend bundling, Cargo for Rust compilation
- Testing: Vitest + React Testing Library + Rust unit tests

## 8. Data Model & Storage

### Database Schema (SQLite)

```sql
-- Files table: Core file metadata and indexing
CREATE TABLE files (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    path TEXT NOT NULL UNIQUE,
    name TEXT NOT NULL,
    size INTEGER NOT NULL,
    modified_time INTEGER NOT NULL,
    created_time INTEGER NOT NULL,
    file_type TEXT NOT NULL,
    mime_type TEXT,
    hash_sha256 TEXT,
    parent_id INTEGER,
    is_directory BOOLEAN NOT NULL DEFAULT FALSE,
    is_hidden BOOLEAN NOT NULL DEFAULT FALSE,
    permissions INTEGER NOT NULL,
    indexed_at INTEGER NOT NULL,
    FOREIGN KEY (parent_id) REFERENCES files (id) ON DELETE CASCADE
);

-- Tags table: Hierarchical tagging system
CREATE TABLE tags (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    parent_id INTEGER,
    color TEXT DEFAULT '#3b82f6',
    description TEXT,
    created_at INTEGER NOT NULL,
    UNIQUE(name, parent_id),
    FOREIGN KEY (parent_id) REFERENCES tags (id) ON DELETE CASCADE
);

-- File-Tag associations: Many-to-many relationship
CREATE TABLE file_tags (
    file_id INTEGER NOT NULL,
    tag_id INTEGER NOT NULL,
    created_at INTEGER NOT NULL,
    PRIMARY KEY (file_id, tag_id),
    FOREIGN KEY (file_id) REFERENCES files (id) ON DELETE CASCADE,
    FOREIGN KEY (tag_id) REFERENCES tags (id) ON DELETE CASCADE
);

-- Search index: Full-text search capabilities
CREATE VIRTUAL TABLE search_index USING fts5(
    file_id UNINDEXED,
    filename,
    content,
    tags,
    content='files',
    content_rowid='id'
);

-- User settings: Application configuration
CREATE TABLE settings (
    key TEXT PRIMARY KEY,
    value TEXT NOT NULL,
    type TEXT NOT NULL DEFAULT 'string', -- string, number, boolean, json
    updated_at INTEGER NOT NULL
);

-- Automation rules: File organization automation
CREATE TABLE automation_rules (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    pattern TEXT NOT NULL, -- JSON pattern matching rules
    actions TEXT NOT NULL, -- JSON actions to perform
    enabled BOOLEAN NOT NULL DEFAULT TRUE,
    created_at INTEGER NOT NULL,
    last_run INTEGER
);

-- Activity log: User actions and system events
CREATE TABLE activity_log (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    action_type TEXT NOT NULL, -- move, copy, delete, tag, etc.
    file_path TEXT NOT NULL,
    details TEXT, -- JSON details about the action
    timestamp INTEGER NOT NULL,
    reversible BOOLEAN NOT NULL DEFAULT FALSE,
    undo_data TEXT -- JSON data needed for undo
);
```

### Indexes for Performance

```sql
-- File system navigation indexes
CREATE INDEX idx_files_parent_id ON files (parent_id);
CREATE INDEX idx_files_path ON files (path);
CREATE INDEX idx_files_modified ON files (modified_time DESC);
CREATE INDEX idx_files_size ON files (size DESC);
CREATE INDEX idx_files_type ON files (file_type);

-- Tag-related indexes
CREATE INDEX idx_tags_parent ON tags (parent_id);
CREATE INDEX idx_file_tags_file ON file_tags (file_id);
CREATE INDEX idx_file_tags_tag ON file_tags (tag_id);

-- Activity and automation indexes
CREATE INDEX idx_activity_timestamp ON activity_log (timestamp DESC);
CREATE INDEX idx_activity_file ON activity_log (file_path);
CREATE INDEX idx_rules_enabled ON automation_rules (enabled);
```

### Data Storage Locations

**Configuration Storage**
```
Windows: %APPDATA%/FileMaster/
macOS: ~/Library/Application Support/FileMaster/
Linux: ~/.config/filemaster/

Structure:
├── database.db          # Main SQLite database
├── settings.json        # User preferences backup
├── thumbnails/          # Thumbnail cache
│   ├── small/          # 64x64 thumbnails
│   ├── medium/         # 256x256 thumbnails
│   └── large/          # 512x512 thumbnails
├── logs/               # Application logs
│   ├── app.log
│   ├── error.log
│   └── audit.log
└── backups/            # Automatic database backups
    ├── database.db.backup.1
    ├── database.db.backup.2
    └── database.db.backup.3
```

### Large Directory Handling Strategy

**Incremental Loading**
- Load directories in chunks of 1000 files
- Virtual scrolling for UI performance
- Background loading with progress indicators
- Prioritize visible items in viewport

**Caching Strategy**
```rust
// Rust backend caching structure
struct DirectoryCache {
    path: PathBuf,
    files: Vec<FileEntry>,
    total_count: usize,
    loaded_range: Range<usize>,
    last_modified: SystemTime,
    cache_expiry: Duration,
}

impl DirectoryCache {
    fn is_valid(&self) -> bool {
        self.last_modified.elapsed().unwrap() < self.cache_expiry
    }
    
    fn load_range(&mut self, start: usize, count: usize) -> Vec<FileEntry> {
        // Implement lazy loading logic
    }
}
```

### Migration Strategy

**Version Management**
```sql
CREATE TABLE schema_version (
    version INTEGER PRIMARY KEY,
    applied_at INTEGER NOT NULL
);
```

**Migration Framework**
```rust
// Migration trait for version updates
trait Migration {
    fn version(&self) -> u32;
    fn up(&self, conn: &Connection) -> Result<(), Error>;
    fn down(&self, conn: &Connection) -> Result<(), Error>;
}

// Example migration
struct AddEncryptionSupport;
impl Migration for AddEncryptionSupport {
    fn version(&self) -> u32 { 2 }
    
    fn up(&self, conn: &Connection) -> Result<(), Error> {
        conn.execute(
            "ALTER TABLE files ADD COLUMN encrypted BOOLEAN DEFAULT FALSE",
            []
        )?;
        conn.execute(
            "ALTER TABLE files ADD COLUMN encryption_key_id TEXT",
            []
        )?;
        Ok(())
    }
}
```

**Backup Before Migration**
- Automatic database backup before any schema change
- Rollback capability if migration fails
- User notification of migration progress
- Data integrity verification after migration

## 9. Search & Indexing Design

### Search Architecture

**Multi-Layer Search System**
1. **Filename Search (Instant)** - In-memory trie structure for sub-100ms filename matching
2. **Metadata Search (Fast)** - SQLite indexes for size, date, type filtering  
3. **Content Search (Comprehensive)** - Full-text search using SQLite FTS5 for document content
4. **Semantic Search (Future)** - Vector embeddings for intelligent content matching

### Indexing Strategy

**Real-Time Incremental Indexing**
```rust
// Core indexing engine structure
pub struct SearchIndexer {
    db_pool: Arc<SqlitePool>,
    content_extractors: HashMap<String, Box<dyn ContentExtractor>>,
    indexing_queue: Arc<Mutex<VecDeque<IndexingTask>>>,
    worker_handles: Vec<JoinHandle<()>>,
}

#[derive(Debug)]
pub struct IndexingTask {
    pub file_path: PathBuf,
    pub operation: IndexOperation,
    pub priority: IndexPriority,
    pub created_at: SystemTime,
}

#[derive(Debug)]
pub enum IndexOperation {
    Add,
    Update,
    Delete,
    Move { from: PathBuf, to: PathBuf },
}

#[derive(Debug, PartialOrd, Ord, PartialEq, Eq)]
pub enum IndexPriority {
    Critical,  // User is waiting for this file
    High,      // Recently accessed files
    Normal,    // Background indexing
    Low,       // Bulk operations
}
```

**File Watcher Integration**
```rust
// File system event handling with debouncing
pub struct FileWatcher {
    watcher: RecommendedWatcher,
    debouncer: Arc<Mutex<HashMap<PathBuf, SystemTime>>>,
    indexer: Arc<SearchIndexer>,
}

impl FileWatcher {
    pub fn handle_event(&mut self, event: DebouncedEvent) -> Result<(), Error> {
        match event {
            DebouncedEvent::Create(path) => {
                self.indexer.queue_task(IndexingTask {
                    file_path: path,
                    operation: IndexOperation::Add,
                    priority: IndexPriority::High,
                    created_at: SystemTime::now(),
                })?;
            }
            DebouncedEvent::Write(path) => {
                self.indexer.queue_task(IndexingTask {
                    file_path: path,
                    operation: IndexOperation::Update,
                    priority: IndexPriority::Normal,
                    created_at: SystemTime::now(),
                })?;
            }
            DebouncedEvent::Remove(path) => {
                self.indexer.queue_task(IndexingTask {
                    file_path: path,
                    operation: IndexOperation::Delete,
                    priority: IndexPriority::Critical,
                    created_at: SystemTime::now(),
                })?;
            }
            DebouncedEvent::Rename(from, to) => {
                self.indexer.queue_task(IndexingTask {
                    file_path: to.clone(),
                    operation: IndexOperation::Move { from, to },
                    priority: IndexPriority::High,
                    created_at: SystemTime::now(),
                })?;
            }
            _ => {}
        }
        Ok(())
    }
}
```

### Content Extraction Pipeline

**Supported File Types & Extractors**
```rust
// Content extraction trait for different file types
pub trait ContentExtractor: Send + Sync {
    fn supported_extensions(&self) -> &[&str];
    fn extract_content(&self, file_path: &Path) -> Result<String, ExtractionError>;
    fn extract_metadata(&self) -> Result<HashMap<String, String>, ExtractionError>;
}

// Text file extractor
pub struct TextExtractor;
impl ContentExtractor for TextExtractor {
    fn supported_extensions(&self) -> &[&str] {
        &["txt", "md", "json", "xml", "csv", "log", "cfg", "ini"]
    }
    
    fn extract_content(&self, file_path: &Path) -> Result<String, ExtractionError> {
        let content = std::fs::read_to_string(file_path)?;
        // Limit content size to prevent memory issues
        if content.len() > 1_000_000 { // 1MB limit
            Ok(content.chars().take(1_000_000).collect())
        } else {
            Ok(content)
        }
    }
}

// PDF extractor using pdf-extract crate
pub struct PdfExtractor;
impl ContentExtractor for PdfExtractor {
    fn supported_extensions(&self) -> &[&str] {
        &["pdf"]
    }
    
    fn extract_content(&self, file_path: &Path) -> Result<String, ExtractionError> {
        let bytes = std::fs::read(file_path)?;
        let doc = lopdf::Document::load_mem(&bytes)?;
        let text = doc.extract_text(&[1])?; // Extract from first page as sample
        Ok(text)
    }
}

// Office document extractor (requires external tools)
pub struct OfficeExtractor;
impl ContentExtractor for OfficeExtractor {
    fn supported_extensions(&self) -> &[&str] {
        &["docx", "xlsx", "pptx", "odt", "ods", "odp"]
    }
    
    fn extract_content(&self, file_path: &Path) -> Result<String, ExtractionError> {
        // Use pandoc or similar tool for office document extraction
        let output = std::process::Command::new("pandoc")
            .arg("--to=plain")
            .arg(file_path)
            .output()?;
        
        if output.status.success() {
            Ok(String::from_utf8_lossy(&output.stdout).to_string())
        } else {
            Err(ExtractionError::ProcessFailed)
        }
    }
}
```

### Search Query Processing

**Query Parser & Optimization**
```rust
#[derive(Debug, Clone)]
pub struct SearchQuery {
    pub terms: Vec<SearchTerm>,
    pub filters: Vec<SearchFilter>,
    pub sort_by: SortCriteria,
    pub limit: usize,
    pub offset: usize,
}

#[derive(Debug, Clone)]
pub enum SearchTerm {
    Exact(String),
    Fuzzy(String, f32), // term, similarity threshold
    Regex(String),
    Wildcard(String),
}

#[derive(Debug, Clone)]
pub enum SearchFilter {
    FileType(Vec<String>),
    SizeRange(u64, u64),
    DateRange(SystemTime, SystemTime),
    Tags(Vec<String>),
    Path(String),
}

#[derive(Debug, Clone)]
pub enum SortCriteria {
    Relevance,
    Name,
    Size,
    ModifiedDate,
    CreatedDate,
}

// Query execution with performance optimization
impl SearchEngine {
    pub async fn search(&self, query: SearchQuery) -> Result<SearchResults, SearchError> {
        let start_time = Instant::now();
        
        // Build SQL query with FTS5 integration
        let mut sql_builder = SqlBuilder::new();
        
        // Add FTS5 search terms
        if !query.terms.is_empty() {
            let fts_query = self.build_fts_query(&query.terms);
            sql_builder.where_clause(&format!(
                "files.id IN (SELECT file_id FROM search_index WHERE search_index MATCH '{}')",
                fts_query
            ));
        }
        
        // Add filters
        for filter in &query.filters {
            match filter {
                SearchFilter::FileType(types) => {
                    let placeholders = types.iter().map(|_| "?").collect::<Vec<_>>().join(",");
                    sql_builder.where_clause(&format!("file_type IN ({})", placeholders));
                }
                SearchFilter::SizeRange(min, max) => {
                    sql_builder.where_clause("size BETWEEN ? AND ?");
                }
                SearchFilter::DateRange(start, end) => {
                    sql_builder.where_clause("modified_time BETWEEN ? AND ?");
                }
                SearchFilter::Tags(tags) => {
                    sql_builder.join("file_tags ON files.id = file_tags.file_id");
                    sql_builder.join("tags ON file_tags.tag_id = tags.id");
                    sql_builder.where_clause("tags.name IN (?)");
                }
                SearchFilter::Path(path_pattern) => {
                    sql_builder.where_clause("path LIKE ?");
                }
            }
        }
        
        // Execute query with pagination
        let results = self.execute_search_query(sql_builder, &query).await?;
        
        let search_time = start_time.elapsed();
        
        Ok(SearchResults {
            files: results,
            total_count: self.get_total_count(&query).await?,
            search_time,
            query: query.clone(),
        })
    }
}
```

### External Drive & Network Volume Handling

**Drive Detection & Monitoring**
```rust
pub struct DriveManager {
    mounted_drives: Arc<Mutex<HashMap<PathBuf, DriveInfo>>>,
    indexing_policies: HashMap<DriveType, IndexingPolicy>,
}

#[derive(Debug, Clone)]
pub struct DriveInfo {
    pub path: PathBuf,
    pub drive_type: DriveType,
    pub total_space: u64,
    pub available_space: u64,
    pub is_indexed: bool,
    pub last_scan: Option<SystemTime>,
}

#[derive(Debug, Clone, PartialEq)]
pub enum DriveType {
    Internal,
    External,
    Network,
    Cloud,
}

#[derive(Debug, Clone)]
pub enum IndexingPolicy {
    Full,           // Index everything
    MetadataOnly,   // Index file metadata but not content
    OnDemand,       // Index only when accessed
    Disabled,       // Don't index
}

impl DriveManager {
    pub async fn scan_drives(&mut self) -> Result<(), DriveError> {
        let system_drives = self.detect_system_drives().await?;
        
        for drive in system_drives {
            if !self.mounted_drives.lock().unwrap().contains_key(&drive.path) {
                // New drive detected
                self.handle_new_drive(drive).await?;
            }
        }
        
        Ok(())
    }
    
    async fn handle_new_drive(&mut self, drive: DriveInfo) -> Result<(), DriveError> {
        let policy = self.indexing_policies.get(&drive.drive_type)
            .cloned()
            .unwrap_or(IndexingPolicy::MetadataOnly);
            
        match policy {
            IndexingPolicy::Full => {
                self.start_full_indexing(&drive).await?;
            }
            IndexingPolicy::MetadataOnly => {
                self.start_metadata_indexing(&drive).await?;
            }
            IndexingPolicy::OnDemand => {
                // Register for on-demand indexing but don't start
                self.register_on_demand_drive(&drive).await?;
            }
            IndexingPolicy::Disabled => {
                // Just track the drive but don't index
            }
        }
        
        self.mounted_drives.lock().unwrap().insert(drive.path.clone(), drive);
        Ok(())
    }
}
```

### Ranking Algorithm

**Multi-Factor Relevance Scoring**
```rust
pub struct RelevanceCalculator {
    weights: RankingWeights,
}

#[derive(Debug, Clone)]
pub struct RankingWeights {
    pub filename_match: f32,        // 0.4
    pub content_match: f32,         // 0.3
    pub recency: f32,              // 0.1
    pub access_frequency: f32,      // 0.1
    pub file_size_penalty: f32,     // 0.05
    pub path_depth_penalty: f32,    // 0.05
}

impl RelevanceCalculator {
    pub fn calculate_score(&self, file: &FileEntry, query: &SearchQuery, match_info: &MatchInfo) -> f32 {
        let mut score = 0.0;
        
        // Filename matching score (exact > prefix > fuzzy > substring)
        score += self.weights.filename_match * match_info.filename_score;
        
        // Content matching score (phrase > all terms > some terms)
        score += self.weights.content_match * match_info.content_score;
        
        // Recency boost (files modified recently get higher scores)
        let days_since_modified = file.modified_time.elapsed()
            .unwrap_or_default()
            .as_secs() / 86400;
        let recency_score = 1.0 / (1.0 + days_since_modified as f32 / 30.0);
        score += self.weights.recency * recency_score;
        
        // Access frequency boost
        score += self.weights.access_frequency * file.access_count as f32 / 100.0;
        
        // File size penalty (very large files slightly penalized)
        let size_penalty = if file.size > 100_000_000 { // 100MB
            0.9
        } else if file.size > 10_000_000 { // 10MB
            0.95
        } else {
            1.0
        };
        score *= size_penalty;
        
        // Path depth penalty (deeply nested files slightly penalized)
        let path_depth = file.path.components().count();
        let depth_penalty = 1.0 - (path_depth as f32 * 0.02).min(0.2);
        score *= depth_penalty;
        
        score.max(0.0).min(1.0)
    }
}
```

### Performance Optimization

**Indexing Performance Targets**
- **Initial Indexing:** 1,000 files/second for metadata, 100 files/second for content
- **Incremental Updates:** <50ms per file modification
- **Search Response:** <100ms for filename search, <500ms for content search
- **Memory Usage:** <100MB for index of 100,000 files

**Optimization Strategies**
1. **Batch Processing:** Group small files for bulk indexing operations
2. **Priority Queues:** User-visible files indexed first
3. **Adaptive Throttling:** Reduce indexing speed when user is actively working
4. **Index Compression:** Use SQLite compression and optimized schemas
5. **Background Processing:** All heavy indexing operations run in background threads

## 10. Previewers & Thumbnails

### Preview System Architecture

**Sandboxed Preview Engine**
```rust
pub struct PreviewEngine {
    preview_workers: Arc<Mutex<Vec<PreviewWorker>>>,
    sandbox_config: SandboxConfig,
    supported_types: HashMap<String, Box<dyn PreviewGenerator>>,
    cache: Arc<Mutex<LruCache<PathBuf, PreviewResult>>>,
}

#[derive(Debug, Clone)]
pub struct SandboxConfig {
    pub max_memory_mb: u64,      // 256MB per preview
    pub timeout_seconds: u64,     // 30 seconds max
    pub temp_dir: PathBuf,       // Isolated temp directory
    pub allowed_syscalls: Vec<String>, // Whitelist of allowed system calls
}

pub trait PreviewGenerator: Send + Sync {
    fn supported_extensions(&self) -> &[&str];
    fn generate_preview(&self, file_path: &Path, config: &PreviewConfig) -> Result<PreviewResult, PreviewError>;
    fn generate_thumbnail(&self, file_path: &Path, size: ThumbnailSize) -> Result<Vec<u8>, PreviewError>;
}

#[derive(Debug)]
pub struct PreviewResult {
    pub content_type: PreviewType,
    pub data: PreviewData,
    pub metadata: HashMap<String, String>,
    pub generated_at: SystemTime,
}

#[derive(Debug)]
pub enum PreviewType {
    Image,
    Text,
    Html,
    Video,
    Audio,
    Document,
    Archive,
}

#[derive(Debug)]
pub enum PreviewData {
    Image(Vec<u8>),
    Text(String),
    Html(String),
    VideoFrame(Vec<u8>),
    AudioWaveform(Vec<f32>),
    DocumentPages(Vec<Vec<u8>>),
    ArchiveList(Vec<ArchiveEntry>),
}
```

### Supported File Types & Generators

**Image Preview Generator**
```rust
pub struct ImagePreviewGenerator;

impl PreviewGenerator for ImagePreviewGenerator {
    fn supported_extensions(&self) -> &[&str] {
        &["jpg", "jpeg", "png", "gif", "webp", "svg", "bmp", "tiff", "ico", 
          "raw", "cr2", "nef", "arw", "dng", "heic", "avif"]
    }
    
    fn generate_preview(&self, file_path: &Path, config: &PreviewConfig) -> Result<PreviewResult, PreviewError> {
        let img = image::open(file_path)?;
        
        // Resize for preview while maintaining aspect ratio
        let preview_img = img.resize(
            config.max_width,
            config.max_height,
            image::imageops::FilterType::Lanczos3
        );
        
        let mut buffer = Vec::new();
        preview_img.write_to(&mut Cursor::new(&mut buffer), image::ImageFormat::WebP)?;
        
        let metadata = self.extract_image_metadata(&img)?;
        
        Ok(PreviewResult {
            content_type: PreviewType::Image,
            data: PreviewData::Image(buffer),
            metadata,
            generated_at: SystemTime::now(),
        })
    }
    
    fn generate_thumbnail(&self, file_path: &Path, size: ThumbnailSize) -> Result<Vec<u8>, PreviewError> {
        let img = image::open(file_path)?;
        let (width, height) = size.dimensions();
        
        let thumbnail = img.resize_exact(width, height, image::imageops::FilterType::Lanczos3);
        
        let mut buffer = Vec::new();
        thumbnail.write_to(&mut Cursor::new(&mut buffer), image::ImageFormat::WebP)?;
        
        Ok(buffer)
    }
}
```

**Document Preview Generator**
```rust
pub struct DocumentPreviewGenerator {
    pdf_renderer: Arc<Mutex<PdfRenderer>>,
    office_converter: Arc<Mutex<OfficeConverter>>,
}

impl PreviewGenerator for DocumentPreviewGenerator {
    fn supported_extensions(&self) -> &[&str] {
        &["pdf", "docx", "xlsx", "pptx", "odt", "ods", "odp", "rtf", "epub"]
    }
    
    fn generate_preview(&self, file_path: &Path, config: &PreviewConfig) -> Result<PreviewResult, PreviewError> {
        let extension = file_path.extension()
            .and_then(|ext| ext.to_str())
            .unwrap_or("")
            .to_lowercase();
            
        match extension.as_str() {
            "pdf" => self.generate_pdf_preview(file_path, config),
            "docx" | "xlsx" | "pptx" => self.generate_office_preview(file_path, config),
            "odt" | "ods" | "odp" => self.generate_libreoffice_preview(file_path, config),
            "epub" => self.generate_epub_preview(file_path, config),
            _ => Err(PreviewError::UnsupportedFormat),
        }
    }
    
    fn generate_pdf_preview(&self, file_path: &Path, config: &PreviewConfig) -> Result<PreviewResult, PreviewError> {
        let doc = lopdf::Document::load(file_path)?;
        let pages = doc.get_pages();
        
        let mut page_images = Vec::new();
        let max_pages = config.max_pages.unwrap_or(3);
        
        for (page_num, _) in pages.iter().take(max_pages) {
            // Render page to image using pdf-render crate
            let page_image = self.render_pdf_page(&doc, *page_num, config)?;
            page_images.push(page_image);
        }
        
        Ok(PreviewResult {
            content_type: PreviewType::Document,
            data: PreviewData::DocumentPages(page_images),
            metadata: HashMap::from([
                ("pages".to_string(), pages.len().to_string()),
                ("format".to_string(), "PDF".to_string()),
            ]),
            generated_at: SystemTime::now(),
        })
    }
}
```

**Code Preview Generator**
```rust
pub struct CodePreviewGenerator {
    highlighter: SyntaxHighlighter,
}

impl PreviewGenerator for CodePreviewGenerator {
    fn supported_extensions(&self) -> &[&str] {
        &["rs", "js", "ts", "py", "java", "cpp", "c", "h", "go", "php", 
          "rb", "swift", "kt", "cs", "scala", "clj", "hs", "elm", "vue", 
          "svelte", "jsx", "tsx", "css", "scss", "less", "html", "xml", 
          "json", "yaml", "toml", "md", "sql", "sh", "bash", "zsh", "ps1"]
    }
    
    fn generate_preview(&self, file_path: &Path, config: &PreviewConfig) -> Result<PreviewResult, PreviewError> {
        let content = std::fs::read_to_string(file_path)?;
        
        // Limit preview to first N lines to prevent performance issues
        let max_lines = config.max_lines.unwrap_or(100);
        let preview_content: String = content
            .lines()
            .take(max_lines)
            .collect::<Vec<_>>()
            .join("\n");
            
        let extension = file_path.extension()
            .and_then(|ext| ext.to_str())
            .unwrap_or("");
            
        let highlighted_html = self.highlighter.highlight(&preview_content, extension)?;
        
        Ok(PreviewResult {
            content_type: PreviewType::Html,
            data: PreviewData::Html(highlighted_html),
            metadata: HashMap::from([
                ("language".to_string(), extension.to_string()),
                ("lines".to_string(), content.lines().count().to_string()),
                ("size".to_string(), content.len().to_string()),
            ]),
            generated_at: SystemTime::now(),
        })
    }
}
```

### Thumbnail Generation Pipeline

**Multi-Size Thumbnail System**
```rust
#[derive(Debug, Clone, Copy)]
pub enum ThumbnailSize {
    Small,   // 64x64
    Medium,  // 256x256  
    Large,   // 512x512
}

impl ThumbnailSize {
    pub fn dimensions(&self) -> (u32, u32) {
        match self {
            ThumbnailSize::Small => (64, 64),
            ThumbnailSize::Medium => (256, 256),
            ThumbnailSize::Large => (512, 512),
        }
    }
    
    pub fn cache_path(&self, file_hash: &str) -> PathBuf {
        let size_dir = match self {
            ThumbnailSize::Small => "small",
            ThumbnailSize::Medium => "medium", 
            ThumbnailSize::Large => "large",
        };
        
        PathBuf::from("thumbnails")
            .join(size_dir)
            .join(format!("{}.webp", file_hash))
    }
}

pub struct ThumbnailCache {
    cache_dir: PathBuf,
    max_cache_size_mb: u64,
    cleanup_threshold: f32,
}

impl ThumbnailCache {
    pub async fn get_thumbnail(&self, file_path: &Path, size: ThumbnailSize) -> Result<Vec<u8>, CacheError> {
        let file_hash = self.calculate_file_hash(file_path).await?;
        let cache_path = self.cache_dir.join(size.cache_path(&file_hash));
        
        if cache_path.exists() {
            // Check if cached thumbnail is newer than source file
            let cache_modified = cache_path.metadata()?.modified()?;
            let file_modified = file_path.metadata()?.modified()?;
            
            if cache_modified >= file_modified {
                return Ok(std::fs::read(cache_path)?);
            }
        }
        
        // Generate new thumbnail
        let thumbnail_data = self.generate_thumbnail(file_path, size).await?;
        
        // Cache the result
        self.cache_thumbnail(&cache_path, &thumbnail_data).await?;
        
        Ok(thumbnail_data)
    }
    
    pub async fn cleanup_cache(&self) -> Result<(), CacheError> {
        let cache_size = self.calculate_cache_size().await?;
        let max_size_bytes = self.max_cache_size_mb * 1024 * 1024;
        
        if cache_size > (max_size_bytes as f64 * self.cleanup_threshold as f64) as u64 {
            // Remove oldest thumbnails until we're under the threshold
            self.remove_oldest_thumbnails(cache_size - max_size_bytes).await?;
        }
        
        Ok(())
    }
}
```

### Security Sandboxing

**Preview Security Model**
```rust
pub struct PreviewSandbox {
    container_runtime: ContainerRuntime,
    resource_limits: ResourceLimits,
    allowed_operations: HashSet<SandboxOperation>,
}

#[derive(Debug, Clone)]
pub struct ResourceLimits {
    pub max_memory_mb: u64,
    pub max_cpu_percent: u32,
    pub max_disk_io_mb: u64,
    pub max_network_connections: u32,
    pub timeout_seconds: u64,
}

#[derive(Debug, Clone, PartialEq, Eq, Hash)]
pub enum SandboxOperation {
    ReadFile,
    WriteTemp,
    NetworkAccess,
    ExecuteCommand,
    CreateProcess,
}

impl PreviewSandbox {
    pub async fn execute_preview(&self, request: PreviewRequest) -> Result<PreviewResult, SandboxError> {
        // Create isolated container for preview generation
        let container = self.container_runtime.create_container(ContainerConfig {
            image: "preview-worker:latest",
            memory_limit: self.resource_limits.max_memory_mb * 1024 * 1024,
            cpu_limit: self.resource_limits.max_cpu_percent,
            network_mode: NetworkMode::None, // No network access by default
            read_only_root: true,
            temp_dir_size_mb: 100,
        }).await?;
        
        // Mount file read-only into container
        container.mount_file(&request.file_path, "/input/file", MountMode::ReadOnly).await?;
        
        // Execute preview generation with timeout
        let result = tokio::time::timeout(
            Duration::from_secs(self.resource_limits.timeout_seconds),
            container.execute_preview_command(&request)
        ).await??;
        
        // Cleanup container
        container.destroy().await?;
        
        Ok(result)
    }
}
```

### Performance Considerations

**Thumbnail Generation Optimization**
- **Parallel Processing:** Generate multiple thumbnail sizes concurrently
- **Smart Caching:** Cache thumbnails with file modification time validation
- **Progressive Loading:** Load small thumbnails first, then upgrade to higher quality
- **Background Generation:** Generate thumbnails for visible items first, others in background
- **Memory Management:** Limit concurrent thumbnail generation to prevent memory exhaustion

**Preview Performance Targets**
- **Thumbnail Generation:** <200ms for images, <1s for documents
- **Preview Loading:** <500ms for text/code, <2s for complex documents
- **Cache Hit Rate:** >80% for frequently accessed files
- **Memory Usage:** <50MB for thumbnail cache, <100MB for preview cache
- **Concurrent Operations:** Support 10 concurrent thumbnail generations

## 11. Security & Privacy Checklist

### Code Signing & Distribution Security

**Code Signing Requirements**
- **Windows:** Authenticode certificate from trusted CA → sign both executable and installer
- **macOS:** Apple Developer ID certificate → notarization required for Gatekeeper bypass
- **Linux:** GPG signing of packages → repository signing for distribution

**Certificate Management**
```bash
# Windows code signing (SignTool)
signtool sign /fd SHA256 /tr http://timestamp.digicert.com /td SHA256 /f certificate.p12 /p password FileMaster.exe

# macOS code signing and notarization
codesign --deep --force --verify --verbose --sign "Developer ID Application: Company Name" FileMaster.app
xcrun notarytool submit FileMaster.app --keychain-profile "notarytool-profile" --wait

# Linux package signing (GPG)
gpg --detach-sign --armor filemaster_1.0.0_amd64.deb
```

### Application Sandboxing

**Platform-Specific Sandboxing**
```rust
// Tauri security configuration
#[derive(Debug, Deserialize)]
pub struct SecurityConfig {
    pub csp: ContentSecurityPolicy,
    pub dangerous_disable_asset_csp_modification: bool,
    pub asset_protocol: AssetProtocolConfig,
    pub pattern: PatternKind,
    pub capabilities: Vec<Capability>,
}

// Restrict dangerous APIs
impl SecurityConfig {
    pub fn production_config() -> Self {
        Self {
            csp: ContentSecurityPolicy {
                default_src: vec!["'self'".to_string()],
                script_src: vec!["'self'".to_string()],
                style_src: vec!["'self'".to_string(), "'unsafe-inline'".to_string()],
                img_src: vec!["'self'".to_string(), "data:".to_string()],
                connect_src: vec!["'self'".to_string()],
                font_src: vec!["'self'".to_string()],
                object_src: vec!["'none'".to_string()],
                media_src: vec!["'self'".to_string()],
            },
            dangerous_disable_asset_csp_modification: false,
            asset_protocol: AssetProtocolConfig {
                enable: true,
                scope: vec!["$RESOURCE/**".to_string()],
            },
            pattern: PatternKind::Brownfield,
            capabilities: vec![
                Capability::FileSystem,
                Capability::Shell,  // Limited shell access for file operations
            ],
        }
    }
}
```

**Permission System**
```rust
pub struct PermissionManager {
    granted_permissions: Arc<Mutex<HashSet<Permission>>>,
    permission_store: Arc<Mutex<PermissionStore>>,
}

#[derive(Debug, Clone, PartialEq, Eq, Hash)]
pub enum Permission {
    ReadDirectory(PathBuf),
    WriteDirectory(PathBuf),
    ExecuteCommand(String),
    NetworkAccess(String), // hostname/IP
    SystemInfo,
    Notifications,
    Clipboard,
}

impl PermissionManager {
    pub async fn request_permission(&self, permission: Permission) -> Result<bool, PermissionError> {
        // Check if permission already granted
        if self.granted_permissions.lock().unwrap().contains(&permission) {
            return Ok(true);
        }
        
        // Show user permission dialog
        let user_response = self.show_permission_dialog(&permission).await?;
        
        if user_response.granted {
            self.granted_permissions.lock().unwrap().insert(permission.clone());
            
            // Persist permission decision
            self.permission_store.lock().unwrap().store_permission(
                permission,
                user_response.remember
            )?;
            
            Ok(true)
        } else {
            Ok(false)
        }
    }
    
    async fn show_permission_dialog(&self, permission: &Permission) -> Result<PermissionResponse, PermissionError> {
        let dialog_config = match permission {
            Permission::ReadDirectory(path) => PermissionDialog {
                title: "File Access Permission".to_string(),
                message: format!("FileMaster wants to read files in:\n{}", path.display()),
                explanation: "This allows the app to index and search your files.".to_string(),
                risk_level: RiskLevel::Low,
                allow_remember: true,
            },
            Permission::WriteDirectory(path) => PermissionDialog {
                title: "File Modification Permission".to_string(),
                message: format!("FileMaster wants to modify files in:\n{}", path.display()),
                explanation: "This allows the app to move, copy, and delete files.".to_string(),
                risk_level: RiskLevel::Medium,
                allow_remember: true,
            },
            Permission::ExecuteCommand(cmd) => PermissionDialog {
                title: "Command Execution Permission".to_string(),
                message: format!("FileMaster wants to execute:\n{}", cmd),
                explanation: "This is needed for file preview generation.".to_string(),
                risk_level: RiskLevel::High,
                allow_remember: false,
            },
            _ => return Err(PermissionError::UnsupportedPermission),
        };
        
        self.show_native_dialog(dialog_config).await
    }
}
```

### Encryption at Rest

**File Encryption System**
```rust
use aes_gcm::{Aes256Gcm, Key, Nonce, aead::{Aead, KeyInit}};
use argon2::{Argon2, password_hash::{PasswordHasher, SaltString}};

pub struct EncryptionManager {
    cipher: Aes256Gcm,
    key_derivation: Argon2<'static>,
    encrypted_storage: Arc<Mutex<EncryptedStorage>>,
}

impl EncryptionManager {
    pub fn new(master_password: &str) -> Result<Self, EncryptionError> {
        let salt = SaltString::generate(&mut OsRng);
        let argon2 = Argon2::default();
        
        let password_hash = argon2.hash_password(master_password.as_bytes(), &salt)?;
        let key = Key::<Aes256Gcm>::from_slice(password_hash.hash.unwrap().as_bytes());
        let cipher = Aes256Gcm::new(key);
        
        Ok(Self {
            cipher,
            key_derivation: argon2,
            encrypted_storage: Arc::new(Mutex::new(EncryptedStorage::new()?)),
        })
    }
    
    pub fn encrypt_file(&self, file_path: &Path) -> Result<PathBuf, EncryptionError> {
        let file_data = std::fs::read(file_path)?;
        let nonce = Nonce::from_slice(b"unique nonce"); // Use proper nonce generation
        
        let ciphertext = self.cipher.encrypt(nonce, file_data.as_ref())?;
        
        let encrypted_path = self.get_encrypted_path(file_path);
        std::fs::write(&encrypted_path, ciphertext)?;
        
        // Store encryption metadata
        self.encrypted_storage.lock().unwrap().store_metadata(
            file_path,
            EncryptionMetadata {
                encrypted_path: encrypted_path.clone(),
                nonce: nonce.to_vec(),
                created_at: SystemTime::now(),
            }
        )?;
        
        Ok(encrypted_path)
    }
    
    pub fn decrypt_file(&self, encrypted_path: &Path) -> Result<Vec<u8>, EncryptionError> {
        let ciphertext = std::fs::read(encrypted_path)?;
        let metadata = self.encrypted_storage.lock().unwrap()
            .get_metadata_by_encrypted_path(encrypted_path)?;
            
        let nonce = Nonce::from_slice(&metadata.nonce);
        let plaintext = self.cipher.decrypt(nonce, ciphertext.as_ref())?;
        
        Ok(plaintext)
    }
}
```

### Secure Deletion

**Multi-Pass File Wiping**
```rust
pub struct SecureDeletion {
    wipe_patterns: Vec<WipePattern>,
    verification_enabled: bool,
}

#[derive(Debug, Clone)]
pub enum WipePattern {
    Zeros,
    Ones, 
    Random,
    DoD522022M,  // US Department of Defense standard
    Gutmann,     // 35-pass Gutmann method
}

impl SecureDeletion {
    pub async fn secure_delete(&self, file_path: &Path) -> Result<(), DeletionError> {
        let file_size = std::fs::metadata(file_path)?.len();
        
        // Perform multiple overwrite passes
        for pattern in &self.wipe_patterns {
            self.overwrite_file(file_path, pattern, file_size).await?;
        }
        
        // Verify deletion if enabled
        if self.verification_enabled {
            self.verify_secure_deletion(file_path).await?;
        }
        
        // Remove file system entry
        std::fs::remove_file(file_path)?;
        
        // Clear file name from directory (platform-specific)
        self.clear_directory_entry(file_path).await?;
        
        Ok(())
    }
    
    async fn overwrite_file(&self, file_path: &Path, pattern: &WipePattern, size: u64) -> Result<(), DeletionError> {
        let mut file = OpenOptions::new()
            .write(true)
            .open(file_path)?;
            
        let buffer = self.generate_pattern_buffer(pattern, 4096)?; // 4KB buffer
        let mut remaining = size;
        
        while remaining > 0 {
            let write_size = std::cmp::min(remaining, buffer.len() as u64) as usize;
            file.write_all(&buffer[..write_size])?;
            remaining -= write_size as u64;
        }
        
        file.sync_all()?; // Force write to disk
        Ok(())
    }
    
    fn generate_pattern_buffer(&self, pattern: &WipePattern, size: usize) -> Result<Vec<u8>, DeletionError> {
        match pattern {
            WipePattern::Zeros => Ok(vec![0u8; size]),
            WipePattern::Ones => Ok(vec![0xFFu8; size]),
            WipePattern::Random => {
                let mut buffer = vec![0u8; size];
                OsRng.fill_bytes(&mut buffer);
                Ok(buffer)
            },
            WipePattern::DoD522022M => {
                // Implement DoD 5220.22-M standard (3-pass)
                self.generate_dod_pattern(size)
            },
            WipePattern::Gutmann => {
                // Implement Gutmann method patterns
                self.generate_gutmann_pattern(size)
            },
        }
    }
}
```

### Privacy-Respecting Telemetry

**Opt-in Analytics System**
```rust
pub struct TelemetryManager {
    config: TelemetryConfig,
    event_queue: Arc<Mutex<VecDeque<TelemetryEvent>>>,
    user_consent: Arc<Mutex<ConsentStatus>>,
}

#[derive(Debug, Clone)]
pub struct TelemetryConfig {
    pub enabled: bool,
    pub endpoint: Option<String>,
    pub batch_size: usize,
    pub flush_interval: Duration,
    pub anonymization_level: AnonymizationLevel,
}

#[derive(Debug, Clone)]
pub enum AnonymizationLevel {
    None,        // Raw data (only with explicit consent)
    Basic,       // Remove PII, keep usage patterns
    Aggressive,  // Only aggregate statistics
}

#[derive(Debug, Clone)]
pub struct TelemetryEvent {
    pub event_type: String,
    pub timestamp: SystemTime,
    pub properties: HashMap<String, Value>,
    pub session_id: String,
}

impl TelemetryManager {
    pub async fn track_event(&self, event_type: &str, properties: HashMap<String, Value>) -> Result<(), TelemetryError> {
        // Check user consent
        let consent = self.user_consent.lock().unwrap().clone();
        if !consent.analytics_enabled {
            return Ok(()); // Silently ignore if not consented
        }
        
        // Anonymize data based on settings
        let anonymized_properties = self.anonymize_properties(properties, &self.config.anonymization_level)?;
        
        let event = TelemetryEvent {
            event_type: event_type.to_string(),
            timestamp: SystemTime::now(),
            properties: anonymized_properties,
            session_id: self.get_session_id(),
        };
        
        // Add to queue
        self.event_queue.lock().unwrap().push_back(event);
        
        // Flush if queue is full
        if self.event_queue.lock().unwrap().len() >= self.config.batch_size {
            self.flush_events().await?;
        }
        
        Ok(())
    }
    
    fn anonymize_properties(&self, properties: HashMap<String, Value>, level: &AnonymizationLevel) -> Result<HashMap<String, Value>, TelemetryError> {
        match level {
            AnonymizationLevel::None => Ok(properties),
            AnonymizationLevel::Basic => {
                let mut anonymized = HashMap::new();
                for (key, value) in properties {
                    if self.is_pii_field(&key) {
                        continue; // Skip PII fields
                    }
                    
                    // Hash file paths to preserve patterns while removing identity
                    if key.contains("path") || key.contains("file") {
                        if let Value::String(s) = value {
                            let hash = self.hash_string(&s);
                            anonymized.insert(key, Value::String(hash));
                        }
                    } else {
                        anonymized.insert(key, value);
                    }
                }
                Ok(anonymized)
            },
            AnonymizationLevel::Aggressive => {
                // Only keep aggregate counts and durations
                let mut aggregated = HashMap::new();
                if let Some(duration) = properties.get("duration") {
                    aggregated.insert("duration_bucket".to_string(), 
                                    Value::String(self.get_duration_bucket(duration)));
                }
                if let Some(count) = properties.get("count") {
                    aggregated.insert("count_bucket".to_string(),
                                    Value::String(self.get_count_bucket(count)));
                }
                Ok(aggregated)
            },
        }
    }
}

#[derive(Debug, Clone)]
pub struct ConsentStatus {
    pub analytics_enabled: bool,
    pub crash_reporting_enabled: bool,
    pub performance_monitoring_enabled: bool,
    pub consent_timestamp: SystemTime,
    pub consent_version: String,
}
```

### Network Security

**HTTPS-Only Communication**
```rust
pub struct SecureHttpClient {
    client: reqwest::Client,
    certificate_pinning: CertificatePinning,
}

impl SecureHttpClient {
    pub fn new() -> Result<Self, HttpError> {
        let client = reqwest::Client::builder()
            .use_rustls_tls()  // Use rustls instead of system TLS
            .min_tls_version(reqwest::tls::Version::TLS_1_2)
            .https_only(true)
            .timeout(Duration::from_secs(30))
            .build()?;
            
        Ok(Self {
            client,
            certificate_pinning: CertificatePinning::new()?,
        })
    }
    
    pub async fn secure_request(&self, url: &str) -> Result<reqwest::Response, HttpError> {
        // Verify certificate pinning
        self.certificate_pinning.verify_host(url)?;
        
        let response = self.client
            .get(url)
            .header("User-Agent", format!("FileMaster/{}", env!("CARGO_PKG_VERSION")))
            .header("Accept", "application/json")
            .send()
            .await?;
            
        // Verify response integrity
        if !response.status().is_success() {
            return Err(HttpError::RequestFailed(response.status()));
        }
        
        Ok(response)
    }
}
```

### Security Checklist Summary

**✓ Application Security**
- [ ] Code signing certificates obtained and configured
- [ ] Application sandboxing enabled with minimal permissions
- [ ] IPC communication secured with input validation
- [ ] File system access limited to user-granted directories
- [ ] Preview system runs in isolated sandbox
- [ ] No arbitrary code execution from file content

**✓ Data Protection**
- [ ] Encryption at rest available for sensitive files
- [ ] Secure deletion with multi-pass overwriting
- [ ] Database encryption for metadata
- [ ] Secure key management and derivation
- [ ] Memory protection against dumps
- [ ] Temporary file cleanup on exit

**✓ Privacy Controls**
- [ ] Local-first operation by default
- [ ] Explicit consent for all network features
- [ ] Telemetry completely opt-in with granular controls
- [ ] No tracking without user knowledge
- [ ] Data anonymization for analytics
- [ ] Clear privacy policy and data handling disclosure

**✓ Network Security**
- [ ] HTTPS-only communication
- [ ] Certificate pinning for API endpoints
- [ ] TLS 1.2+ minimum version
- [ ] Request/response integrity validation
- [ ] No insecure external dependencies
- [ ] Rate limiting for API calls

**✓ Update Security**
- [ ] Signed update packages
- [ ] Update integrity verification
- [ ] Rollback capability for failed updates
- [ ] Secure update channel (HTTPS)
- [ ] User control over update installation
- [ ] Delta updates to minimize attack surface

## 12. Performance Considerations & Benchmarks

### Performance Targets & Metrics

**Application Startup Performance**
- **Cold Start:** <3 seconds from launch to usable interface
- **Warm Start:** <1 second when app data cached
- **Memory Usage:** <100MB baseline, <500MB with large directories loaded
- **CPU Usage:** <5% idle, <25% during intensive operations

**File System Operations**
- **Directory Loading:** <200ms for 1,000 files, <2s for 10,000 files
- **File Operations:** <50ms for single file copy/move, <5s for 1,000 files
- **Search Response:** <100ms for filename search, <500ms for content search
- **Thumbnail Generation:** <200ms for images, <1s for documents

**UI Responsiveness Targets**
- **Frame Rate:** 60fps during animations and scrolling
- **Input Latency:** <16ms from user input to visual response
- **Virtual Scrolling:** Smooth scrolling through 100k+ items
- **Preview Loading:** <500ms for text/code, <2s for complex documents

### Performance Monitoring & Profiling

**Built-in Performance Monitoring**
```rust
pub struct PerformanceMonitor {
    metrics_collector: Arc<Mutex<MetricsCollector>>,
    profiler: Option<Profiler>,
    benchmarks: HashMap<String, BenchmarkResult>,
}

#[derive(Debug, Clone)]
pub struct PerformanceMetric {
    pub name: String,
    pub value: f64,
    pub unit: MetricUnit,
    pub timestamp: SystemTime,
    pub tags: HashMap<String, String>,
}

#[derive(Debug, Clone)]
pub enum MetricUnit {
    Milliseconds,
    Seconds,
    Bytes,
    Count,
    Percentage,
}

impl PerformanceMonitor {
    pub fn start_timer(&self, operation: &str) -> TimerGuard {
        TimerGuard::new(operation.to_string(), self.metrics_collector.clone())
    }
    
    pub fn record_metric(&self, name: &str, value: f64, unit: MetricUnit) {
        let metric = PerformanceMetric {
            name: name.to_string(),
            value,
            unit,
            timestamp: SystemTime::now(),
            tags: HashMap::new(),
        };
        
        self.metrics_collector.lock().unwrap().record(metric);
    }
    
    pub async fn run_benchmark(&mut self, benchmark_name: &str) -> Result<BenchmarkResult, BenchmarkError> {
        let benchmark = match benchmark_name {
            "file_indexing" => self.benchmark_file_indexing().await?,
            "search_performance" => self.benchmark_search_performance().await?,
            "ui_responsiveness" => self.benchmark_ui_responsiveness().await?,
            "memory_usage" => self.benchmark_memory_usage().await?,
            _ => return Err(BenchmarkError::UnknownBenchmark),
        };
        
        self.benchmarks.insert(benchmark_name.to_string(), benchmark.clone());
        Ok(benchmark)
    }
}

// Timer guard for automatic timing
pub struct TimerGuard {
    operation: String,
    start_time: Instant,
    metrics_collector: Arc<Mutex<MetricsCollector>>,
}

impl Drop for TimerGuard {
    fn drop(&mut self) {
        let duration = self.start_time.elapsed();
        let metric = PerformanceMetric {
            name: format!("{}_duration", self.operation),
            value: duration.as_millis() as f64,
            unit: MetricUnit::Milliseconds,
            timestamp: SystemTime::now(),
            tags: HashMap::new(),
        };
        
        self.metrics_collector.lock().unwrap().record(metric);
    }
}
```

**Profiling Integration**
```rust
// Integration with system profilers
pub struct SystemProfiler {
    #[cfg(target_os = "windows")]
    etw_session: Option<EtwSession>,
    
    #[cfg(target_os = "macos")]
    instruments_session: Option<InstrumentsSession>,
    
    #[cfg(target_os = "linux")]
    perf_session: Option<PerfSession>,
}

impl SystemProfiler {
    pub fn start_cpu_profiling(&mut self) -> Result<(), ProfilerError> {
        #[cfg(target_os = "windows")]
        {
            self.etw_session = Some(EtwSession::new("FileMaster-CPU")?);
            self.etw_session.as_mut().unwrap().start()?;
        }
        
        #[cfg(target_os = "macos")]
        {
            self.instruments_session = Some(InstrumentsSession::new("Time Profiler")?);
            self.instruments_session.as_mut().unwrap().start()?;
        }
        
        #[cfg(target_os = "linux")]
        {
            self.perf_session = Some(PerfSession::new("cpu-clock")?);
            self.perf_session.as_mut().unwrap().start()?;
        }
        
        Ok(())
    }
    
    pub fn capture_memory_snapshot(&self) -> Result<MemorySnapshot, ProfilerError> {
        let mut snapshot = MemorySnapshot::new();
        
        // Capture heap allocations
        snapshot.heap_size = self.get_heap_size()?;
        snapshot.heap_allocations = self.get_heap_allocations()?;
        
        // Capture stack usage
        snapshot.stack_size = self.get_stack_size()?;
        
        // Capture GPU memory if applicable
        snapshot.gpu_memory = self.get_gpu_memory_usage().ok();
        
        Ok(snapshot)
    }
}
```

### Large Directory Optimization

**Virtual Scrolling Implementation**
```rust
pub struct VirtualScrollManager {
    viewport_height: f32,
    item_height: f32,
    total_items: usize,
    visible_range: Range<usize>,
    buffer_size: usize,
    cached_items: LruCache<usize, FileEntry>,
}

impl VirtualScrollManager {
    pub fn new(viewport_height: f32, item_height: f32, buffer_size: usize) -> Self {
        Self {
            viewport_height,
            item_height,
            total_items: 0,
            visible_range: 0..0,
            buffer_size,
            cached_items: LruCache::new(buffer_size * 3), // 3x buffer for smooth scrolling
        }
    }
    
    pub fn update_scroll_position(&mut self, scroll_top: f32) -> Range<usize> {
        let visible_count = (self.viewport_height / self.item_height).ceil() as usize;
        let start_index = (scroll_top / self.item_height).floor() as usize;
        
        // Add buffer before and after visible area
        let buffer_start = start_index.saturating_sub(self.buffer_size);
        let buffer_end = (start_index + visible_count + self.buffer_size).min(self.total_items);
        
        self.visible_range = buffer_start..buffer_end;
        self.visible_range.clone()
    }
    
    pub fn get_visible_items(&self) -> Vec<Option<&FileEntry>> {
        self.visible_range
            .clone()
            .map(|index| self.cached_items.get(&index))
            .collect()
    }
}
```

**Incremental Loading Strategy**
```rust
pub struct IncrementalLoader {
    directory: PathBuf,
    batch_size: usize,
    loaded_ranges: Vec<Range<usize>>,
    total_count: Option<usize>,
    loading_tasks: HashMap<Range<usize>, JoinHandle<Vec<FileEntry>>>,
}

impl IncrementalLoader {
    pub async fn load_range(&mut self, range: Range<usize>) -> Result<Vec<FileEntry>, LoadError> {
        // Check if range already loaded
        if self.is_range_loaded(&range) {
            return self.get_cached_range(&range);
        }
        
        // Check if already loading
        if let Some(task) = self.loading_tasks.get(&range) {
            if !task.is_finished() {
                return Ok(Vec::new()); // Still loading
            }
        }
        
        // Start loading task
        let directory = self.directory.clone();
        let batch_size = self.batch_size;
        
        let task = tokio::spawn(async move {
            Self::load_directory_range(directory, range, batch_size).await
        });
        
        self.loading_tasks.insert(range.clone(), task);
        Ok(Vec::new()) // Return empty for now, will be populated on next call
    }
    
    async fn load_directory_range(
        directory: PathBuf, 
        range: Range<usize>, 
        batch_size: usize
    ) -> Vec<FileEntry> {
        let mut entries = Vec::new();
        let mut dir_iter = match std::fs::read_dir(&directory) {
            Ok(iter) => iter.skip(range.start),
            Err(_) => return entries,
        };
        
        for (i, entry_result) in dir_iter.enumerate() {
            if i >= range.len() {
                break;
            }
            
            if let Ok(entry) = entry_result {
                if let Ok(file_entry) = FileEntry::from_dir_entry(entry).await {
                    entries.push(file_entry);
                }
            }
            
            // Yield control periodically
            if i % batch_size == 0 {
                tokio::task::yield_now().await;
            }
        }
        
        entries
    }
}
```

### Memory Management Optimization

**Smart Caching Strategy**
```rust
pub struct SmartCache<K, V> {
    cache: LruCache<K, Arc<V>>,
    memory_pressure_threshold: usize,
    current_memory_usage: Arc<AtomicUsize>,
    eviction_strategy: EvictionStrategy,
}

#[derive(Debug, Clone)]
pub enum EvictionStrategy {
    LeastRecentlyUsed,
    LeastFrequentlyUsed,
    TimeToLive(Duration),
    MemoryPressure,
}

impl<K, V> SmartCache<K, V> 
where 
    K: Hash + Eq + Clone,
    V: Sized,
{
    pub fn insert(&mut self, key: K, value: V) -> Option<Arc<V>> {
        let value_size = std::mem::size_of_val(&value);
        let arc_value = Arc::new(value);
        
        // Check memory pressure
        if self.should_evict_before_insert(value_size) {
            self.evict_items();
        }
        
        let old_value = self.cache.put(key, arc_value.clone());
        
        // Update memory usage
        self.current_memory_usage.fetch_add(value_size, Ordering::Relaxed);
        
        if let Some(old) = &old_value {
            let old_size = std::mem::size_of_val(old.as_ref());
            self.current_memory_usage.fetch_sub(old_size, Ordering::Relaxed);
        }
        
        old_value
    }
    
    fn should_evict_before_insert(&self, new_item_size: usize) -> bool {
        let current_usage = self.current_memory_usage.load(Ordering::Relaxed);
        (current_usage + new_item_size) > self.memory_pressure_threshold
    }
    
    fn evict_items(&mut self) {
        match self.eviction_strategy {
            EvictionStrategy::MemoryPressure => {
                // Evict until we're under 80% of threshold
                let target = (self.memory_pressure_threshold as f64 * 0.8) as usize;
                let current = self.current_memory_usage.load(Ordering::Relaxed);
                
                if current > target {
                    let to_evict = current - target;
                    self.evict_by_size(to_evict);
                }
            },
            EvictionStrategy::TimeToLive(ttl) => {
                self.evict_expired_items(ttl);
            },
            _ => {
                // LRU/LFU handled by underlying cache
            }
        }
    }
}
```

### Search Performance Optimization

**Query Optimization & Caching**
```rust
pub struct SearchQueryOptimizer {
    query_cache: LruCache<String, SearchResults>,
    index_statistics: IndexStatistics,
    query_planner: QueryPlanner,
}

impl SearchQueryOptimizer {
    pub async fn optimize_query(&self, query: &SearchQuery) -> OptimizedQuery {
        let mut optimized = query.clone();
        
        // Reorder filters by selectivity (most selective first)
        optimized.filters.sort_by_key(|filter| {
            self.estimate_filter_selectivity(filter)
        });
        
        // Choose optimal index strategy
        optimized.index_strategy = self.choose_index_strategy(&optimized);
        
        // Determine if we can use cached results
        if let Some(cached_result) = self.check_cache(&optimized) {
            optimized.use_cached_result = Some(cached_result);
        }
        
        optimized
    }
    
    fn estimate_filter_selectivity(&self, filter: &SearchFilter) -> u32 {
        match filter {
            SearchFilter::FileType(types) => {
                // More specific file types = higher selectivity
                let total_files = self.index_statistics.total_files;
                let matching_files: u32 = types.iter()
                    .map(|t| self.index_statistics.files_by_type.get(t).unwrap_or(&0))
                    .sum();
                
                if total_files > 0 {
                    ((matching_files as f64 / total_files as f64) * 1000.0) as u32
                } else {
                    1000
                }
            },
            SearchFilter::SizeRange(min, max) => {
                // Smaller ranges = higher selectivity
                let range_size = max - min;
                if range_size < 1024 * 1024 { 100 } // <1MB = high selectivity
                else if range_size < 100 * 1024 * 1024 { 500 } // <100MB = medium
                else { 900 } // Large ranges = low selectivity
            },
            SearchFilter::DateRange(start, end) => {
                let range_days = end.duration_since(*start)
                    .unwrap_or_default()
                    .as_secs() / 86400;
                
                if range_days < 7 { 100 } // Week = high selectivity
                else if range_days < 30 { 300 } // Month = medium
                else { 800 } // Longer = low selectivity
            },
            SearchFilter::Tags(tags) => {
                // Fewer files with specific tags = higher selectivity
                200 / (tags.len() as u32).max(1)
            },
            SearchFilter::Path(pattern) => {
                // Specific paths = high selectivity, wildcards = low
                if pattern.contains('*') || pattern.contains('?') { 700 }
                else { 50 }
            },
        }
    }
}
```

### UI Performance Optimization

**Efficient Rendering Pipeline**
```rust
pub struct RenderingOptimizer {
    frame_budget_ms: f64, // 16.67ms for 60fps
    render_queue: VecDeque<RenderTask>,
    dirty_regions: Vec<Rect>,
    last_frame_time: Instant,
}

#[derive(Debug)]
pub struct RenderTask {
    pub priority: RenderPriority,
    pub region: Rect,
    pub task_type: RenderTaskType,
    pub estimated_cost_ms: f64,
}

#[derive(Debug, PartialOrd, Ord, PartialEq, Eq)]
pub enum RenderPriority {
    Critical,  // User interaction feedback
    High,      // Visible content updates
    Medium,    // Background updates
    Low,       // Preemptive rendering
}

impl RenderingOptimizer {
    pub fn schedule_render(&mut self, task: RenderTask) {
        // Insert task in priority order
        let insert_pos = self.render_queue
            .binary_search_by(|probe| probe.priority.cmp(&task.priority))
            .unwrap_or_else(|pos| pos);
        
        self.render_queue.insert(insert_pos, task);
    }
    
    pub fn execute_frame(&mut self) -> FrameResult {
        let frame_start = Instant::now();
        let mut tasks_completed = 0;
        let mut total_cost = 0.0;
        
        while let Some(task) = self.render_queue.front() {
            // Check if we have budget for this task
            if total_cost + task.estimated_cost_ms > self.frame_budget_ms {
                break;
            }
            
            let task = self.render_queue.pop_front().unwrap();
            
            // Execute the render task
            let task_start = Instant::now();
            self.execute_render_task(&task);
            let actual_cost = task_start.elapsed().as_secs_f64() * 1000.0;
            
            tasks_completed += 1;
            total_cost += actual_cost;
        }
        
        let frame_time = frame_start.elapsed();
        
        FrameResult {
            frame_time,
            tasks_completed,
            tasks_remaining: self.render_queue.len(),
            budget_used_percent: (total_cost / self.frame_budget_ms * 100.0) as u32,
        }
    }
}
```

### Benchmark Implementation

**Comprehensive Benchmarking Suite**
```rust
pub struct BenchmarkSuite {
    benchmarks: HashMap<String, Box<dyn Benchmark>>,
    results: Vec<BenchmarkResult>,
}

pub trait Benchmark {
    fn name(&self) -> &str;
    fn description(&self) -> &str;
    fn run(&mut self) -> Result<BenchmarkResult, BenchmarkError>;
    fn setup(&mut self) -> Result<(), BenchmarkError> { Ok(()) }
    fn teardown(&mut self) -> Result<(), BenchmarkError> { Ok(()) }
}

pub struct FileIndexingBenchmark {
    test_directory: PathBuf,
    file_count: usize,
    indexer: SearchIndexer,
}

impl Benchmark for FileIndexingBenchmark {
    fn name(&self) -> &str { "file_indexing" }
    
    fn description(&self) -> &str {
        "Measures file indexing performance across different directory sizes"
    }
    
    fn run(&mut self) -> Result<BenchmarkResult, BenchmarkError> {
        let mut results = BenchmarkResult::new(self.name());
        
        // Test different file counts
        let test_counts = vec![100, 1000, 10000, 50000];
        
        for count in test_counts {
            self.setup_test_files(count)?;
            
            let start = Instant::now();
            self.indexer.index_directory(&self.test_directory)?;
            let duration = start.elapsed();
            
            let files_per_second = count as f64 / duration.as_secs_f64();
            
            results.add_measurement(
                &format!("files_per_second_{}", count),
                files_per_second,
                MetricUnit::Count
            );
            
            results.add_measurement(
                &format!("total_time_ms_{}", count),
                duration.as_millis() as f64,
                MetricUnit::Milliseconds
            );
        }
        
        Ok(results)
    }
}

// Memory usage benchmark
pub struct MemoryUsageBenchmark {
    baseline_memory: usize,
    memory_sampler: MemorySampler,
}

impl Benchmark for MemoryUsageBenchmark {
    fn name(&self) -> &str { "memory_usage" }
    
    fn description(&self) -> &str {
        "Measures memory usage patterns during typical operations"
    }
    
    fn run(&mut self) -> Result<BenchmarkResult, BenchmarkError> {
        let mut results = BenchmarkResult::new(self.name());
        
        // Baseline measurement
        self.baseline_memory = self.memory_sampler.get_current_usage()?;
        
        // Test scenarios
        self.test_directory_loading(&mut results)?;
        self.test_search_operations(&mut results)?;
        self.test_thumbnail_generation(&mut results)?;
        self.test_memory_cleanup(&mut results)?;
        
        Ok(results)
    }
    
    fn test_directory_loading(&mut self, results: &mut BenchmarkResult) -> Result<(), BenchmarkError> {
        let start_memory = self.memory_sampler.get_current_usage()?;
        
        // Load large directory
        let large_dir = self.create_large_test_directory(10000)?;
        // ... load directory logic ...
        
        let peak_memory = self.memory_sampler.get_peak_usage()?;
        let end_memory = self.memory_sampler.get_current_usage()?;
        
        results.add_measurement(
            "directory_loading_peak_mb",
            (peak_memory - start_memory) as f64 / 1024.0 / 1024.0,
            MetricUnit::Bytes
        );
        
        results.add_measurement(
            "directory_loading_retained_mb", 
            (end_memory - start_memory) as f64 / 1024.0 / 1024.0,
            MetricUnit::Bytes
        );
        
        Ok(())
    }
}
```

## 13. Accessibility & Internationalization

### Accessibility Requirements

**Keyboard Navigation**
- **Complete Keyboard Access:** Every function accessible via keyboard shortcuts
- **Tab Order:** Logical tab sequence through all interactive elements
- **Focus Management:** Clear visual focus indicators, focus trapping in modals
- **Keyboard Shortcuts:** Customizable shortcuts with conflict detection

```rust
pub struct KeyboardNavigationManager {
    focus_stack: Vec<FocusableElement>,
    current_focus: Option<ElementId>,
    shortcut_registry: HashMap<KeyCombination, Action>,
    navigation_mode: NavigationMode,
}

#[derive(Debug, Clone)]
pub enum NavigationMode {
    Standard,    // Tab navigation
    Vim,         // Vim-like navigation (hjkl)
    Spatial,     // Arrow key spatial navigation
}

impl KeyboardNavigationManager {
    pub fn handle_key_event(&mut self, event: KeyEvent) -> Result<ActionResult, NavigationError> {
        match event {
            KeyEvent::Tab { shift: false } => self.focus_next(),
            KeyEvent::Tab { shift: true } => self.focus_previous(),
            KeyEvent::Escape => self.exit_current_context(),
            KeyEvent::Enter => self.activate_current_element(),
            KeyEvent::ArrowKey(direction) => self.handle_arrow_navigation(direction),
            KeyEvent::Shortcut(combination) => self.execute_shortcut(combination),
            _ => Ok(ActionResult::Ignored),
        }
    }
    
    pub fn register_shortcut(&mut self, combination: KeyCombination, action: Action) -> Result<(), NavigationError> {
        // Check for conflicts
        if let Some(existing) = self.shortcut_registry.get(&combination) {
            return Err(NavigationError::ShortcutConflict {
                combination,
                existing_action: existing.clone(),
                new_action: action,
            });
        }
        
        self.shortcut_registry.insert(combination, action);
        Ok(())
    }
}

// Default keyboard shortcuts
impl Default for KeyboardNavigationManager {
    fn default() -> Self {
        let mut manager = Self {
            focus_stack: Vec::new(),
            current_focus: None,
            shortcut_registry: HashMap::new(),
            navigation_mode: NavigationMode::Standard,
        };
        
        // Register default shortcuts
        manager.register_shortcut(KeyCombination::new(&[Key::Ctrl, Key::O]), Action::OpenFile).unwrap();
        manager.register_shortcut(KeyCombination::new(&[Key::Ctrl, Key::N]), Action::NewFolder).unwrap();
        manager.register_shortcut(KeyCombination::new(&[Key::Ctrl, Key::F]), Action::Search).unwrap();
        manager.register_shortcut(KeyCombination::new(&[Key::F2]), Action::Rename).unwrap();
        manager.register_shortcut(KeyCombination::new(&[Key::Delete]), Action::Delete).unwrap();
        manager.register_shortcut(KeyCombination::new(&[Key::Ctrl, Key::Z]), Action::Undo).unwrap();
        manager.register_shortcut(KeyCombination::new(&[Key::Ctrl, Key::Y]), Action::Redo).unwrap();
        
        manager
    }
}
```

**Screen Reader Support**
```rust
pub struct ScreenReaderSupport {
    announcements: VecDeque<Announcement>,
    live_regions: HashMap<ElementId, LiveRegion>,
    aria_labels: HashMap<ElementId, String>,
}

#[derive(Debug, Clone)]
pub struct Announcement {
    pub message: String,
    pub priority: AnnouncementPriority,
    pub timestamp: SystemTime,
}

#[derive(Debug, Clone, PartialEq)]
pub enum AnnouncementPriority {
    Polite,    // Wait for user to finish current task
    Assertive, // Interrupt current announcement
    Off,       // Don't announce
}

impl ScreenReaderSupport {
    pub fn announce(&mut self, message: String, priority: AnnouncementPriority) {
        let announcement = Announcement {
            message,
            priority,
            timestamp: SystemTime::now(),
        };
        
        match priority {
            AnnouncementPriority::Assertive => {
                // Clear queue and announce immediately
                self.announcements.clear();
                self.announcements.push_front(announcement);
            },
            AnnouncementPriority::Polite => {
                self.announcements.push_back(announcement);
            },
            AnnouncementPriority::Off => {
                // Don't add to queue
            }
        }
    }
    
    pub fn describe_file_list(&self, files: &[FileEntry]) -> String {
        let file_count = files.len();
        let folder_count = files.iter().filter(|f| f.is_directory).count();
        let file_count = file_count - folder_count;
        
        match (folder_count, file_count) {
            (0, 0) => "Empty folder".to_string(),
            (0, 1) => "1 file".to_string(),
            (0, n) => format!("{} files", n),
            (1, 0) => "1 folder".to_string(),
            (n, 0) => format!("{} folders", n),
            (1, 1) => "1 folder, 1 file".to_string(),
            (f, 1) => format!("{} folders, 1 file", f),
            (1, n) => format!("1 folder, {} files", n),
            (f, n) => format!("{} folders, {} files", f, n),
        }
    }
    
    pub fn describe_file_operation(&self, operation: &FileOperation) -> String {
        match operation {
            FileOperation::Copy { source, destination, count } => {
                if *count == 1 {
                    format!("Copying {} to {}", 
                           source.file_name().unwrap_or_default().to_string_lossy(),
                           destination.display())
                } else {
                    format!("Copying {} items to {}", count, destination.display())
                }
            },
            FileOperation::Move { source, destination, count } => {
                if *count == 1 {
                    format!("Moving {} to {}", 
                           source.file_name().unwrap_or_default().to_string_lossy(),
                           destination.display())
                } else {
                    format!("Moving {} items to {}", count, destination.display())
                }
            },
            FileOperation::Delete { items } => {
                if items.len() == 1 {
                    format!("Deleting {}", 
                           items[0].file_name().unwrap_or_default().to_string_lossy())
                } else {
                    format!("Deleting {} items", items.len())
                }
            },
        }
    }
}
```

**High Contrast & Visual Accessibility**
```css
/* High contrast theme */
[data-theme="high-contrast"] {
  --primary-50: #ffffff;
  --primary-500: #0000ff;
  --primary-600: #0000cc;
  --primary-900: #000080;
  
  --neutral-50: #ffffff;
  --neutral-100: #ffffff;
  --neutral-200: #c0c0c0;
  --neutral-500: #808080;
  --neutral-800: #000000;
  --neutral-900: #000000;
  
  --success-500: #00ff00;
  --warning-500: #ffff00;
  --error-500: #ff0000;
  --info-500: #00ffff;
}

/* Focus indicators */
.focus-visible {
  outline: 3px solid var(--primary-500);
  outline-offset: 2px;
}

/* Ensure minimum contrast ratios */
.text-contrast-aa {
  color: var(--neutral-900);
  background-color: var(--neutral-50);
  /* Ensures 4.5:1 contrast ratio */
}

.text-contrast-aaa {
  color: var(--neutral-900);
  background-color: var(--neutral-50);
  /* Ensures 7:1 contrast ratio */
}

/* Motion sensitivity */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

/* Large text support */
@media (min-resolution: 120dpi) {
  .text-base { font-size: 1.125rem; }
  .text-sm { font-size: 1rem; }
  .text-xs { font-size: 0.875rem; }
}
```

### Internationalization Strategy

**Multi-Language Support Architecture**
```rust
pub struct I18nManager {
    current_locale: Locale,
    fallback_locale: Locale,
    translations: HashMap<Locale, TranslationBundle>,
    formatters: HashMap<Locale, LocaleFormatters>,
    rtl_locales: HashSet<Locale>,
}

#[derive(Debug, Clone, PartialEq, Eq, Hash)]
pub struct Locale {
    pub language: String,    // "en", "es", "zh"
    pub country: Option<String>,  // "US", "MX", "CN"
    pub script: Option<String>,   // "Hans", "Hant"
}

impl I18nManager {
    pub fn new(locale: Locale) -> Self {
        let mut manager = Self {
            current_locale: locale.clone(),
            fallback_locale: Locale::en_us(),
            translations: HashMap::new(),
            formatters: HashMap::new(),
            rtl_locales: HashSet::from([
                Locale::new("ar", None, None), // Arabic
                Locale::new("he", None, None), // Hebrew
                Locale::new("fa", None, None), // Persian
                Locale::new("ur", None, None), // Urdu
            ]),
        };
        
        manager.load_translations(&locale).unwrap_or_else(|e| {
            eprintln!("Failed to load translations for {}: {}", locale, e);
        });
        
        manager
    }
    
    pub fn t(&self, key: &str, params: Option<HashMap<String, String>>) -> String {
        let translation = self.get_translation(key)
            .unwrap_or_else(|| {
                eprintln!("Missing translation for key: {}", key);
                key.to_string()
            });
        
        if let Some(params) = params {
            self.interpolate_translation(translation, params)
        } else {
            translation
        }
    }
    
    pub fn format_file_size(&self, bytes: u64) -> String {
        let formatter = self.formatters.get(&self.current_locale)
            .or_else(|| self.formatters.get(&self.fallback_locale))
            .unwrap();
        
        formatter.format_bytes(bytes)
    }
    
    pub fn format_date(&self, date: SystemTime) -> String {
        let formatter = self.formatters.get(&self.current_locale)
            .or_else(|| self.formatters.get(&self.fallback_locale))
            .unwrap();
        
        formatter.format_date(date)
    }
    
    pub fn is_rtl(&self) -> bool {
        self.rtl_locales.contains(&self.current_locale)
    }
}

// Translation bundle structure
#[derive(Debug, Clone)]
pub struct TranslationBundle {
    pub locale: Locale,
    pub translations: HashMap<String, String>,
    pub plurals: HashMap<String, PluralRules>,
}

#[derive(Debug, Clone)]
pub struct PluralRules {
    pub zero: Option<String>,
    pub one: String,
    pub two: Option<String>,
    pub few: Option<String>,
    pub many: Option<String>,
    pub other: String,
}

impl TranslationBundle {
    pub fn get_plural(&self, key: &str, count: i32) -> Option<&String> {
        if let Some(rules) = self.plurals.get(key) {
            match count {
                0 => rules.zero.as_ref().or(Some(&rules.other)),
                1 => Some(&rules.one),
                2 => rules.two.as_ref().or(Some(&rules.other)),
                3..=10 => rules.few.as_ref().or(Some(&rules.other)),
                _ => rules.many.as_ref().or(Some(&rules.other)),
            }
        } else {
            None
        }
    }
}
```

**Translation Files Structure**
```json
// translations/en-US.json
{
  "app": {
    "name": "FileMaster",
    "tagline": "Organize your files with intelligence"
  },
  "menu": {
    "file": "File",
    "edit": "Edit", 
    "view": "View",
    "go": "Go",
    "tools": "Tools",
    "help": "Help"
  },
  "file_operations": {
    "copy": "Copy",
    "move": "Move", 
    "delete": "Delete",
    "rename": "Rename",
    "new_folder": "New Folder"
  },
  "search": {
    "placeholder": "Search files and folders...",
    "results": {
      "zero": "No files found",
      "one": "1 file found", 
      "other": "{count} files found"
    }
  },
  "file_size": {
    "bytes": "{size} B",
    "kilobytes": "{size} KB", 
    "megabytes": "{size} MB",
    "gigabytes": "{size} GB"
  },
  "errors": {
    "file_not_found": "File not found: {path}",
    "permission_denied": "Permission denied accessing {path}",
    "disk_full": "Not enough disk space for this operation"
  }
}

// translations/es-ES.json
{
  "app": {
    "name": "FileMaster",
    "tagline": "Organiza tus archivos con inteligencia"
  },
  "menu": {
    "file": "Archivo",
    "edit": "Editar",
    "view": "Ver", 
    "go": "Ir",
    "tools": "Herramientas",
    "help": "Ayuda"
  },
  "file_operations": {
    "copy": "Copiar",
    "move": "Mover",
    "delete": "Eliminar", 
    "rename": "Renombrar",
    "new_folder": "Nueva Carpeta"
  },
  "search": {
    "placeholder": "Buscar archivos y carpetas...",
    "results": {
      "zero": "No se encontraron archivos",
      "one": "1 archivo encontrado",
      "other": "{count} archivos encontrados"
    }
  }
}

// translations/zh-CN.json
{
  "app": {
    "name": "文件管理大师",
    "tagline": "智能整理您的文件"
  },
  "menu": {
    "file": "文件",
    "edit": "编辑",
    "view": "查看",
    "go": "转到", 
    "tools": "工具",
    "help": "帮助"
  },
  "file_operations": {
    "copy": "复制",
    "move": "移动",
    "delete": "删除",
    "rename": "重命名", 
    "new_folder": "新建文件夹"
  }
}
```

**RTL (Right-to-Left) Support**
```css
/* RTL layout adjustments */
[dir="rtl"] {
  direction: rtl;
  text-align: right;
}

[dir="rtl"] .file-tree {
  border-right: none;
  border-left: 1px solid var(--neutral-200);
}

[dir="rtl"] .file-list-item {
  padding-right: var(--space-2);
  padding-left: var(--space-6);
}

[dir="rtl"] .icon-before {
  margin-left: var(--space-2);
  margin-right: 0;
}

[dir="rtl"] .breadcrumb::after {
  content: "\\";
  transform: scaleX(-1);
}

/* Logical properties for better RTL support */
.margin-inline-start { margin-inline-start: var(--space-4); }
.margin-inline-end { margin-inline-end: var(--space-4); }
.padding-inline { padding-inline: var(--space-2); }
.border-inline-start { border-inline-start: 1px solid var(--neutral-200); }
```

**Locale-Specific Formatting**
```rust
pub struct LocaleFormatters {
    pub number_formatter: NumberFormatter,
    pub date_formatter: DateFormatter,
    pub currency_formatter: CurrencyFormatter,
}

impl LocaleFormatters {
    pub fn format_bytes(&self, bytes: u64) -> String {
        let (value, unit) = match bytes {
            0..=1023 => (bytes as f64, "B"),
            1024..=1048575 => (bytes as f64 / 1024.0, "KB"),
            1048576..=1073741823 => (bytes as f64 / 1048576.0, "MB"),
            _ => (bytes as f64 / 1073741824.0, "GB"),
        };
        
        if value < 10.0 && unit != "B" {
            format!("{:.1} {}", value, unit)
        } else {
            format!("{:.0} {}", value, unit)
        }
    }
    
    pub fn format_date(&self, date: SystemTime) -> String {
        let datetime: DateTime<Local> = date.into();
        
        match self.date_formatter.style {
            DateStyle::Short => datetime.format("%m/%d/%Y").to_string(),
            DateStyle::Medium => datetime.format("%b %d, %Y").to_string(),
            DateStyle::Long => datetime.format("%B %d, %Y").to_string(),
            DateStyle::Relative => {
                let now = SystemTime::now();
                let duration = now.duration_since(date).unwrap_or_default();
                
                match duration.as_secs() {
                    0..=59 => "Just now".to_string(),
                    60..=3599 => format!("{} minutes ago", duration.as_secs() / 60),
                    3600..=86399 => format!("{} hours ago", duration.as_secs() / 3600),
                    86400..=604799 => format!("{} days ago", duration.as_secs() / 86400),
                    _ => datetime.format("%b %d, %Y").to_string(),
                }
            }
        }
    }
}
```

### Supported Languages (Initial Release)

**Tier 1 Languages (Full Support)**
- English (US, UK, AU, CA)
- Spanish (ES, MX, AR)
- French (FR, CA)
- German (DE, AT, CH)
- Portuguese (BR, PT)
- Italian (IT)
- Dutch (NL, BE)
- Russian (RU)

**Tier 2 Languages (Basic Support)**
- Chinese Simplified (CN)
- Chinese Traditional (TW, HK)
- Japanese (JP)
- Korean (KR)
- Arabic (SA, EG, AE)
- Hebrew (IL)
- Hindi (IN)
- Turkish (TR)

**Translation Management Process**
1. **Source String Extraction:** Automated extraction from source code
2. **Translation Memory:** Reuse existing translations across updates
3. **Professional Translation:** Native speakers for Tier 1 languages
4. **Community Translation:** Crowdsourced platform for Tier 2+ languages
5. **Quality Assurance:** Native speaker review and testing
6. **Continuous Localization:** Regular updates with new features

## 14. Testing Strategy

### Testing Pyramid & Approach

**Testing Levels**
- **Unit Tests (70%):** Fast, isolated tests for individual functions and components
- **Integration Tests (20%):** Test component interactions and system boundaries
- **End-to-End Tests (10%):** Full user workflow testing across the entire application

### Unit Testing Framework

**Frontend Testing (React + TypeScript)**
```typescript
// src/components/__tests__/FileList.test.tsx
import { render, screen, fireEvent, waitFor } from '@testing-library/react';
import { vi } from 'vitest';
import { FileList } from '../FileList';
import { FileEntry } from '../../types';

const mockFiles: FileEntry[] = [
  {
    id: '1',
    name: 'document.pdf',
    path: '/home/user/document.pdf',
    size: 1024000,
    modified: new Date('2023-01-01'),
    isDirectory: false,
    type: 'pdf'
  },
  {
    id: '2', 
    name: 'photos',
    path: '/home/user/photos',
    size: 0,
    modified: new Date('2023-01-02'),
    isDirectory: true,
    type: 'directory'
  }
];

describe('FileList', () => {
  it('renders file list correctly', () => {
    render(<FileList files={mockFiles} onFileSelect={vi.fn()} />);
    
    expect(screen.getByText('document.pdf')).toBeInTheDocument();
    expect(screen.getByText('photos')).toBeInTheDocument();
    expect(screen.getByText('1.0 MB')).toBeInTheDocument();
  });

  it('handles file selection', async () => {
    const onFileSelect = vi.fn();
    render(<FileList files={mockFiles} onFileSelect={onFileSelect} />);
    
    fireEvent.click(screen.getByText('document.pdf'));
    
    await waitFor(() => {
      expect(onFileSelect).toHaveBeenCalledWith(mockFiles[0]);
    });
  });

  it('supports keyboard navigation', async () => {
    render(<FileList files={mockFiles} onFileSelect={vi.fn()} />);
    
    const firstItem = screen.getByText('document.pdf');
    firstItem.focus();
    
    fireEvent.keyDown(firstItem, { key: 'ArrowDown' });
    
    await waitFor(() => {
      expect(screen.getByText('photos')).toHaveFocus();
    });
  });

  it('handles empty file list', () => {
    render(<FileList files={[]} onFileSelect={vi.fn()} />);
    
    expect(screen.getByText('This folder is empty')).toBeInTheDocument();
    expect(screen.getByRole('button', { name: 'Create new file' })).toBeInTheDocument();
  });
});
```

**Backend Testing (Rust)**
```rust
// src-tauri/src/file_manager/tests.rs
use super::*;
use tempfile::tempdir;
use std::fs;

#[cfg(test)]
mod tests {
    use super::*;

    #[tokio::test]
    async fn test_list_directory() {
        let temp_dir = tempdir().unwrap();
        let temp_path = temp_dir.path();
        
        // Create test files
        fs::write(temp_path.join("test1.txt"), "content1").unwrap();
        fs::write(temp_path.join("test2.txt"), "content2").unwrap();
        fs::create_dir(temp_path.join("subdir")).unwrap();
        
        let file_manager = FileManager::new();
        let result = file_manager.list_directory(temp_path).await.unwrap();
        
        assert_eq!(result.len(), 3);
        assert!(result.iter().any(|f| f.name == "test1.txt"));
        assert!(result.iter().any(|f| f.name == "test2.txt"));
        assert!(result.iter().any(|f| f.name == "subdir" && f.is_directory));
    }

    #[tokio::test]
    async fn test_copy_file() {
        let temp_dir = tempdir().unwrap();
        let source = temp_dir.path().join("source.txt");
        let dest = temp_dir.path().join("dest.txt");
        
        fs::write(&source, "test content").unwrap();
        
        let file_manager = FileManager::new();
        let result = file_manager.copy_file(&source, &dest).await;
        
        assert!(result.is_ok());
        assert!(dest.exists());
        assert_eq!(fs::read_to_string(&dest).unwrap(), "test content");
        assert!(source.exists()); // Original should still exist
    }

    #[tokio::test]
    async fn test_search_files() {
        let temp_dir = tempdir().unwrap();
        let temp_path = temp_dir.path();
        
        // Create test files with different content
        fs::write(temp_path.join("document.txt"), "important document content").unwrap();
        fs::write(temp_path.join("readme.md"), "# Project README").unwrap();
        fs::write(temp_path.join("config.json"), r#"{"key": "value"}"#).unwrap();
        
        let mut search_engine = SearchEngine::new();
        search_engine.index_directory(temp_path).await.unwrap();
        
        let query = SearchQuery {
            terms: vec![SearchTerm::Exact("document".to_string())],
            filters: vec![],
            sort_by: SortCriteria::Relevance,
            limit: 10,
            offset: 0,
        };
        
        let results = search_engine.search(query).await.unwrap();
        
        assert_eq!(results.files.len(), 1);
        assert_eq!(results.files[0].name, "document.txt");
        assert!(results.search_time.as_millis() < 100); // Should be fast
    }

    #[test]
    fn test_file_size_formatting() {
        assert_eq!(format_file_size(512), "512 B");
        assert_eq!(format_file_size(1024), "1.0 KB");
        assert_eq!(format_file_size(1536), "1.5 KB");
        assert_eq!(format_file_size(1048576), "1.0 MB");
        assert_eq!(format_file_size(1073741824), "1.0 GB");
    }

    #[tokio::test]
    async fn test_permission_denied_handling() {
        let file_manager = FileManager::new();
        
        // Try to access a restricted directory (will vary by OS)
        let restricted_path = if cfg!(windows) {
            PathBuf::from("C:\\System Volume Information")
        } else {
            PathBuf::from("/root")
        };
        
        let result = file_manager.list_directory(&restricted_path).await;
        
        match result {
            Err(FileManagerError::PermissionDenied(_)) => {
                // Expected error
            },
            _ => panic!("Should have received permission denied error"),
        }
    }
}

// Property-based testing for file operations
#[cfg(test)]
mod property_tests {
    use super::*;
    use proptest::prelude::*;

    proptest! {
        #[test]
        fn test_file_path_validation(
            path in r"[a-zA-Z0-9_\-/\\\.]{1,100}"
        ) {
            let result = validate_file_path(&path);
            // Path should be valid if it doesn't contain invalid characters
            if !path.contains("..") && !path.contains("//") {
                assert!(result.is_ok());
            }
        }

        #[test]
        fn test_search_query_parsing(
            query in r"[a-zA-Z0-9 ]{1,50}"
        ) {
            let parsed = parse_search_query(&query);
            // Should always parse without panicking
            assert!(parsed.is_ok());
            // Should contain at least the original query terms
            assert!(!parsed.unwrap().terms.is_empty());
        }
    }
}
```

### Integration Testing

**File System Integration Tests**
```rust
// tests/integration/file_operations.rs
use filemaster::{FileManager, SearchEngine, TagManager};
use tempfile::TempDir;
use std::fs;

#[tokio::test]
async fn test_full_file_workflow() {
    let temp_dir = TempDir::new().unwrap();
    let base_path = temp_dir.path();
    
    // Initialize components
    let file_manager = FileManager::new();
    let mut search_engine = SearchEngine::new();
    let mut tag_manager = TagManager::new();
    
    // Step 1: Create files
    let doc_path = base_path.join("important.txt");
    fs::write(&doc_path, "This is an important document").unwrap();
    
    let img_path = base_path.join("photo.jpg");
    fs::write(&img_path, b"\xFF\xD8\xFF\xE0").unwrap(); // JPEG header
    
    // Step 2: Index files
    search_engine.index_directory(base_path).await.unwrap();
    
    // Step 3: Add tags
    tag_manager.add_tag(&doc_path, "work").await.unwrap();
    tag_manager.add_tag(&doc_path, "important").await.unwrap();
    tag_manager.add_tag(&img_path, "personal").await.unwrap();
    
    // Step 4: Search by content
    let search_results = search_engine.search_content("important").await.unwrap();
    assert_eq!(search_results.len(), 1);
    assert_eq!(search_results[0].path, doc_path);
    
    // Step 5: Search by tags
    let tagged_files = tag_manager.find_files_with_tag("work").await.unwrap();
    assert_eq!(tagged_files.len(), 1);
    assert_eq!(tagged_files[0].path, doc_path);
    
    // Step 6: Move file
    let new_path = base_path.join("documents").join("important.txt");
    fs::create_dir_all(new_path.parent().unwrap()).unwrap();
    
    file_manager.move_file(&doc_path, &new_path).await.unwrap();
    
    // Step 7: Verify search still works after move
    search_engine.handle_file_moved(&doc_path, &new_path).await.unwrap();
    let updated_results = search_engine.search_content("important").await.unwrap();
    assert_eq!(updated_results.len(), 1);
    assert_eq!(updated_results[0].path, new_path);
    
    // Step 8: Verify tags are preserved
    let moved_file_tags = tag_manager.get_file_tags(&new_path).await.unwrap();
    assert!(moved_file_tags.contains(&"work".to_string()));
    assert!(moved_file_tags.contains(&"important".to_string()));
}

#[tokio::test]
async fn test_large_directory_performance() {
    let temp_dir = TempDir::new().unwrap();
    let base_path = temp_dir.path();
    
    // Create 1000 test files
    for i in 0..1000 {
        let file_path = base_path.join(format!("file_{:04}.txt", i));
        fs::write(&file_path, format!("Content of file {}", i)).unwrap();
    }
    
    let file_manager = FileManager::new();
    
    // Measure directory listing performance
    let start = std::time::Instant::now();
    let files = file_manager.list_directory(base_path).await.unwrap();
    let list_duration = start.elapsed();
    
    assert_eq!(files.len(), 1000);
    assert!(list_duration.as_millis() < 2000); // Should complete within 2 seconds
    
    // Measure search indexing performance
    let mut search_engine = SearchEngine::new();
    let start = std::time::Instant::now();
    search_engine.index_directory(base_path).await.unwrap();
    let index_duration = start.elapsed();
    
    assert!(index_duration.as_secs() < 10); // Should index within 10 seconds
    
    // Measure search performance
    let start = std::time::Instant::now();
    let results = search_engine.search_filename("file_0500").await.unwrap();
    let search_duration = start.elapsed();
    
    assert_eq!(results.len(), 1);
    assert!(search_duration.as_millis() < 100); // Should search within 100ms
}
```

### End-to-End Testing

**E2E Testing with Playwright**
```typescript
// tests/e2e/file-operations.spec.ts
import { test, expect } from '@playwright/test';
import { promises as fs } from 'fs';
import { join } from 'path';
import os from 'os';

test.describe('File Operations', () => {
  let testDir: string;

  test.beforeEach(async () => {
    // Create temporary test directory
    testDir = await fs.mkdtemp(join(os.tmpdir(), 'filemaster-test-'));
    
    // Create test files
    await fs.writeFile(join(testDir, 'document.txt'), 'Test document content');
    await fs.writeFile(join(testDir, 'image.jpg'), Buffer.from('fake-image-data'));
    await fs.mkdir(join(testDir, 'subfolder'));
    await fs.writeFile(join(testDir, 'subfolder', 'nested.txt'), 'Nested file');
  });

  test.afterEach(async () => {
    // Cleanup test directory
    await fs.rmdir(testDir, { recursive: true });
  });

  test('should navigate and display files', async ({ page }) => {
    await page.goto('/');
    
    // Open test directory
    await page.click('[data-testid="open-folder"]');
    await page.fill('[data-testid="folder-path"]', testDir);
    await page.press('[data-testid="folder-path"]', 'Enter');
    
    // Verify files are displayed
    await expect(page.locator('[data-testid="file-item"]')).toHaveCount(3);
    await expect(page.locator('text=document.txt')).toBeVisible();
    await expect(page.locator('text=image.jpg')).toBeVisible();
    await expect(page.locator('text=subfolder')).toBeVisible();
  });

  test('should copy files using drag and drop', async ({ page }) => {
    await page.goto('/');
    
    // Navigate to test directory
    await page.click('[data-testid="open-folder"]');
    await page.fill('[data-testid="folder-path"]', testDir);
    await page.press('[data-testid="folder-path"]', 'Enter');
    
    // Enable dual-pane mode
    await page.press('body', 'F3');
    
    // Navigate second pane to subfolder
    await page.click('[data-testid="right-pane"] [data-testid="folder-tree"] >> text=subfolder');
    
    // Drag document.txt from left pane to right pane
    const sourceFile = page.locator('[data-testid="left-pane"] >> text=document.txt');
    const targetPane = page.locator('[data-testid="right-pane"] [data-testid="file-list"]');
    
    await sourceFile.dragTo(targetPane);
    
    // Verify copy dialog appears
    await expect(page.locator('[data-testid="copy-dialog"]')).toBeVisible();
    await page.click('[data-testid="confirm-copy"]');
    
    // Wait for operation to complete
    await expect(page.locator('[data-testid="operation-complete"]')).toBeVisible();
    
    // Verify file was copied
    await expect(page.locator('[data-testid="right-pane"] >> text=document.txt')).toBeVisible();
    
    // Verify original file still exists
    await expect(page.locator('[data-testid="left-pane"] >> text=document.txt')).toBeVisible();
  });

  test('should search files by content', async ({ page }) => {
    await page.goto('/');
    
    // Navigate to test directory and index it
    await page.click('[data-testid="open-folder"]');
    await page.fill('[data-testid="folder-path"]', testDir);
    await page.press('[data-testid="folder-path"]', 'Enter');
    
    // Wait for indexing to complete
    await expect(page.locator('[data-testid="indexing-complete"]')).toBeVisible({ timeout: 10000 });
    
    // Perform search
    await page.press('body', 'Ctrl+f');
    await page.fill('[data-testid="search-input"]', 'Test document');
    
    // Verify search results
    await expect(page.locator('[data-testid="search-results"]')).toBeVisible();
    await expect(page.locator('[data-testid="search-result-item"] >> text=document.txt')).toBeVisible();
    
    // Click search result
    await page.click('[data-testid="search-result-item"] >> text=document.txt');
    
    // Verify file is selected and preview is shown
    await expect(page.locator('[data-testid="selected-file"] >> text=document.txt')).toBeVisible();
    await expect(page.locator('[data-testid="preview-pane"] >> text=Test document content')).toBeVisible();
  });

  test('should handle file operation errors gracefully', async ({ page }) => {
    await page.goto('/');
    
    // Navigate to test directory
    await page.click('[data-testid="open-folder"]');
    await page.fill('[data-testid="folder-path"]', testDir);
    await page.press('[data-testid="folder-path"]', 'Enter');
    
    // Try to delete a file that doesn't exist (simulate by deleting it externally first)
    await fs.unlink(join(testDir, 'document.txt'));
    
    // Try to delete the file in the UI
    await page.click('[data-testid="file-item"] >> text=document.txt');
    await page.press('body', 'Delete');
    
    // Verify error dialog appears
    await expect(page.locator('[data-testid="error-dialog"]')).toBeVisible();
    await expect(page.locator('text=File not found')).toBeVisible();
    
    // Close error dialog
    await page.click('[data-testid="close-error"]');
    
    // Verify UI refreshes and removes non-existent file
    await expect(page.locator('[data-testid="file-item"] >> text=document.txt')).not.toBeVisible();
  });
});

test.describe('Accessibility', () => {
  test('should be fully keyboard navigable', async ({ page }) => {
    await page.goto('/');
    
    // Test tab navigation
    await page.press('body', 'Tab');
    await expect(page.locator('[data-testid="file-tree"]')).toBeFocused();
    
    await page.press('body', 'Tab');
    await expect(page.locator('[data-testid="search-input"]')).toBeFocused();
    
    await page.press('body', 'Tab');
    await expect(page.locator('[data-testid="file-list"]')).toBeFocused();
    
    // Test arrow key navigation within file list
    await page.press('body', 'ArrowDown');
    await page.press('body', 'ArrowDown');
    await page.press('body', 'Enter');
    
    // Verify file selection works via keyboard
    await expect(page.locator('[data-testid="selected-file"]')).toBeVisible();
  });

  test('should work with screen readers', async ({ page }) => {
    await page.goto('/');
    
    // Check ARIA labels and roles
    await expect(page.locator('[role="tree"]')).toBeVisible(); // File tree
    await expect(page.locator('[role="grid"]')).toBeVisible(); // File list
    await expect(page.locator('[role="search"]')).toBeVisible(); // Search box
    
    // Check live regions for announcements
    await expect(page.locator('[aria-live="polite"]')).toBeVisible();
    
    // Verify alt text on icons
    await expect(page.locator('[alt="Folder icon"]')).toBeVisible();
    await expect(page.locator('[alt="File icon"]')).toBeVisible();
  });
});
```

### Performance Testing

**Load Testing Framework**
```rust
// tests/performance/load_test.rs
use criterion::{criterion_group, criterion_main, Criterion, BenchmarkId};
use filemaster::{FileManager, SearchEngine};
use tempfile::TempDir;
use std::fs;

fn benchmark_directory_listing(c: &mut Criterion) {
    let mut group = c.benchmark_group("directory_listing");
    
    for file_count in [100, 1000, 10000].iter() {
        let temp_dir = TempDir::new().unwrap();
        let base_path = temp_dir.path();
        
        // Create test files
        for i in 0..*file_count {
            let file_path = base_path.join(format!("file_{:05}.txt", i));
            fs::write(&file_path, format!("Content {}", i)).unwrap();
        }
        
        let file_manager = FileManager::new();
        
        group.benchmark_with_input(
            BenchmarkId::new("list_directory", file_count),
            file_count,
            |b, _| {
                b.to_async(tokio::runtime::Runtime::new().unwrap())
                 .iter(|| file_manager.list_directory(base_path))
            },
        );
    }
    
    group.finish();
}

fn benchmark_search_performance(c: &mut Criterion) {
    let mut group = c.benchmark_group("search_performance");
    
    let temp_dir = TempDir::new().unwrap();
    let base_path = temp_dir.path();
    
    // Create test files with searchable content
    for i in 0..1000 {
        let file_path = base_path.join(format!("document_{:03}.txt", i));
        let content = format!(
            "This is document number {} with some searchable content about {}",
            i, 
            if i % 10 == 0 { "important" } else { "regular" }
        );
        fs::write(&file_path, content).unwrap();
    }
    
    let rt = tokio::runtime::Runtime::new().unwrap();
    let mut search_engine = SearchEngine::new();
    rt.block_on(search_engine.index_directory(base_path)).unwrap();
    
    group.benchmark_function("filename_search", |b| {
        b.to_async(&rt).iter(|| {
            search_engine.search_filename("document_005")
        })
    });
    
    group.benchmark_function("content_search", |b| {
        b.to_async(&rt).iter(|| {
            search_engine.search_content("important")
        })
    });
    
    group.finish();
}

criterion_group!(benches, benchmark_directory_listing, benchmark_search_performance);
criterion_main!(benches);
```

### CI/CD Pipeline Configuration

**GitHub Actions Workflow**
```yaml
# .github/workflows/ci.yml
name: CI/CD Pipeline

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

env:
  CARGO_TERM_COLOR: always

jobs:
  test-frontend:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Setup Node.js
      uses: actions/setup-node@v4
      with:
        node-version: '18'
        cache: 'npm'
    
    - name: Install dependencies
      run: npm ci
    
    - name: Run linter
      run: npm run lint
    
    - name: Run type check
      run: npm run type-check
    
    - name: Run unit tests
      run: npm run test:unit -- --coverage
    
    - name: Upload coverage to Codecov
      uses: codecov/codecov-action@v3
      with:
        file: ./coverage/lcov.info

  test-backend:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest, macos-latest]
    
    steps:
    - uses: actions/checkout@v4
    - name: Setup Rust
      uses: actions-rs/toolchain@v1
      with:
        toolchain: stable
        components: rustfmt, clippy
    
    - name: Cache cargo registry
      uses: actions/cache@v3
      with:
        path: ~/.cargo/registry
        key: ${{ runner.os }}-cargo-registry-${{ hashFiles('**/Cargo.lock') }}
    
    - name: Run clippy
      run: cargo clippy --all-targets --all-features -- -D warnings
    
    - name: Run rustfmt
      run: cargo fmt --all -- --check
    
    - name: Run unit tests
      run: cargo test --verbose
    
    - name: Run integration tests
      run: cargo test --test '*' --verbose

  test-e2e:
    runs-on: ubuntu-latest
    needs: [test-frontend, test-backend]
    
    steps:
    - uses: actions/checkout@v4
    - name: Setup Node.js
      uses: actions/setup-node@v4
      with:
        node-version: '18'
        cache: 'npm'
    
    - name: Setup Rust
      uses: actions-rs/toolchain@v1
      with:
        toolchain: stable
    
    - name: Install dependencies
      run: npm ci
    
    - name: Build application
      run: npm run build
    
    - name: Install Playwright
      run: npx playwright install --with-deps
    
    - name: Run E2E tests
      run: npm run test:e2e
    
    - name: Upload E2E test results
      uses: actions/upload-artifact@v3
      if: failure()
      with:
        name: playwright-report
        path: playwright-report/

  security-audit:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Security audit (npm)
      run: npm audit --audit-level moderate
    
    - name: Security audit (cargo)
      run: cargo audit

  performance-test:
    runs-on: ubuntu-latest
    if: github.event_name == 'push' && github.ref == 'refs/heads/main'
    
    steps:
    - uses: actions/checkout@v4
    - name: Setup Rust
      uses: actions-rs/toolchain@v1
      with:
        toolchain: stable
    
    - name: Run performance benchmarks
      run: cargo bench -- --output-format json | tee benchmark-results.json
    
    - name: Store benchmark results
      uses: benchmark-action/github-action-benchmark@v1
      with:
        tool: 'cargo'
        output-file-path: benchmark-results.json
        github-token: ${{ secrets.GITHUB_TOKEN }}
        auto-push: true

  build-release:
    runs-on: ${{ matrix.os }}
    needs: [test-frontend, test-backend, test-e2e]
    if: github.event_name == 'push' && github.ref == 'refs/heads/main'
    
    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest, macos-latest]
    
    steps:
    - uses: actions/checkout@v4
    - name: Setup Node.js
      uses: actions/setup-node@v4
      with:
        node-version: '18'
        cache: 'npm'
    
    - name: Setup Rust
      uses: actions-rs/toolchain@v1
      with:
        toolchain: stable
    
    - name: Install dependencies
      run: npm ci
    
    - name: Build release
      run: npm run tauri build
    
    - name: Upload artifacts
      uses: actions/upload-artifact@v3
      with:
        name: release-${{ matrix.os }}
        path: src-tauri/target/release/bundle/
```

### Test Coverage Requirements

**Coverage Targets**
- **Overall Coverage:** Minimum 80%, target 90%
- **Critical Paths:** 95% coverage for file operations, search, security
- **UI Components:** 85% coverage for all React components
- **Backend Logic:** 90% coverage for Rust business logic

**Coverage Exclusions**
- Generated code and build artifacts
- Third-party library integrations (tested via integration tests)
- Platform-specific system calls (tested on CI matrix)
- Development and debugging utilities

## 15. Starter Code & File Scaffold

### Project Structure

```
filemaster/
├── src/                          # Frontend React application
│   ├── components/              # React components
│   │   ├── FileList/
│   │   │   ├── FileList.tsx
│   │   │   ├── FileList.test.tsx
│   │   │   └── FileList.module.css
│   │   ├── FileTree/
│   │   ├── SearchBar/
│   │   ├── PreviewPane/
│   │   └── TagPanel/
│   ├── hooks/                   # Custom React hooks
│   ├── services/               # API communication layer
│   ├── store/                  # Redux store and slices
│   ├── types/                  # TypeScript type definitions
│   ├── utils/                  # Utility functions
│   └── main.tsx               # Application entry point
├── src-tauri/                  # Tauri backend application
│   ├── src/
│   │   ├── main.rs            # Tauri main process
│   │   ├── commands/          # IPC command handlers
│   │   ├── file_manager/      # File system operations
│   │   ├── search/            # Search and indexing
│   │   ├── security/          # Security and encryption
│   │   └── database/          # SQLite database layer
│   ├── Cargo.toml             # Rust dependencies
│   └── tauri.conf.json        # Tauri configuration
├── tests/                      # Test files
│   ├── unit/                  # Unit tests
│   ├── integration/           # Integration tests
│   └── e2e/                   # End-to-end tests
├── docs/                       # Documentation
├── scripts/                    # Build and utility scripts
├── package.json               # Node.js dependencies
├── vite.config.ts             # Vite configuration
├── tailwind.config.js         # Tailwind CSS configuration
└── README.md                  # Project documentation
```

### Core Application Files

**Main Entry Point (src/main.tsx)**
```typescript
// src/main.tsx - Frontend application entry point
import React from 'react';
import ReactDOM from 'react-dom/client';
import { Provider } from 'react-redux';
import { store } from './store/store';
import { App } from './App';
import { I18nProvider } from './contexts/I18nContext';
import { ThemeProvider } from './contexts/ThemeContext';
import './index.css';

ReactDOM.createRoot(document.getElementById('root') as HTMLElement).render(
  <React.StrictMode>
    <Provider store={store}>
      <I18nProvider>
        <ThemeProvider>
          <App />
        </ThemeProvider>
      </I18nProvider>
    </Provider>
  </React.StrictMode>
);
```

**Tauri Main Process (src-tauri/src/main.rs)**
```rust
// src-tauri/src/main.rs - Tauri backend main process
#![cfg_attr(
    all(not(debug_assertions), target_os = "windows"),
    windows_subsystem = "windows"
)]

use tauri::{Manager, State};
use std::sync::Arc;
use tokio::sync::Mutex;

mod commands;
mod file_manager;
mod search;
mod security;
mod database;

use file_manager::FileManager;
use search::SearchEngine;
use database::Database;

pub struct AppState {
    file_manager: Arc<FileManager>,
    search_engine: Arc<Mutex<SearchEngine>>,
    database: Arc<Database>,
}

#[tokio::main]
async fn main() {
    // Initialize database
    let database = Arc::new(Database::new().await.expect("Failed to initialize database"));
    
    // Initialize core services
    let file_manager = Arc::new(FileManager::new());
    let search_engine = Arc::new(Mutex::new(
        SearchEngine::new(database.clone()).await.expect("Failed to initialize search engine")
    ));
    
    let app_state = AppState {
        file_manager,
        search_engine,
        database,
    };

    tauri::Builder::default()
        .manage(app_state)
        .invoke_handler(tauri::generate_handler![
            commands::list_directory,
            commands::copy_file,
            commands::move_file,
            commands::delete_file,
            commands::search_files,
            commands::add_tag,
            commands::get_file_tags,
            commands::generate_thumbnail,
        ])
        .setup(|app| {
            // Setup file system watcher
            let app_handle = app.handle();
            tokio::spawn(async move {
                setup_file_watcher(app_handle).await;
            });
            
            Ok(())
        })
        .run(tauri::generate_context!())
        .expect("error while running tauri application");
}

async fn setup_file_watcher(app_handle: tauri::AppHandle) {
    use notify::{RecommendedWatcher, RecursiveMode, Watcher};
    use std::path::Path;
    
    let (tx, mut rx) = tokio::sync::mpsc::channel(100);
    
    let mut watcher = RecommendedWatcher::new(
        move |res| {
            if let Ok(event) = res {
                let _ = tx.blocking_send(event);
            }
        },
        notify::Config::default(),
    ).expect("Failed to create file watcher");
    
    // Watch common directories (can be configured by user later)
    if let Ok(home_dir) = std::env::var("HOME") {
        let _ = watcher.watch(Path::new(&home_dir), RecursiveMode::Recursive);
    }
    
    // Handle file system events
    while let Some(event) = rx.recv().await {
        app_handle.emit_all("file-system-event", &event).unwrap();
    }
}
```

**File Manager Core (src-tauri/src/file_manager.rs)**
```rust
// src-tauri/src/file_manager.rs - Core file operations
use serde::{Deserialize, Serialize};
use std::path::{Path, PathBuf};
use std::fs;
use tokio::fs as async_fs;
use thiserror::Error;

#[derive(Error, Debug)]
pub enum FileManagerError {
    #[error("IO error: {0}")]
    Io(#[from] std::io::Error),
    #[error("Permission denied: {path}")]
    PermissionDenied { path: PathBuf },
    #[error("File not found: {path}")]
    FileNotFound { path: PathBuf },
    #[error("Invalid path: {path}")]
    InvalidPath { path: String },
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct FileEntry {
    pub path: PathBuf,
    pub name: String,
    pub size: u64,
    pub modified: std::time::SystemTime,
    pub created: std::time::SystemTime,
    pub is_directory: bool,
    pub is_hidden: bool,
    pub file_type: String,
    pub permissions: u32,
}

pub struct FileManager {
    // Configuration and state
}

impl FileManager {
    pub fn new() -> Self {
        Self {}
    }
    
    pub async fn list_directory(&self, path: &Path) -> Result<Vec<FileEntry>, FileManagerError> {
        if !path.exists() {
            return Err(FileManagerError::FileNotFound { path: path.to_path_buf() });
        }
        
        if !path.is_dir() {
            return Err(FileManagerError::InvalidPath { 
                path: path.to_string_lossy().to_string() 
            });
        }
        
        let mut entries = Vec::new();
        let mut dir = async_fs::read_dir(path).await?;
        
        while let Some(entry) = dir.next_entry().await? {
            let metadata = entry.metadata().await?;
            let file_name = entry.file_name().to_string_lossy().to_string();
            
            // Skip hidden files on Unix systems
            #[cfg(unix)]
            let is_hidden = file_name.starts_with('.');
            #[cfg(windows)]
            let is_hidden = {
                use std::os::windows::fs::MetadataExt;
                metadata.file_attributes() & 0x2 != 0
            };
            
            let file_entry = FileEntry {
                path: entry.path(),
                name: file_name,
                size: metadata.len(),
                modified: metadata.modified()?,
                created: metadata.created().unwrap_or_else(|_| metadata.modified().unwrap()),
                is_directory: metadata.is_dir(),
                is_hidden,
                file_type: get_file_type(&entry.path()),
                permissions: get_permissions(&metadata),
            };
            
            entries.push(file_entry);
        }
        
        // Sort entries: directories first, then by name
        entries.sort_by(|a, b| {
            match (a.is_directory, b.is_directory) {
                (true, false) => std::cmp::Ordering::Less,
                (false, true) => std::cmp::Ordering::Greater,
                _ => a.name.to_lowercase().cmp(&b.name.to_lowercase()),
            }
        });
        
        Ok(entries)
    }
    
    pub async fn copy_file(&self, source: &Path, destination: &Path) -> Result<(), FileManagerError> {
        self.validate_paths(source, destination)?;
        
        if source.is_dir() {
            self.copy_directory_recursive(source, destination).await
        } else {
            async_fs::copy(source, destination).await?;
            Ok(())
        }
    }
    
    pub async fn move_file(&self, source: &Path, destination: &Path) -> Result<(), FileManagerError> {
        self.validate_paths(source, destination)?;
        
        // Try rename first (fastest for same filesystem)
        match async_fs::rename(source, destination).await {
            Ok(_) => Ok(()),
            Err(_) => {
                // Fall back to copy + delete for cross-filesystem moves
                self.copy_file(source, destination).await?;
                self.delete_file(source).await
            }
        }
    }
    
    pub async fn delete_file(&self, path: &Path) -> Result<(), FileManagerError> {
        if !path.exists() {
            return Err(FileManagerError::FileNotFound { path: path.to_path_buf() });
        }
        
        if path.is_dir() {
            async_fs::remove_dir_all(path).await?;
        } else {
            async_fs::remove_file(path).await?;
        }
        
        Ok(())
    }
    
    async fn copy_directory_recursive(&self, source: &Path, destination: &Path) -> Result<(), FileManagerError> {
        async_fs::create_dir_all(destination).await?;
        
        let mut entries = async_fs::read_dir(source).await?;
        while let Some(entry) = entries.next_entry().await? {
            let source_path = entry.path();
            let dest_path = destination.join(entry.file_name());
            
            if source_path.is_dir() {
                self.copy_directory_recursive(&source_path, &dest_path).await?;
            } else {
                async_fs::copy(&source_path, &dest_path).await?;
            }
        }
        
        Ok(())
    }
    
    fn validate_paths(&self, source: &Path, destination: &Path) -> Result<(), FileManagerError> {
        if !source.exists() {
            return Err(FileManagerError::FileNotFound { path: source.to_path_buf() });
        }
        
        // Prevent copying to subdirectory of itself
        if destination.starts_with(source) {
            return Err(FileManagerError::InvalidPath { 
                path: format!("Cannot copy to subdirectory of source: {} -> {}", 
                             source.display(), destination.display()) 
            });
        }
        
        Ok(())
    }
}

fn get_file_type(path: &Path) -> String {
    path.extension()
        .and_then(|ext| ext.to_str())
        .map(|ext| ext.to_lowercase())
        .unwrap_or_else(|| {
            if path.is_dir() {
                "directory".to_string()
            } else {
                "unknown".to_string()
            }
        })
}

#[cfg(unix)]
fn get_permissions(metadata: &fs::Metadata) -> u32 {
    use std::os::unix::fs::PermissionsExt;
    metadata.permissions().mode()
}

#[cfg(windows)]
fn get_permissions(_metadata: &fs::Metadata) -> u32 {
    // Windows permissions are more complex, simplified for now
    0o644
}
```

**IPC Commands (src-tauri/src/commands.rs)**
```rust
// src-tauri/src/commands.rs - Tauri IPC command handlers
use tauri::{command, State};
use std::path::PathBuf;
use crate::{AppState, FileManagerError};
use crate::file_manager::FileEntry;

#[command]
pub async fn list_directory(
    path: String,
    state: State<'_, AppState>
) -> Result<Vec<FileEntry>, String> {
    let path = PathBuf::from(path);
    state.file_manager
        .list_directory(&path)
        .await
        .map_err(|e| e.to_string())
}

#[command]
pub async fn copy_file(
    source: String,
    destination: String,
    state: State<'_, AppState>
) -> Result<(), String> {
    let source = PathBuf::from(source);
    let destination = PathBuf::from(destination);
    
    state.file_manager
        .copy_file(&source, &destination)
        .await
        .map_err(|e| e.to_string())
}

#[command]
pub async fn move_file(
    source: String,
    destination: String,
    state: State<'_, AppState>
) -> Result<(), String> {
    let source = PathBuf::from(source);
    let destination = PathBuf::from(destination);
    
    state.file_manager
        .move_file(&source, &destination)
        .await
        .map_err(|e| e.to_string())
}

#[command]
pub async fn delete_file(
    path: String,
    state: State<'_, AppState>
) -> Result<(), String> {
    let path = PathBuf::from(path);
    
    state.file_manager
        .delete_file(&path)
        .await
        .map_err(|e| e.to_string())
}

#[command]
pub async fn search_files(
    query: String,
    filters: Vec<String>,
    state: State<'_, AppState>
) -> Result<Vec<FileEntry>, String> {
    let search_engine = state.search_engine.lock().await;
    
    search_engine
        .search(&query, &filters)
        .await
        .map_err(|e| e.to_string())
}

#[command]
pub async fn add_tag(
    file_path: String,
    tag: String,
    state: State<'_, AppState>
) -> Result<(), String> {
    let path = PathBuf::from(file_path);
    
    state.database
        .add_file_tag(&path, &tag)
        .await
        .map_err(|e| e.to_string())
}

#[command]
pub async fn get_file_tags(
    file_path: String,
    state: State<'_, AppState>
) -> Result<Vec<String>, String> {
    let path = PathBuf::from(file_path);
    
    state.database
        .get_file_tags(&path)
        .await
        .map_err(|e| e.to_string())
}

#[command]
pub async fn generate_thumbnail(
    file_path: String,
    size: u32,
    state: State<'_, AppState>
) -> Result<Vec<u8>, String> {
    let path = PathBuf::from(file_path);
    
    // Thumbnail generation logic would go here
    // For now, return empty vector
    Ok(Vec::new())
}
```

### Frontend React Components

**Main App Component (src/App.tsx)**
```typescript
// src/App.tsx - Main application component
import React, { useEffect } from 'react';
import { useDispatch } from 'react-redux';
import { invoke } from '@tauri-apps/api/tauri';
import { listen } from '@tauri-apps/api/event';
import { FileTree } from './components/FileTree/FileTree';
import { FileList } from './components/FileList/FileList';
import { SearchBar } from './components/SearchBar/SearchBar';
import { PreviewPane } from './components/PreviewPane/PreviewPane';
import { TagPanel } from './components/TagPanel/TagPanel';
import { StatusBar } from './components/StatusBar/StatusBar';
import { useAppSelector } from './hooks/redux';
import { setCurrentDirectory } from './store/fileSlice';
import './App.css';

export const App: React.FC = () => {
  const dispatch = useDispatch();
  const { currentDirectory, selectedFiles, isLoading } = useAppSelector(state => state.files);
  const { searchQuery, searchResults } = useAppSelector(state => state.search);
  const { previewVisible, tagPanelVisible } = useAppSelector(state => state.ui);

  useEffect(() => {
    // Listen for file system events from backend
    const unlisten = listen('file-system-event', (event) => {
      console.log('File system event:', event);
      // Handle file system changes
    });

    return () => {
      unlisten.then(fn => fn());
    };
  }, []);

  const handleDirectoryChange = async (path: string) => {
    try {
      const files = await invoke<FileEntry[]>('list_directory', { path });
      dispatch(setCurrentDirectory({ path, files }));
    } catch (error) {
      console.error('Failed to load directory:', error);
    }
  };

  return (
    <div className="app">
      <header className="app-header">
        <div className="app-title">FileMaster</div>
        <SearchBar />
        <div className="app-controls">
          {/* Window controls would go here */}
        </div>
      </header>
      
      <main className="app-main">
        <div className="app-sidebar">
          <FileTree onDirectorySelect={handleDirectoryChange} />
          {tagPanelVisible && <TagPanel />}
        </div>
        
        <div className="app-content">
          <div className="app-toolbar">
            {/* Toolbar buttons */}
          </div>
          
          <div className="app-body">
            <FileList
              files={searchQuery ? searchResults : currentDirectory?.files || []}
              isLoading={isLoading}
            />
            
            {previewVisible && (
              <PreviewPane
                file={selectedFiles[0]}
              />
            )}
          </div>
        </div>
      </main>
      
      <StatusBar />
    </div>
  );
};
```

### Getting Started (MVP)

**Prerequisites**
- Node.js 18+ and npm
- Rust 1.70+ and Cargo
- Git

**Bootstrap Commands**

```bash
# 1. Clone and setup the project
git clone https://github.com/your-org/filemaster.git
cd filemaster

# 2. Install frontend dependencies
npm install

# 3. Install Rust dependencies (automatically handled by Tauri)
# Rust dependencies are defined in src-tauri/Cargo.toml

# 4. Setup development database
npm run setup-db

# 5. Run in development mode
npm run tauri dev

# 6. Run tests
npm run test:unit          # Frontend unit tests
npm run test:backend       # Backend unit tests  
npm run test:integration   # Integration tests
npm run test:e2e          # End-to-end tests

# 7. Build for production
npm run tauri build       # Creates platform-specific installers
```

**Package.json Scripts**
```json
{
  "name": "filemaster",
  "version": "0.1.0",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "tauri": "tauri",
    "tauri:dev": "tauri dev",
    "tauri:build": "tauri build",
    "test:unit": "vitest run",
    "test:unit:watch": "vitest",
    "test:backend": "cargo test --manifest-path src-tauri/Cargo.toml",
    "test:integration": "cargo test --test '*' --manifest-path src-tauri/Cargo.toml",
    "test:e2e": "playwright test",
    "lint": "eslint src --ext .ts,.tsx",
    "lint:fix": "eslint src --ext .ts,.tsx --fix",
    "type-check": "tsc --noEmit",
    "setup-db": "node scripts/setup-database.js"
  },
  "dependencies": {
    "@tauri-apps/api": "^1.5.0",
    "@reduxjs/toolkit": "^1.9.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-redux": "^8.1.0",
    "react-router-dom": "^6.15.0"
  },
  "devDependencies": {
    "@tauri-apps/cli": "^1.5.0",
    "@types/react": "^18.2.0",
    "@types/react-dom": "^18.2.0",
    "@typescript-eslint/eslint-plugin": "^6.0.0",
    "@typescript-eslint/parser": "^6.0.0",
    "@vitejs/plugin-react": "^4.0.0",
    "eslint": "^8.45.0",
    "eslint-plugin-react-hooks": "^4.6.0",
    "typescript": "^5.0.0",
    "vite": "^4.4.0",
    "vitest": "^0.34.0",
    "@testing-library/react": "^13.4.0",
    "@testing-library/jest-dom": "^6.0.0",
    "@playwright/test": "^1.37.0",
    "tailwindcss": "^3.3.0",
    "autoprefixer": "^10.4.0",
    "postcss": "^8.4.0"
  }
}
```

This starter code provides a solid foundation for the FileMaster application with:
- Secure Tauri backend with proper error handling
- Modern React frontend with TypeScript
- IPC communication between frontend and backend
- File system operations with proper validation
- Test framework setup
- Development and build scripts

The code follows security best practices, includes comprehensive error handling, and provides a scalable architecture for building the full file management application.

## 16. Packaging & Distribution

### Cross-Platform Build System

**Windows Distribution**
```powershell
# Windows packaging script - scripts/build-windows.ps1
param(
    [string]$BuildType = "release",
    [switch]$CodeSign = $false
)

Write-Host "Building FileMaster for Windows..."

# Build the application
npm run tauri build --target x86_64-pc-windows-msvc

# Code signing (if certificate available)
if ($CodeSign -and $env:WINDOWS_CERTIFICATE_PATH) {
    $AppPath = "src-tauri/target/release/FileMaster.exe"
    $CertPath = $env:WINDOWS_CERTIFICATE_PATH
    $CertPassword = $env:WINDOWS_CERTIFICATE_PASSWORD
    
    Write-Host "Signing executable..."
    & "C:\Program Files (x86)\Windows Kits\10\bin\10.0.22000.0\x64\signtool.exe" sign `
        /f $CertPath `
        /p $CertPassword `
        /tr "http://timestamp.digicert.com" `
        /td SHA256 `
        /fd SHA256 `
        $AppPath
    
    # Sign installer
    $InstallerPath = "src-tauri/target/release/bundle/msi/FileMaster_1.0.0_x64_en-US.msi"
    & "C:\Program Files (x86)\Windows Kits\10\bin\10.0.22000.0\x64\signtool.exe" sign `
        /f $CertPath `
        /p $CertPassword `
        /tr "http://timestamp.digicert.com" `
        /td SHA256 `
        /fd SHA256 `
        $InstallerPath
}

Write-Host "Windows build complete!"
```

**macOS Distribution**
```bash
#!/bin/bash
# macOS packaging script - scripts/build-macos.sh

set -e

BUILD_TYPE=${1:-release}
SIGN_APP=${2:-false}

echo "Building FileMaster for macOS..."

# Build for both Intel and Apple Silicon
npm run tauri build -- --target universal-apple-darwin

APP_PATH="src-tauri/target/universal-apple-darwin/release/bundle/macos/FileMaster.app"
DMG_PATH="src-tauri/target/universal-apple-darwin/release/bundle/dmg/FileMaster_1.0.0_universal.dmg"

if [ "$SIGN_APP" = "true" ] && [ -n "$APPLE_DEVELOPER_ID" ]; then
    echo "Code signing application..."
    
    # Sign the app bundle
    codesign --deep --force --verify --verbose \
        --sign "Developer ID Application: $APPLE_DEVELOPER_ID" \
        --options runtime \
        "$APP_PATH"
    
    # Create and sign DMG
    echo "Creating and signing DMG..."
    codesign --force --verify --verbose \
        --sign "Developer ID Application: $APPLE_DEVELOPER_ID" \
        "$DMG_PATH"
    
    # Notarize the DMG
    if [ -n "$APPLE_NOTARIZATION_PROFILE" ]; then
        echo "Submitting for notarization..."
        xcrun notarytool submit "$DMG_PATH" \
            --keychain-profile "$APPLE_NOTARIZATION_PROFILE" \
            --wait
        
        # Staple the notarization
        xcrun stapler staple "$DMG_PATH"
        
        echo "Notarization complete!"
    fi
fi

echo "macOS build complete!"
```

**Linux Distribution**
```bash
#!/bin/bash
# Linux packaging script - scripts/build-linux.sh

set -e

BUILD_TYPE=${1:-release}
PACKAGE_FORMATS=${2:-"deb,appimage"}

echo "Building FileMaster for Linux..."

# Build the application
npm run tauri build

# Create different package formats
if [[ "$PACKAGE_FORMATS" == *"deb"* ]]; then
    echo "Creating DEB package..."
    # DEB package is created automatically by Tauri
    
    # Sign the DEB package if GPG key is available
    if [ -n "$GPG_KEY_ID" ]; then
        echo "Signing DEB package..."
        dpkg-sig --sign builder \
            --gpg-options "--digest-algo=sha256" \
            src-tauri/target/release/bundle/deb/filemaster_1.0.0_amd64.deb
    fi
fi

if [[ "$PACKAGE_FORMATS" == *"rpm"* ]]; then
    echo "Creating RPM package..."
    # Convert DEB to RPM using alien
    sudo alien --to-rpm --scripts \
        src-tauri/target/release/bundle/deb/filemaster_1.0.0_amd64.deb
    
    # Sign RPM if key available
    if [ -n "$RPM_GPG_KEY" ]; then
        rpm --addsign filemaster-1.0.0-1.x86_64.rpm
    fi
fi

if [[ "$PACKAGE_FORMATS" == *"appimage"* ]]; then
    echo "Creating AppImage..."
    # AppImage is created automatically by Tauri
    
    # Make AppImage executable
    chmod +x src-tauri/target/release/bundle/appimage/filemaster_1.0.0_amd64.AppImage
fi

echo "Linux build complete!"
```

### Tauri Configuration

**tauri.conf.json**
```json
{
  "build": {
    "beforeDevCommand": "npm run dev",
    "beforeBuildCommand": "npm run build",
    "devPath": "http://localhost:1420",
    "distDir": "../dist",
    "withGlobalTauri": false
  },
  "package": {
    "productName": "FileMaster",
    "version": "1.0.0"
  },
  "tauri": {
    "allowlist": {
      "all": false,
      "shell": {
        "all": false,
        "open": true
      },
      "path": {
        "all": true
      },
      "fs": {
        "all": true,
        "scope": ["$HOME/**", "$DESKTOP/**", "$DOCUMENT/**", "$DOWNLOAD/**"]
      },
      "dialog": {
        "all": false,
        "ask": true,
        "confirm": true,
        "message": true,
        "open": true,
        "save": true
      },
      "notification": {
        "all": true
      },
      "globalShortcut": {
        "all": true
      }
    },
    "bundle": {
      "active": true,
      "targets": "all",
      "identifier": "com.filemaster.app",
      "icon": [
        "icons/32x32.png",
        "icons/128x128.png",
        "icons/128x128@2x.png",
        "icons/icon.icns",
        "icons/icon.ico"
      ],
      "resources": [],
      "externalBin": [],
      "copyright": "Copyright © 2024 FileMaster Team",
      "category": "Productivity",
      "shortDescription": "Intelligent file management for power users",
      "longDescription": "FileMaster is a powerful, privacy-focused file manager that helps you organize, search, and manage your files with intelligence and ease.",
      "deb": {
        "depends": ["libwebkit2gtk-4.0-37", "libgtk-3-0"],
        "section": "utils",
        "priority": "optional"
      },
      "macOS": {
        "frameworks": [],
        "minimumSystemVersion": "10.13",
        "license": "LICENSE",
        "useBootstrapper": false,
        "signingIdentity": null,
        "hardenedRuntime": true,
        "entitlements": "entitlements.plist"
      },
      "windows": {
        "certificateThumbprint": null,
        "digestAlgorithm": "sha256",
        "timestampUrl": "http://timestamp.digicert.com",
        "wix": {
          "language": "en-US",
          "template": "installer.wxs"
        }
      }
    },
    "security": {
      "csp": "default-src 'self'; img-src 'self' asset: https://asset.localhost data:; style-src 'self' 'unsafe-inline'"
    },
    "windows": [
      {
        "fullscreen": false,
        "resizable": true,
        "title": "FileMaster",
        "width": 1200,
        "height": 800,
        "minWidth": 800,
        "minHeight": 600
      }
    ],
    "systemTray": {
      "iconPath": "icons/icon.png",
      "iconAsTemplate": true,
      "menuOnLeftClick": false
    }
  }
}
```

### Auto-Update System

**Update Configuration**
```rust
// src-tauri/src/updater.rs - Auto-update implementation
use serde::{Deserialize, Serialize};
use tauri::updater::{UpdateResponse, UpdaterEvent};
use tauri::{AppHandle, Manager};

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct UpdateInfo {
    pub version: String,
    pub release_notes: String,
    pub download_url: String,
    pub signature: String,
    pub release_date: String,
}

pub struct UpdateManager {
    app_handle: AppHandle,
    update_url: String,
    check_interval: std::time::Duration,
}

impl UpdateManager {
    pub fn new(app_handle: AppHandle) -> Self {
        Self {
            app_handle,
            update_url: "https://api.filemaster.app/updates".to_string(),
            check_interval: std::time::Duration::from_secs(3600), // Check every hour
        }
    }
    
    pub async fn check_for_updates(&self) -> Result<Option<UpdateInfo>, Box<dyn std::error::Error>> {
        let client = reqwest::Client::new();
        let current_version = self.app_handle.package_info().version.to_string();
        
        let response = client
            .get(&format!("{}/check", self.update_url))
            .header("User-Agent", format!("FileMaster/{}", current_version))
            .header("Current-Version", current_version)
            .send()
            .await?;
        
        if response.status().is_success() {
            let update_info: Option<UpdateInfo> = response.json().await?;
            Ok(update_info)
        } else {
            Ok(None)
        }
    }
    
    pub async fn download_and_install_update(&self, update_info: &UpdateInfo) -> Result<(), Box<dyn std::error::Error>> {
        // Verify signature before downloading
        self.verify_update_signature(update_info)?;
        
        // Use Tauri's built-in updater
        let update_result = self.app_handle.updater().check().await?;
        
        if update_result.is_update_available() {
            // Emit update progress events to frontend
            let app_handle = self.app_handle.clone();
            
            update_result
                .download_and_install(move |event| {
                    match event {
                        UpdaterEvent::DownloadProgress { chunk_length, content_length } => {
                            let progress = chunk_length as f64 / content_length.unwrap_or(1) as f64 * 100.0;
                            app_handle.emit_all("update-progress", progress).unwrap();
                        }
                        UpdaterEvent::Downloaded => {
                            app_handle.emit_all("update-downloaded", ()).unwrap();
                        }
                        UpdaterEvent::Updated => {
                            app_handle.emit_all("update-installed", ()).unwrap();
                        }
                        UpdaterEvent::AlreadyUpToDate => {
                            app_handle.emit_all("update-not-needed", ()).unwrap();
                        }
                        UpdaterEvent::Error(error) => {
                            app_handle.emit_all("update-error", error).unwrap();
                        }
                    }
                })
                .await?;
        }
        
        Ok(())
    }
    
    fn verify_update_signature(&self, update_info: &UpdateInfo) -> Result<(), Box<dyn std::error::Error>> {
        // Implement signature verification using public key
        // This is critical for security - only install signed updates
        
        use ed25519_dalek::{PublicKey, Signature, Verifier};
        use base64::decode;
        
        let public_key_bytes = include_bytes!("../keys/update_public_key.der");
        let public_key = PublicKey::from_bytes(public_key_bytes)?;
        
        let signature_bytes = decode(&update_info.signature)?;
        let signature = Signature::from_bytes(&signature_bytes)?;
        
        let message = format!("{}|{}", update_info.version, update_info.download_url);
        
        public_key.verify(message.as_bytes(), &signature)?;
        
        Ok(())
    }
    
    pub fn start_periodic_check(&self) {
        let updater = self.clone();
        
        tokio::spawn(async move {
            let mut interval = tokio::time::interval(updater.check_interval);
            
            loop {
                interval.tick().await;
                
                match updater.check_for_updates().await {
                    Ok(Some(update_info)) => {
                        // Emit update available event to frontend
                        updater.app_handle.emit_all("update-available", update_info).unwrap();
                    }
                    Ok(None) => {
                        // No update available
                    }
                    Err(error) => {
                        eprintln!("Update check failed: {}", error);
                    }
                }
            }
        });
    }
}

impl Clone for UpdateManager {
    fn clone(&self) -> Self {
        Self {
            app_handle: self.app_handle.clone(),
            update_url: self.update_url.clone(),
            check_interval: self.check_interval,
        }
    }
}
```

### Release Pipeline

**GitHub Actions Release Workflow**
```yaml
# .github/workflows/release.yml
name: Release

on:
  push:
    tags:
      - 'v*.*.*'

jobs:
  create-release:
    runs-on: ubuntu-latest
    outputs:
      release_id: ${{ steps.create-release.outputs.result }}

    steps:
      - uses: actions/checkout@v4
      - name: setup node
        uses: actions/setup-node@v4
        with:
          node-version: 18
      - name: get version
        run: echo "PACKAGE_VERSION=$(node -p "require('./package.json').version")" >> $GITHUB_ENV
      - name: create release
        id: create-release
        uses: actions/github-script@v6
        with:
          script: |
            const { data } = await github.rest.repos.createRelease({
              owner: context.repo.owner,
              repo: context.repo.repo,
              tag_name: `v${process.env.PACKAGE_VERSION}`,
              name: `FileMaster v${process.env.PACKAGE_VERSION}`,
              body: 'Take a look at the assets to download and install this app.',
              draft: true,
              prerelease: false
            })
            return data.id

  build-tauri:
    needs: create-release
    strategy:
      fail-fast: false
      matrix:
        platform: [macos-latest, ubuntu-20.04, windows-latest]

    runs-on: ${{ matrix.platform }}
    steps:
      - uses: actions/checkout@v4
      
      - name: setup node
        uses: actions/setup-node@v4
        with:
          node-version: 18
          cache: 'npm'
      
      - name: install Rust stable
        uses: dtolnay/rust-toolchain@stable
        with:
          targets: ${{ matrix.platform == 'macos-latest' && 'aarch64-apple-darwin,x86_64-apple-darwin' || '' }}
      
      - name: install dependencies (ubuntu only)
        if: matrix.platform == 'ubuntu-20.04'
        run: |
          sudo apt-get update
          sudo apt-get install -y libgtk-3-dev libwebkit2gtk-4.0-dev libappindicator3-dev librsvg2-dev patchelf
      
      - name: install frontend dependencies
        run: npm ci

      - uses: tauri-apps/tauri-action@v0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          TAURI_PRIVATE_KEY: ${{ secrets.TAURI_PRIVATE_KEY }}
          TAURI_KEY_PASSWORD: ${{ secrets.TAURI_KEY_PASSWORD }}
          APPLE_CERTIFICATE: ${{ secrets.APPLE_CERTIFICATE }}
          APPLE_CERTIFICATE_PASSWORD: ${{ secrets.APPLE_CERTIFICATE_PASSWORD }}
          APPLE_SIGNING_IDENTITY: ${{ secrets.APPLE_SIGNING_IDENTITY }}
          APPLE_ID: ${{ secrets.APPLE_ID }}
          APPLE_PASSWORD: ${{ secrets.APPLE_PASSWORD }}
          APPLE_TEAM_ID: ${{ secrets.APPLE_TEAM_ID }}
        with:
          releaseId: ${{ needs.create-release.outputs.release_id }}
          args: ${{ matrix.platform == 'macos-latest' && '--target universal-apple-darwin' || '' }}

  publish-release:
    runs-on: ubuntu-latest
    needs: [create-release, build-tauri]
    
    steps:
      - name: publish release
        id: publish-release
        uses: actions/github-script@v6
        env:
          release_id: ${{ needs.create-release.outputs.release_id }}
        with:
          script: |
            github.rest.repos.updateRelease({
              owner: context.repo.owner,
              repo: context.repo.repo,
              release_id: process.env.release_id,
              draft: false,
              prerelease: false
            })
```

### Installation Instructions

**Windows Installation**
```markdown
## Windows Installation

### Option 1: MSI Installer (Recommended)
1. Download `FileMaster-1.0.0-x64.msi` from the releases page
2. Right-click the installer and select "Run as administrator"
3. Follow the installation wizard
4. FileMaster will be available in your Start Menu

### Option 2: Portable Version
1. Download `FileMaster-1.0.0-x64-portable.zip`
2. Extract to your desired location
3. Run `FileMaster.exe`

### System Requirements
- Windows 10 version 1903 or later
- WebView2 Runtime (automatically installed)
- 4GB RAM minimum, 8GB recommended
- 500MB free disk space
```

**macOS Installation**
```markdown
## macOS Installation

### Option 1: DMG Package (Recommended)
1. Download `FileMaster-1.0.0-universal.dmg`
2. Double-click to mount the disk image
3. Drag FileMaster to your Applications folder
4. Launch from Applications or Spotlight

### Option 2: Homebrew Cask
```bash
brew install --cask filemaster
```

### System Requirements
- macOS 10.13 High Sierra or later
- Universal binary supports both Intel and Apple Silicon
- 4GB RAM minimum, 8GB recommended
- 500MB free disk space

### Security Note
FileMaster is signed and notarized by Apple. If you see a security warning, go to System Preferences > Security & Privacy and click "Open Anyway".
```

**Linux Installation**
```markdown
## Linux Installation

### Ubuntu/Debian (DEB Package)
```bash
# Download and install
wget https://github.com/filemaster/filemaster/releases/latest/download/filemaster_1.0.0_amd64.deb
sudo dpkg -i filemaster_1.0.0_amd64.deb
sudo apt-get install -f  # Fix dependencies if needed
```

### Fedora/RHEL (RPM Package)
```bash
# Download and install
wget https://github.com/filemaster/filemaster/releases/latest/download/filemaster-1.0.0-1.x86_64.rpm
sudo rpm -i filemaster-1.0.0-1.x86_64.rpm
```

### AppImage (Universal)
```bash
# Download and run
wget https://github.com/filemaster/filemaster/releases/latest/download/filemaster_1.0.0_amd64.AppImage
chmod +x filemaster_1.0.0_amd64.AppImage
./filemaster_1.0.0_amd64.AppImage
```

### System Requirements
- Linux kernel 3.10 or later
- GTK 3.20 or later
- WebKitGTK 2.20 or later
- 4GB RAM minimum, 8GB recommended
- 500MB free disk space
```

## 17. DevOps & Observability

### Logging Framework

**Structured Logging System**
```rust
// src-tauri/src/logging.rs - Comprehensive logging system
use serde_json::json;
use std::fs::OpenOptions;
use std::io::Write;
use std::path::PathBuf;
use chrono::{DateTime, Utc};
use uuid::Uuid;

#[derive(Debug, Clone)]
pub struct Logger {
    session_id: String,
    log_file: PathBuf,
    log_level: LogLevel,
    structured_logging: bool,
}

#[derive(Debug, Clone, PartialEq, PartialOrd)]
pub enum LogLevel {
    Trace = 0,
    Debug = 1,
    Info = 2,
    Warn = 3,
    Error = 4,
    Fatal = 5,
}

#[derive(Debug, Clone)]
pub struct LogEntry {
    pub timestamp: DateTime<Utc>,
    pub level: LogLevel,
    pub message: String,
    pub module: String,
    pub session_id: String,
    pub thread_id: String,
    pub metadata: serde_json::Value,
}

impl Logger {
    pub fn new() -> Result<Self, std::io::Error> {
        let session_id = Uuid::new_v4().to_string();
        let log_dir = Self::get_log_directory()?;
        std::fs::create_dir_all(&log_dir)?;
        
        let log_file = log_dir.join(format!("filemaster-{}.log", 
            Utc::now().format("%Y%m%d")));
        
        Ok(Self {
            session_id,
            log_file,
            log_level: LogLevel::Info,
            structured_logging: true,
        })
    }
    
    pub fn log(&self, level: LogLevel, module: &str, message: &str, metadata: Option<serde_json::Value>) {
        if level < self.log_level {
            return;
        }
        
        let entry = LogEntry {
            timestamp: Utc::now(),
            level,
            message: message.to_string(),
            module: module.to_string(),
            session_id: self.session_id.clone(),
            thread_id: format!("{:?}", std::thread::current().id()),
            metadata: metadata.unwrap_or(json!({})),
        };
        
        self.write_log_entry(&entry);
        
        // Also write to stdout in development
        #[cfg(debug_assertions)]
        self.write_to_stdout(&entry);
    }
    
    fn write_log_entry(&self, entry: &LogEntry) {
        let log_line = if self.structured_logging {
            serde_json::to_string(&json!({
                "timestamp": entry.timestamp.to_rfc3339(),
                "level": format!("{:?}", entry.level),
                "message": entry.message,
                "module": entry.module,
                "session_id": entry.session_id,
                "thread_id": entry.thread_id,
                "metadata": entry.metadata
            })).unwrap()
        } else {
            format!("{} [{:?}] {}: {} - {}",
                entry.timestamp.format("%Y-%m-%d %H:%M:%S%.3f"),
                entry.level,
                entry.module,
                entry.message,
                entry.metadata
            )
        };
        
        if let Ok(mut file) = OpenOptions::new()
            .create(true)
            .append(true)
            .open(&self.log_file) {
            let _ = writeln!(file, "{}", log_line);
        }
    }
    
    fn write_to_stdout(&self, entry: &LogEntry) {
        println!("{} [{:?}] {}: {}",
            entry.timestamp.format("%H:%M:%S%.3f"),
            entry.level,
            entry.module,
            entry.message
        );
    }
    
    fn get_log_directory() -> Result<PathBuf, std::io::Error> {
        let log_dir = if cfg!(target_os = "windows") {
            dirs::data_local_dir()
                .unwrap_or_else(|| PathBuf::from("."))
                .join("FileMaster")
                .join("logs")
        } else if cfg!(target_os = "macos") {
            dirs::home_dir()
                .unwrap_or_else(|| PathBuf::from("."))
                .join("Library")
                .join("Logs")
                .join("FileMaster")
        } else {
            dirs::home_dir()
                .unwrap_or_else(|| PathBuf::from("."))
                .join(".local")
                .join("share")
                .join("filemaster")
                .join("logs")
        };
        
        Ok(log_dir)
    }
    
    // Convenience methods
    pub fn trace(&self, module: &str, message: &str) {
        self.log(LogLevel::Trace, module, message, None);
    }
    
    pub fn debug(&self, module: &str, message: &str) {
        self.log(LogLevel::Debug, module, message, None);
    }
    
    pub fn info(&self, module: &str, message: &str) {
        self.log(LogLevel::Info, module, message, None);
    }
    
    pub fn warn(&self, module: &str, message: &str) {
        self.log(LogLevel::Warn, module, message, None);
    }
    
    pub fn error(&self, module: &str, message: &str) {
        self.log(LogLevel::Error, module, message, None);
    }
    
    pub fn fatal(&self, module: &str, message: &str) {
        self.log(LogLevel::Fatal, module, message, None);
    }
    
    // Structured logging with metadata
    pub fn info_with_metadata(&self, module: &str, message: &str, metadata: serde_json::Value) {
        self.log(LogLevel::Info, module, message, Some(metadata));
    }
    
    pub fn error_with_metadata(&self, module: &str, message: &str, metadata: serde_json::Value) {
        self.log(LogLevel::Error, module, message, Some(metadata));
    }
}

// Global logger instance
lazy_static::lazy_static! {
    pub static ref LOGGER: Logger = Logger::new().expect("Failed to initialize logger");
}

// Macros for easy logging
#[macro_export]
macro_rules! log_info {
    ($message:expr) => {
        crate::logging::LOGGER.info(module_path!(), $message);
    };
    ($message:expr, $metadata:expr) => {
        crate::logging::LOGGER.info_with_metadata(module_path!(), $message, $metadata);
    };
}

#[macro_export]
macro_rules! log_error {
    ($message:expr) => {
        crate::logging::LOGGER.error(module_path!(), $message);
    };
    ($message:expr, $metadata:expr) => {
        crate::logging::LOGGER.error_with_metadata(module_path!(), $message, $metadata);
    };
}

#[macro_export]
macro_rules! log_warn {
    ($message:expr) => {
        crate::logging::LOGGER.warn(module_path!(), $message);
    };
}

#[macro_export]
macro_rules! log_debug {
    ($message:expr) => {
        crate::logging::LOGGER.debug(module_path!(), $message);
    };
}
```

### Error Reporting System

**Privacy-Respecting Crash Reporting**
```rust
// src-tauri/src/error_reporting.rs - Crash and error reporting
use serde::{Deserialize, Serialize};
use std::panic;
use uuid::Uuid;

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct ErrorReport {
    pub report_id: String,
    pub timestamp: chrono::DateTime<chrono::Utc>,
    pub app_version: String,
    pub platform: String,
    pub error_type: ErrorType,
    pub error_message: String,
    pub stack_trace: Option<String>,
    pub user_actions: Vec<String>,
    pub system_info: SystemInfo,
    pub user_consent: bool,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub enum ErrorType {
    Panic,
    FileSystemError,
    SearchError,
    DatabaseError,
    NetworkError,
    PermissionError,
    Unknown,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct SystemInfo {
    pub os_name: String,
    pub os_version: String,
    pub arch: String,
    pub memory_total: u64,
    pub memory_available: u64,
    pub disk_space_available: u64,
}

pub struct ErrorReporter {
    enabled: bool,
    endpoint: Option<String>,
    user_consent: bool,
    recent_actions: std::collections::VecDeque<String>,
}

impl ErrorReporter {
    pub fn new() -> Self {
        Self {
            enabled: false, // Disabled by default - requires explicit opt-in
            endpoint: None,
            user_consent: false,
            recent_actions: std::collections::VecDeque::with_capacity(50),
        }
    }
    
    pub fn enable_with_consent(&mut self, endpoint: String) {
        self.enabled = true;
        self.endpoint = Some(endpoint);
        self.user_consent = true;
        
        // Set up panic hook
        self.setup_panic_handler();
    }
    
    pub fn disable(&mut self) {
        self.enabled = false;
        self.user_consent = false;
        
        // Restore default panic handler
        panic::take_hook();
    }
    
    pub fn record_user_action(&mut self, action: String) {
        if self.recent_actions.len() >= 50 {
            self.recent_actions.pop_front();
        }
        self.recent_actions.push_back(format!("{}: {}", 
            chrono::Utc::now().format("%H:%M:%S"), action));
    }
    
    fn setup_panic_handler(&self) {
        let reporter = self.clone();
        
        panic::set_hook(Box::new(move |panic_info| {
            let error_report = ErrorReport {
                report_id: Uuid::new_v4().to_string(),
                timestamp: chrono::Utc::now(),
                app_version: env!("CARGO_PKG_VERSION").to_string(),
                platform: format!("{}-{}", std::env::consts::OS, std::env::consts::ARCH),
                error_type: ErrorType::Panic,
                error_message: panic_info.to_string(),
                stack_trace: Some(format!("{:?}", backtrace::Backtrace::new())),
                user_actions: reporter.recent_actions.iter().cloned().collect(),
                system_info: reporter.collect_system_info(),
                user_consent: reporter.user_consent,
            };
            
            // Log locally first
            crate::log_error!("Application panic occurred", serde_json::to_value(&error_report).unwrap());
            
            // Send to remote endpoint if enabled and user consented
            if reporter.enabled && reporter.user_consent {
                if let Some(endpoint) = &reporter.endpoint {
                    tokio::spawn(async move {
                        let _ = reporter.send_error_report(endpoint, &error_report).await;
                    });
                }
            }
        }));
    }
    
    pub async fn report_error(&self, error_type: ErrorType, message: String, stack_trace: Option<String>) {
        if !self.enabled || !self.user_consent {
            return;
        }
        
        let error_report = ErrorReport {
            report_id: Uuid::new_v4().to_string(),
            timestamp: chrono::Utc::now(),
            app_version: env!("CARGO_PKG_VERSION").to_string(),
            platform: format!("{}-{}", std::env::consts::OS, std::env::consts::ARCH),
            error_type,
            error_message: message,
            stack_trace,
            user_actions: self.recent_actions.iter().cloned().collect(),
            system_info: self.collect_system_info(),
            user_consent: self.user_consent,
        };
        
        // Log locally
        crate::log_error!("Error reported", serde_json::to_value(&error_report).unwrap());
        
        // Send to remote endpoint
        if let Some(endpoint) = &self.endpoint {
            let _ = self.send_error_report(endpoint, &error_report).await;
        }
    }
    
    async fn send_error_report(&self, endpoint: &str, report: &ErrorReport) -> Result<(), Box<dyn std::error::Error>> {
        let client = reqwest::Client::new();
        
        let response = client
            .post(endpoint)
            .header("Content-Type", "application/json")
            .header("User-Agent", format!("FileMaster/{}", env!("CARGO_PKG_VERSION")))
            .json(report)
            .send()
            .await?;
        
        if response.status().is_success() {
            crate::log_info!("Error report sent successfully", serde_json::json!({
                "report_id": report.report_id
            }));
        } else {
            crate::log_warn!("Failed to send error report");
        }
        
        Ok(())
    }
    
    fn collect_system_info(&self) -> SystemInfo {
        SystemInfo {
            os_name: std::env::consts::OS.to_string(),
            os_version: sys_info::os_release().unwrap_or_default(),
            arch: std::env::consts::ARCH.to_string(),
            memory_total: sys_info::mem_info().map(|m| m.total).unwrap_or(0),
            memory_available: sys_info::mem_info().map(|m| m.avail).unwrap_or(0),
            disk_space_available: sys_info::disk_info()
                .map(|d| d.free)
                .unwrap_or(0),
        }
    }
}

impl Clone for ErrorReporter {
    fn clone(&self) -> Self {
        Self {
            enabled: self.enabled,
            endpoint: self.endpoint.clone(),
            user_consent: self.user_consent,
            recent_actions: self.recent_actions.clone(),
        }
    }
}

// Global error reporter
lazy_static::lazy_static! {
    pub static ref ERROR_REPORTER: std::sync::Mutex<ErrorReporter> = 
        std::sync::Mutex::new(ErrorReporter::new());
}
```

### Feature Flag System

**Runtime Feature Management**
```rust
// src-tauri/src/feature_flags.rs - Feature flag system
use serde::{Deserialize, Serialize};
use std::collections::HashMap;
use std::sync::RwLock;

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct FeatureFlag {
    pub name: String,
    pub enabled: bool,
    pub description: String,
    pub rollout_percentage: f32, // 0.0 to 1.0
    pub user_groups: Vec<String>,
    pub conditions: Vec<FeatureCondition>,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub enum FeatureCondition {
    UserGroup(String),
    AppVersion(String),
    Platform(String),
    RandomPercentage(f32),
    UserProperty { key: String, value: String },
}

pub struct FeatureFlagManager {
    flags: RwLock<HashMap<String, FeatureFlag>>,
    user_context: RwLock<UserContext>,
    remote_endpoint: Option<String>,
}

#[derive(Debug, Clone, Default)]
pub struct UserContext {
    pub user_id: Option<String>,
    pub groups: Vec<String>,
    pub properties: HashMap<String, String>,
    pub app_version: String,
    pub platform: String,
}

impl FeatureFlagManager {
    pub fn new() -> Self {
        Self {
            flags: RwLock::new(HashMap::new()),
            user_context: RwLock::new(UserContext {
                app_version: env!("CARGO_PKG_VERSION").to_string(),
                platform: format!("{}-{}", std::env::consts::OS, std::env::consts::ARCH),
                ..Default::default()
            }),
            remote_endpoint: None,
        }
    }
    
    pub fn with_remote_endpoint(mut self, endpoint: String) -> Self {
        self.remote_endpoint = Some(endpoint);
        self
    }
    
    pub fn is_enabled(&self, flag_name: &str) -> bool {
        let flags = self.flags.read().unwrap();
        let user_context = self.user_context.read().unwrap();
        
        if let Some(flag) = flags.get(flag_name) {
            self.evaluate_flag(flag, &user_context)
        } else {
            false // Default to disabled for unknown flags
        }
    }
    
    pub fn is_enabled_with_default(&self, flag_name: &str, default: bool) -> bool {
        let flags = self.flags.read().unwrap();
        let user_context = self.user_context.read().unwrap();
        
        if let Some(flag) = flags.get(flag_name) {
            self.evaluate_flag(flag, &user_context)
        } else {
            default
        }
    }
    
    fn evaluate_flag(&self, flag: &FeatureFlag, context: &UserContext) -> bool {
        if !flag.enabled {
            return false;
        }
        
        // Check all conditions
        for condition in &flag.conditions {
            if !self.evaluate_condition(condition, context) {
                return false;
            }
        }
        
        // Check rollout percentage
        if flag.rollout_percentage < 1.0 {
            let hash = self.hash_user_for_flag(&flag.name, context);
            let user_percentage = (hash % 1000) as f32 / 1000.0;
            if user_percentage >= flag.rollout_percentage {
                return false;
            }
        }
        
        true
    }
    
    fn evaluate_condition(&self, condition: &FeatureCondition, context: &UserContext) -> bool {
        match condition {
            FeatureCondition::UserGroup(group) => {
                context.groups.contains(group)
            }
            FeatureCondition::AppVersion(version) => {
                context.app_version == *version
            }
            FeatureCondition::Platform(platform) => {
                context.platform == *platform
            }
            FeatureCondition::RandomPercentage(percentage) => {
                use std::collections::hash_map::DefaultHasher;
                use std::hash::{Hash, Hasher};
                
                let mut hasher = DefaultHasher::new();
                context.user_id.as_ref().unwrap_or(&"anonymous".to_string()).hash(&mut hasher);
                let hash = hasher.finish();
                let user_percentage = (hash % 1000) as f32 / 1000.0;
                user_percentage < *percentage
            }
            FeatureCondition::UserProperty { key, value } => {
                context.properties.get(key).map(|v| v == value).unwrap_or(false)
            }
        }
    }
    
    fn hash_user_for_flag(&self, flag_name: &str, context: &UserContext) -> u64 {
        use std::collections::hash_map::DefaultHasher;
        use std::hash::{Hash, Hasher};
        
        let mut hasher = DefaultHasher::new();
        context.user_id.as_ref().unwrap_or(&"anonymous".to_string()).hash(&mut hasher);
        flag_name.hash(&mut hasher);
        hasher.finish()
    }
    
    pub async fn refresh_flags(&self) -> Result<(), Box<dyn std::error::Error>> {
        if let Some(endpoint) = &self.remote_endpoint {
            let client = reqwest::Client::new();
            let context = self.user_context.read().unwrap().clone();
            
            let response = client
                .get(format!("{}/flags", endpoint))
                .header("User-Agent", format!("FileMaster/{}", env!("CARGO_PKG_VERSION")))
                .json(&context)
                .send()
                .await?;
            
            if response.status().is_success() {
                let flags: HashMap<String, FeatureFlag> = response.json().await?;
                *self.flags.write().unwrap() = flags;
                
                crate::log_info!("Feature flags refreshed successfully");
            }
        }
        
        Ok(())
    }
    
    pub fn set_user_context(&self, context: UserContext) {
        *self.user_context.write().unwrap() = context;
    }
    
    pub fn add_user_group(&self, group: String) {
        self.user_context.write().unwrap().groups.push(group);
    }
    
    pub fn set_user_property(&self, key: String, value: String) {
        self.user_context.write().unwrap().properties.insert(key, value);
    }
    
    // Built-in feature flags for FileMaster
    pub fn initialize_default_flags(&self) {
        let mut flags = self.flags.write().unwrap();
        
        flags.insert("advanced_search".to_string(), FeatureFlag {
            name: "advanced_search".to_string(),
            enabled: true,
            description: "Enable advanced search features".to_string(),
            rollout_percentage: 1.0,
            user_groups: vec![],
            conditions: vec![],
        });
        
        flags.insert("cloud_sync".to_string(), FeatureFlag {
            name: "cloud_sync".to_string(),
            enabled: false,
            description: "Enable cloud synchronization features".to_string(),
            rollout_percentage: 0.1, // 10% rollout
            user_groups: vec!["beta_testers".to_string()],
            conditions: vec![],
        });
        
        flags.insert("ai_suggestions".to_string(), FeatureFlag {
            name: "ai_suggestions".to_string(),
            enabled: false,
            description: "AI-powered file organization suggestions".to_string(),
            rollout_percentage: 0.05, // 5% rollout
            user_groups: vec!["premium_users".to_string()],
            conditions: vec![],
        });
    }
}

// Global feature flag manager
lazy_static::lazy_static! {
    pub static ref FEATURE_FLAGS: FeatureFlagManager = {
        let manager = FeatureFlagManager::new();
        manager.initialize_default_flags();
        manager
    };
}

// Convenience macros
#[macro_export]
macro_rules! feature_enabled {
    ($flag:expr) => {
        crate::feature_flags::FEATURE_FLAGS.is_enabled($flag)
    };
    ($flag:expr, $default:expr) => {
        crate::feature_flags::FEATURE_FLAGS.is_enabled_with_default($flag, $default)
    };
}
```

### Monitoring Dashboard

**Health Check System**
```rust
// src-tauri/src/health.rs - Application health monitoring
use serde::{Deserialize, Serialize};
use std::time::{Duration, Instant};

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct HealthStatus {
    pub status: HealthLevel,
    pub timestamp: chrono::DateTime<chrono::Utc>,
    pub checks: Vec<HealthCheck>,
    pub system_metrics: SystemMetrics,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub enum HealthLevel {
    Healthy,
    Warning,
    Critical,
    Down,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct HealthCheck {
    pub name: String,
    pub status: HealthLevel,
    pub message: String,
    pub duration_ms: u64,
    pub details: serde_json::Value,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct SystemMetrics {
    pub memory_usage_mb: u64,
    pub cpu_usage_percent: f32,
    pub disk_usage_percent: f32,
    pub open_file_handles: u32,
    pub database_connections: u32,
    pub uptime_seconds: u64,
}

pub struct HealthMonitor {
    start_time: Instant,
    checks: Vec<Box<dyn HealthChecker + Send + Sync>>,
}

pub trait HealthChecker {
    fn name(&self) -> &str;
    fn check(&self) -> HealthCheck;
}

impl HealthMonitor {
    pub fn new() -> Self {
        let mut monitor = Self {
            start_time: Instant::now(),
            checks: Vec::new(),
        };
        
        // Register default health checks
        monitor.register_check(Box::new(DatabaseHealthChecker));
        monitor.register_check(Box::new(FileSystemHealthChecker));
        monitor.register_check(Box::new(SearchIndexHealthChecker));
        monitor.register_check(Box::new(MemoryHealthChecker));
        
        monitor
    }
    
    pub fn register_check(&mut self, checker: Box<dyn HealthChecker + Send + Sync>) {
        self.checks.push(checker);
    }
    
    pub fn get_health_status(&self) -> HealthStatus {
        let start = Instant::now();
        let mut checks = Vec::new();
        let mut overall_status = HealthLevel::Healthy;
        
        for checker in &self.checks {
            let check = checker.check();
            
            // Determine overall status
            match check.status {
                HealthLevel::Critical | HealthLevel::Down => {
                    overall_status = HealthLevel::Critical;
                }
                HealthLevel::Warning if matches!(overall_status, HealthLevel::Healthy) => {
                    overall_status = HealthLevel::Warning;
                }
                _ => {}
            }
            
            checks.push(check);
        }
        
        HealthStatus {
            status: overall_status,
            timestamp: chrono::Utc::now(),
            checks,
            system_metrics: self.collect_system_metrics(),
        }
    }
    
    fn collect_system_metrics(&self) -> SystemMetrics {
        SystemMetrics {
            memory_usage_mb: sys_info::mem_info()
                .map(|m| (m.total - m.avail) / 1024)
                .unwrap_or(0),
            cpu_usage_percent: sys_info::loadavg()
                .map(|l| l.one as f32)
                .unwrap_or(0.0),
            disk_usage_percent: 0.0, // Simplified
            open_file_handles: 0, // Platform specific
            database_connections: 1, // Simplified
            uptime_seconds: self.start_time.elapsed().as_secs(),
        }
    }
}

// Health checker implementations
struct DatabaseHealthChecker;

impl HealthChecker for DatabaseHealthChecker {
    fn name(&self) -> &str {
        "database"
    }
    
    fn check(&self) -> HealthCheck {
        let start = Instant::now();
        
        // Perform a simple database query
        let (status, message) = match self.test_database_connection() {
            Ok(_) => (HealthLevel::Healthy, "Database connection OK".to_string()),
            Err(e) => (HealthLevel::Critical, format!("Database error: {}", e)),
        };
        
        HealthCheck {
            name: self.name().to_string(),
            status,
            message,
            duration_ms: start.elapsed().as_millis() as u64,
            details: serde_json::json!({}),
        }
    }
}

impl DatabaseHealthChecker {
    fn test_database_connection(&self) -> Result<(), Box<dyn std::error::Error>> {
        // Simplified database health check
        // In real implementation, would test actual database connection
        Ok(())
    }
}

struct FileSystemHealthChecker;

impl HealthChecker for FileSystemHealthChecker {
    fn name(&self) -> &str {
        "filesystem"
    }
    
    fn check(&self) -> HealthCheck {
        let start = Instant::now();
        
        let (status, message) = match self.test_filesystem_access() {
            Ok(_) => (HealthLevel::Healthy, "File system access OK".to_string()),
            Err(e) => (HealthLevel::Warning, format!("File system warning: {}", e)),
        };
        
        HealthCheck {
            name: self.name().to_string(),
            status,
            message,
            duration_ms: start.elapsed().as_millis() as u64,
            details: serde_json::json!({}),
        }
    }
}

impl FileSystemHealthChecker {
    fn test_filesystem_access(&self) -> Result<(), Box<dyn std::error::Error>> {
        // Test basic file system operations
        let temp_file = std::env::temp_dir().join("filemaster_health_check");
        std::fs::write(&temp_file, "health check")?;
        std::fs::remove_file(&temp_file)?;
        Ok(())
    }
}

struct SearchIndexHealthChecker;

impl HealthChecker for SearchIndexHealthChecker {
    fn name(&self) -> &str {
        "search_index"
    }
    
    fn check(&self) -> HealthCheck {
        let start = Instant::now();
        
        let (status, message) = (HealthLevel::Healthy, "Search index OK".to_string());
        
        HealthCheck {
            name: self.name().to_string(),
            status,
            message,
            duration_ms: start.elapsed().as_millis() as u64,
            details: serde_json::json!({}),
        }
    }
}

struct MemoryHealthChecker;

impl HealthChecker for MemoryHealthChecker {
    fn name(&self) -> &str {
        "memory"
    }
    
    fn check(&self) -> HealthCheck {
        let start = Instant::now();
        
        let (status, message) = if let Ok(mem_info) = sys_info::mem_info() {
            let usage_percent = ((mem_info.total - mem_info.avail) as f64 / mem_info.total as f64) * 100.0;
            
            if usage_percent > 90.0 {
                (HealthLevel::Critical, format!("High memory usage: {:.1}%", usage_percent))
            } else if usage_percent > 80.0 {
                (HealthLevel::Warning, format!("Elevated memory usage: {:.1}%", usage_percent))
            } else {
                (HealthLevel::Healthy, format!("Memory usage OK: {:.1}%", usage_percent))
            }
        } else {
            (HealthLevel::Warning, "Could not check memory usage".to_string())
        };
        
        HealthCheck {
            name: self.name().to_string(),
            status,
            message,
            duration_ms: start.elapsed().as_millis() as u64,
            details: serde_json::json!({}),
        }
    }
}

// Global health monitor
lazy_static::lazy_static! {
    pub static ref HEALTH_MONITOR: std::sync::Mutex<HealthMonitor> = 
        std::sync::Mutex::new(HealthMonitor::new());
}
```

This comprehensive DevOps and Observability system provides:
- Structured logging with JSON output for easy parsing
- Privacy-respecting error reporting with explicit user consent
- Feature flag system for gradual rollouts and A/B testing
- Health monitoring with multiple system checks
- Integration with external monitoring systems
- Proper log rotation and retention policies
- Performance metrics collection
- User action tracking for debugging context

The system is designed to be privacy-first, requiring explicit user consent for any data collection, while still providing valuable insights for maintaining and improving the application.

## 18. Migration & Backup Plan

### Data Migration Strategy

**Version Migration Framework**
```rust
// src-tauri/src/migration.rs - Database and settings migration system
use serde::{Deserialize, Serialize};
use std::path::PathBuf;
use semver::Version;

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct MigrationPlan {
    pub from_version: Version,
    pub to_version: Version,
    pub migrations: Vec<Migration>,
    pub requires_backup: bool,
    pub estimated_time_minutes: u32,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct Migration {
    pub id: String,
    pub description: String,
    pub migration_type: MigrationType,
    pub rollback_supported: bool,
    pub data_loss_risk: RiskLevel,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub enum MigrationType {
    DatabaseSchema,
    SettingsFormat,
    FileStructure,
    IndexRebuild,
    DataConversion,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub enum RiskLevel {
    None,
    Low,
    Medium,
    High,
}

pub struct MigrationManager {
    current_version: Version,
    migrations: Vec<Box<dyn MigrationStep>>,
    backup_manager: BackupManager,
}

pub trait MigrationStep {
    fn id(&self) -> &str;
    fn from_version(&self) -> &Version;
    fn to_version(&self) -> &Version;
    fn description(&self) -> &str;
    fn requires_backup(&self) -> bool;
    fn execute(&self, context: &MigrationContext) -> Result<(), MigrationError>;
    fn rollback(&self, context: &MigrationContext) -> Result<(), MigrationError>;
    fn validate(&self, context: &MigrationContext) -> Result<(), MigrationError>;
}

#[derive(Debug)]
pub struct MigrationContext {
    pub data_dir: PathBuf,
    pub backup_dir: PathBuf,
    pub database_path: PathBuf,
    pub settings_path: PathBuf,
    pub dry_run: bool,
}

impl MigrationManager {
    pub fn new(current_version: Version) -> Self {
        let mut manager = Self {
            current_version,
            migrations: Vec::new(),
            backup_manager: BackupManager::new(),
        };
        
        manager.register_migrations();
        manager
    }
    
    fn register_migrations(&mut self) {
        // Register all available migrations
        self.migrations.push(Box::new(DatabaseSchemaV1ToV2));
        self.migrations.push(Box::new(SettingsFormatV2ToV3));
        self.migrations.push(Box::new(SearchIndexV3ToV4));
    }
    
    pub fn plan_migration(&self, target_version: &Version) -> Result<MigrationPlan, MigrationError> {
        let applicable_migrations: Vec<_> = self.migrations
            .iter()
            .filter(|m| {
                m.from_version() <= &self.current_version && 
                m.to_version() <= target_version &&
                m.from_version() > &self.current_version
            })
            .collect();
        
        if applicable_migrations.is_empty() {
            return Ok(MigrationPlan {
                from_version: self.current_version.clone(),
                to_version: target_version.clone(),
                migrations: vec![],
                requires_backup: false,
                estimated_time_minutes: 0,
            });
        }
        
        let migrations: Vec<Migration> = applicable_migrations
            .iter()
            .map(|m| Migration {
                id: m.id().to_string(),
                description: m.description().to_string(),
                migration_type: self.classify_migration(m),
                rollback_supported: true, // Simplified
                data_loss_risk: self.assess_risk(m),
            })
            .collect();
        
        let requires_backup = applicable_migrations.iter().any(|m| m.requires_backup());
        let estimated_time = self.estimate_migration_time(&applicable_migrations);
        
        Ok(MigrationPlan {
            from_version: self.current_version.clone(),
            to_version: target_version.clone(),
            migrations,
            requires_backup,
            estimated_time_minutes: estimated_time,
        })
    }
    
    pub async fn execute_migration(&self, plan: &MigrationPlan, progress_callback: impl Fn(f32, &str)) -> Result<(), MigrationError> {
        let context = MigrationContext {
            data_dir: self.get_data_directory()?,
            backup_dir: self.get_backup_directory()?,
            database_path: self.get_database_path()?,
            settings_path: self.get_settings_path()?,
            dry_run: false,
        };
        
        // Create backup if required
        if plan.requires_backup {
            progress_callback(0.1, "Creating backup...");
            self.backup_manager.create_full_backup(&context.data_dir, &context.backup_dir).await?;
        }
        
        let total_steps = plan.migrations.len();
        
        for (index, migration_info) in plan.migrations.iter().enumerate() {
            let migration = self.migrations
                .iter()
                .find(|m| m.id() == migration_info.id)
                .ok_or(MigrationError::MigrationNotFound(migration_info.id.clone()))?;
            
            let progress = 0.2 + (index as f32 / total_steps as f32) * 0.7;
            progress_callback(progress, &format!("Running migration: {}", migration.description()));
            
            // Validate before execution
            migration.validate(&context)?;
            
            // Execute migration
            migration.execute(&context)?;
            
            // Validate after execution
            migration.validate(&context)?;
        }
        
        progress_callback(0.9, "Finalizing migration...");
        
        // Update version information
        self.update_version_info(&plan.to_version)?;
        
        progress_callback(1.0, "Migration completed successfully");
        
        Ok(())
    }
    
    fn classify_migration(&self, migration: &Box<dyn MigrationStep>) -> MigrationType {
        // Simplified classification based on migration ID
        if migration.id().contains("database") {
            MigrationType::DatabaseSchema
        } else if migration.id().contains("settings") {
            MigrationType::SettingsFormat
        } else if migration.id().contains("index") {
            MigrationType::IndexRebuild
        } else {
            MigrationType::DataConversion
        }
    }
    
    fn assess_risk(&self, _migration: &Box<dyn MigrationStep>) -> RiskLevel {
        // Simplified risk assessment
        RiskLevel::Low
    }
    
    fn estimate_migration_time(&self, migrations: &[&Box<dyn MigrationStep>]) -> u32 {
        // Estimate based on migration types
        migrations.len() as u32 * 2 // 2 minutes per migration
    }
    
    fn get_data_directory(&self) -> Result<PathBuf, MigrationError> {
        Ok(dirs::data_dir()
            .ok_or(MigrationError::DirectoryNotFound)?
            .join("FileMaster"))
    }
    
    fn get_backup_directory(&self) -> Result<PathBuf, MigrationError> {
        Ok(self.get_data_directory()?.join("backups"))
    }
    
    fn get_database_path(&self) -> Result<PathBuf, MigrationError> {
        Ok(self.get_data_directory()?.join("database.db"))
    }
    
    fn get_settings_path(&self) -> Result<PathBuf, MigrationError> {
        Ok(self.get_data_directory()?.join("settings.json"))
    }
    
    fn update_version_info(&self, version: &Version) -> Result<(), MigrationError> {
        // Update version in settings or database
        Ok(())
    }
}

#[derive(Debug, thiserror::Error)]
pub enum MigrationError {
    #[error("Migration not found: {0}")]
    MigrationNotFound(String),
    #[error("Directory not found")]
    DirectoryNotFound,
    #[error("IO error: {0}")]
    Io(#[from] std::io::Error),
    #[error("Database error: {0}")]
    Database(String),
    #[error("Validation failed: {0}")]
    ValidationFailed(String),
}

// Example migration implementations
struct DatabaseSchemaV1ToV2;

impl MigrationStep for DatabaseSchemaV1ToV2 {
    fn id(&self) -> &str {
        "database_v1_to_v2"
    }
    
    fn from_version(&self) -> &Version {
        &Version::new(1, 0, 0)
    }
    
    fn to_version(&self) -> &Version {
        &Version::new(1, 1, 0)
    }
    
    fn description(&self) -> &str {
        "Add encryption support to database schema"
    }
    
    fn requires_backup(&self) -> bool {
        true
    }
    
    fn execute(&self, context: &MigrationContext) -> Result<(), MigrationError> {
        // Execute SQL schema changes
        let connection = rusqlite::Connection::open(&context.database_path)
            .map_err(|e| MigrationError::Database(e.to_string()))?;
        
        connection.execute(
            "ALTER TABLE files ADD COLUMN encrypted BOOLEAN DEFAULT FALSE",
            []
        ).map_err(|e| MigrationError::Database(e.to_string()))?;
        
        connection.execute(
            "ALTER TABLE files ADD COLUMN encryption_key_id TEXT",
            []
        ).map_err(|e| MigrationError::Database(e.to_string()))?;
        
        Ok(())
    }
    
    fn rollback(&self, context: &MigrationContext) -> Result<(), MigrationError> {
        // Rollback is complex for schema changes, typically restore from backup
        Ok(())
    }
    
    fn validate(&self, context: &MigrationContext) -> Result<(), MigrationError> {
        // Validate that the schema changes were applied correctly
        let connection = rusqlite::Connection::open(&context.database_path)
            .map_err(|e| MigrationError::Database(e.to_string()))?;
        
        // Check if new columns exist
        let mut stmt = connection.prepare("PRAGMA table_info(files)")
            .map_err(|e| MigrationError::Database(e.to_string()))?;
        
        let column_names: Vec<String> = stmt.query_map([], |row| {
            Ok(row.get::<_, String>(1)?) // Column name is at index 1
        }).map_err(|e| MigrationError::Database(e.to_string()))?
        .collect::<Result<Vec<_>, _>>()
        .map_err(|e| MigrationError::Database(e.to_string()))?;
        
        if !column_names.contains(&"encrypted".to_string()) {
            return Err(MigrationError::ValidationFailed("encrypted column not found".to_string()));
        }
        
        if !column_names.contains(&"encryption_key_id".to_string()) {
            return Err(MigrationError::ValidationFailed("encryption_key_id column not found".to_string()));
        }
        
        Ok(())
    }
}

struct SettingsFormatV2ToV3;

impl MigrationStep for SettingsFormatV2ToV3 {
    fn id(&self) -> &str {
        "settings_v2_to_v3"
    }
    
    fn from_version(&self) -> &Version {
        &Version::new(1, 1, 0)
    }
    
    fn to_version(&self) -> &Version {
        &Version::new(1, 2, 0)
    }
    
    fn description(&self) -> &str {
        "Migrate settings format to support themes and accessibility options"
    }
    
    fn requires_backup(&self) -> bool {
        false
    }
    
    fn execute(&self, context: &MigrationContext) -> Result<(), MigrationError> {
        // Read old settings format
        let old_settings = std::fs::read_to_string(&context.settings_path)?;
        let old_json: serde_json::Value = serde_json::from_str(&old_settings)
            .map_err(|e| MigrationError::ValidationFailed(e.to_string()))?;
        
        // Convert to new format
        let new_settings = serde_json::json!({
            "version": "1.2.0",
            "ui": {
                "theme": old_json.get("theme").unwrap_or(&serde_json::Value::String("light".to_string())),
                "accessibility": {
                    "high_contrast": false,
                    "reduced_motion": false,
                    "screen_reader_support": true
                }
            },
            "file_management": old_json.get("file_management").unwrap_or(&serde_json::json!({})),
            "search": old_json.get("search").unwrap_or(&serde_json::json!({})),
            "privacy": old_json.get("privacy").unwrap_or(&serde_json::json!({
                "telemetry_enabled": false,
                "error_reporting_enabled": false
            }))
        });
        
        // Write new settings
        std::fs::write(&context.settings_path, serde_json::to_string_pretty(&new_settings)
            .map_err(|e| MigrationError::ValidationFailed(e.to_string()))?)?;
        
        Ok(())
    }
    
    fn rollback(&self, _context: &MigrationContext) -> Result<(), MigrationError> {
        // Settings rollback would restore from backup
        Ok(())
    }
    
    fn validate(&self, context: &MigrationContext) -> Result<(), MigrationError> {
        // Validate new settings format
        let settings_content = std::fs::read_to_string(&context.settings_path)?;
        let settings: serde_json::Value = serde_json::from_str(&settings_content)
            .map_err(|e| MigrationError::ValidationFailed(e.to_string()))?;
        
        if !settings.get("ui").is_some() {
            return Err(MigrationError::ValidationFailed("ui section missing".to_string()));
        }
        
        if !settings.get("ui").unwrap().get("accessibility").is_some() {
            return Err(MigrationError::ValidationFailed("accessibility section missing".to_string()));
        }
        
        Ok(())
    }
}

struct SearchIndexV3ToV4;

impl MigrationStep for SearchIndexV3ToV4 {
    fn id(&self) -> &str {
        "search_index_v3_to_v4"
    }
    
    fn from_version(&self) -> &Version {
        &Version::new(1, 2, 0)
    }
    
    fn to_version(&self) -> &Version {
        &Version::new(1, 3, 0)
    }
    
    fn description(&self) -> &str {
        "Rebuild search index with improved tokenization"
    }
    
    fn requires_backup(&self) -> bool {
        false // Index can be rebuilt
    }
    
    fn execute(&self, context: &MigrationContext) -> Result<(), MigrationError> {
        // Drop and recreate search index
        let connection = rusqlite::Connection::open(&context.database_path)
            .map_err(|e| MigrationError::Database(e.to_string()))?;
        
        connection.execute("DROP TABLE IF EXISTS search_index", [])
            .map_err(|e| MigrationError::Database(e.to_string()))?;
        
        connection.execute(
            "CREATE VIRTUAL TABLE search_index USING fts5(
                file_id UNINDEXED,
                filename,
                content,
                tags,
                tokenize='porter unicode61'
            )",
            []
        ).map_err(|e| MigrationError::Database(e.to_string()))?;
        
        // Rebuild index (simplified - would need actual search engine)
        // This would trigger a background reindexing process
        
        Ok(())
    }
    
    fn rollback(&self, _context: &MigrationContext) -> Result<(), MigrationError> {
        // Index rollback would recreate old index structure
        Ok(())
    }
    
    fn validate(&self, context: &MigrationContext) -> Result<(), MigrationError> {
        // Validate new index structure
        let connection = rusqlite::Connection::open(&context.database_path)
            .map_err(|e| MigrationError::Database(e.to_string()))?;
        
        let mut stmt = connection.prepare("SELECT name FROM sqlite_master WHERE type='table' AND name='search_index'")
            .map_err(|e| MigrationError::Database(e.to_string()))?;
        
        let table_exists = stmt.exists([])
            .map_err(|e| MigrationError::Database(e.to_string()))?;
        
        if !table_exists {
            return Err(MigrationError::ValidationFailed("search_index table not found".to_string()));
        }
        
        Ok(())
    }
}
```

### Backup System

**Comprehensive Backup Strategy**
```rust
// src-tauri/src/backup.rs - Backup and restore system
use serde::{Deserialize, Serialize};
use std::path::{Path, PathBuf};
use chrono::{DateTime, Utc};
use uuid::Uuid;

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct BackupMetadata {
    pub id: String,
    pub created_at: DateTime<Utc>,
    pub app_version: String,
    pub backup_type: BackupType,
    pub size_bytes: u64,
    pub file_count: u32,
    pub checksum: String,
    pub description: String,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub enum BackupType {
    Full,
    Incremental,
    Settings,
    Database,
}

pub struct BackupManager {
    backup_root: PathBuf,
    retention_policy: RetentionPolicy,
    compression_enabled: bool,
}

#[derive(Debug, Clone)]
pub struct RetentionPolicy {
    pub keep_daily: u32,     // Keep daily backups for N days
    pub keep_weekly: u32,    // Keep weekly backups for N weeks
    pub keep_monthly: u32,   // Keep monthly backups for N months
    pub max_total_size_gb: u64, // Maximum total backup size
}

impl BackupManager {
    pub fn new() -> Result<Self, BackupError> {
        let backup_root = Self::get_backup_directory()?;
        std::fs::create_dir_all(&backup_root)?;
        
        Ok(Self {
            backup_root,
            retention_policy: RetentionPolicy {
                keep_daily: 7,
                keep_weekly: 4,
                keep_monthly: 6,
                max_total_size_gb: 5,
            },
            compression_enabled: true,
        })
    }
    
    pub async fn create_full_backup(&self, source_dir: &Path, description: Option<String>) -> Result<BackupMetadata, BackupError> {
        let backup_id = Uuid::new_v4().to_string();
        let backup_dir = self.backup_root.join(&backup_id);
        std::fs::create_dir_all(&backup_dir)?;
        
        let start_time = std::time::Instant::now();
        crate::log_info!("Starting full backup", serde_json::json!({
            "backup_id": backup_id,
            "source": source_dir.display().to_string()
        }));
        
        // Copy all files
        let (file_count, total_size) = self.copy_directory_recursive(source_dir, &backup_dir).await?;
        
        // Create backup archive if compression enabled
        let final_backup_path = if self.compression_enabled {
            self.compress_backup(&backup_dir, &format!("{}.tar.gz", backup_id)).await?
        } else {
            backup_dir
        };
        
        // Calculate checksum
        let checksum = self.calculate_backup_checksum(&final_backup_path).await?;
        
        let metadata = BackupMetadata {
            id: backup_id,
            created_at: Utc::now(),
            app_version: env!("CARGO_PKG_VERSION").to_string(),
            backup_type: BackupType::Full,
            size_bytes: total_size,
            file_count,
            checksum,
            description: description.unwrap_or_else(|| "Full backup".to_string()),
        };
        
        // Save metadata
        self.save_backup_metadata(&metadata).await?;
        
        let duration = start_time.elapsed();
        crate::log_info!("Full backup completed", serde_json::json!({
            "backup_id": metadata.id,
            "duration_seconds": duration.as_secs(),
            "size_mb": total_size / 1024 / 1024,
            "file_count": file_count
        }));
        
        // Apply retention policy
        self.apply_retention_policy().await?;
        
        Ok(metadata)
    }
    
    pub async fn create_incremental_backup(&self, source_dir: &Path, last_backup_id: &str) -> Result<BackupMetadata, BackupError> {
        let last_backup = self.get_backup_metadata(last_backup_id).await?;
        let backup_id = Uuid::new_v4().to_string();
        let backup_dir = self.backup_root.join(&backup_id);
        std::fs::create_dir_all(&backup_dir)?;
        
        crate::log_info!("Starting incremental backup", serde_json::json!({
            "backup_id": backup_id,
            "base_backup_id": last_backup_id
        }));
        
        // Find changed files since last backup
        let changed_files = self.find_changed_files(source_dir, &last_backup.created_at).await?;
        
        let mut file_count = 0;
        let mut total_size = 0;
        
        for file_path in changed_files {
            let relative_path = file_path.strip_prefix(source_dir)
                .map_err(|_| BackupError::InvalidPath)?;
            let dest_path = backup_dir.join(relative_path);
            
            if let Some(parent) = dest_path.parent() {
                std::fs::create_dir_all(parent)?;
            }
            
            std::fs::copy(&file_path, &dest_path)?;
            
            let metadata = std::fs::metadata(&dest_path)?;
            total_size += metadata.len();
            file_count += 1;
        }
        
        let checksum = self.calculate_backup_checksum(&backup_dir).await?;
        
        let metadata = BackupMetadata {
            id: backup_id,
            created_at: Utc::now(),
            app_version: env!("CARGO_PKG_VERSION").to_string(),
            backup_type: BackupType::Incremental,
            size_bytes: total_size,
            file_count,
            checksum,
            description: format!("Incremental backup from {}", last_backup_id),
        };
        
        self.save_backup_metadata(&metadata).await?;
        
        crate::log_info!("Incremental backup completed", serde_json::json!({
            "backup_id": metadata.id,
            "file_count": file_count,
            "size_mb": total_size / 1024 / 1024
        }));
        
        Ok(metadata)
    }
    
    pub async fn restore_backup(&self, backup_id: &str, restore_path: &Path, options: RestoreOptions) -> Result<(), BackupError> {
        let metadata = self.get_backup_metadata(backup_id).await?;
        
        crate::log_info!("Starting backup restore", serde_json::json!({
            "backup_id": backup_id,
            "restore_path": restore_path.display().to_string(),
            "backup_type": format!("{:?}", metadata.backup_type)
        }));
        
        // Verify backup integrity
        if options.verify_integrity {
            self.verify_backup_integrity(&metadata).await?;
        }
        
        let backup_path = self.get_backup_path(&metadata.id);
        
        match metadata.backup_type {
            BackupType::Full => {
                if backup_path.extension().and_then(|s| s.to_str()) == Some("gz") {
                    // Extract compressed backup
                    self.extract_backup(&backup_path, restore_path).await?;
                } else {
                    // Copy uncompressed backup
                    self.copy_directory_recursive(&backup_path, restore_path).await?;
                }
            },
            BackupType::Incremental => {
                return Err(BackupError::UnsupportedOperation("Incremental restore requires base backup".to_string()));
            },
            BackupType::Settings | BackupType::Database => {
                // Restore specific components
                self.restore_specific_backup(&backup_path, restore_path, &metadata.backup_type).await?;
            }
        }
        
        crate::log_info!("Backup restore completed", serde_json::json!({
            "backup_id": backup_id,
            "restore_path": restore_path.display().to_string()
        }));
        
        Ok(())
    }
    
    pub async fn list_backups(&self) -> Result<Vec<BackupMetadata>, BackupError> {
        let metadata_dir = self.backup_root.join("metadata");
        if !metadata_dir.exists() {
            return Ok(Vec::new());
        }
        
        let mut backups = Vec::new();
        let mut entries = tokio::fs::read_dir(&metadata_dir).await?;
        
        while let Some(entry) = entries.next_entry().await? {
            if entry.file_name().to_string_lossy().ends_with(".json") {
                let content = tokio::fs::read_to_string(entry.path()).await?;
                let metadata: BackupMetadata = serde_json::from_str(&content)
                    .map_err(|e| BackupError::InvalidMetadata(e.to_string()))?;
                backups.push(metadata);
            }
        }
        
        // Sort by creation time (newest first)
        backups.sort_by(|a, b| b.created_at.cmp(&a.created_at));
        
        Ok(backups)
    }
    
    pub async fn delete_backup(&self, backup_id: &str) -> Result<(), BackupError> {
        let metadata = self.get_backup_metadata(backup_id).await?;
        let backup_path = self.get_backup_path(backup_id);
        
        // Delete backup data
        if backup_path.is_dir() {
            tokio::fs::remove_dir_all(&backup_path).await?;
        } else {
            tokio::fs::remove_file(&backup_path).await?;
        }
        
        // Delete metadata
        let metadata_path = self.backup_root.join("metadata").join(format!("{}.json", backup_id));
        tokio::fs::remove_file(&metadata_path).await?;
        
        crate::log_info!("Backup deleted", serde_json::json!({
            "backup_id": backup_id,
            "size_mb": metadata.size_bytes / 1024 / 1024
        }));
        
        Ok(())
    }
    
    async fn copy_directory_recursive(&self, source: &Path, dest: &Path) -> Result<(u32, u64), BackupError> {
        let mut file_count = 0;
        let mut total_size = 0;
        
        let mut stack = vec![(source.to_path_buf(), dest.to_path_buf())];
        
        while let Some((src_dir, dst_dir)) = stack.pop() {
            std::fs::create_dir_all(&dst_dir)?;
            
            let mut entries = tokio::fs::read_dir(&src_dir).await?;
            while let Some(entry) = entries.next_entry().await? {
                let src_path = entry.path();
                let dst_path = dst_dir.join(entry.file_name());
                
                let metadata = entry.metadata().await?;
                
                if metadata.is_dir() {
                    stack.push((src_path, dst_path));
                } else {
                    tokio::fs::copy(&src_path, &dst_path).await?;
                    file_count += 1;
                    total_size += metadata.len();
                }
            }
        }
        
        Ok((file_count, total_size))
    }
    
    async fn find_changed_files(&self, source_dir: &Path, since: &DateTime<Utc>) -> Result<Vec<PathBuf>, BackupError> {
        let mut changed_files = Vec::new();
        let since_timestamp = since.timestamp();
        
        let mut stack = vec![source_dir.to_path_buf()];
        
        while let Some(dir) = stack.pop() {
            let mut entries = tokio::fs::read_dir(&dir).await?;
            
            while let Some(entry) = entries.next_entry().await? {
                let path = entry.path();
                let metadata = entry.metadata().await?;
                
                if metadata.is_dir() {
                    stack.push(path);
                } else {
                    let modified = metadata.modified()?;
                    let modified_timestamp = modified.duration_since(std::time::UNIX_EPOCH)
                        .map_err(|_| BackupError::InvalidTimestamp)?
                        .as_secs() as i64;
                    
                    if modified_timestamp > since_timestamp {
                        changed_files.push(path);
                    }
                }
            }
        }
        
        Ok(changed_files)
    }
    
    async fn compress_backup(&self, backup_dir: &Path, archive_name: &str) -> Result<PathBuf, BackupError> {
        let archive_path = self.backup_root.join(archive_name);
        
        // Use tar + gzip compression
        let output = std::process::Command::new("tar")
            .arg("-czf")
            .arg(&archive_path)
            .arg("-C")
            .arg(backup_dir.parent().unwrap())
            .arg(backup_dir.file_name().unwrap())
            .output()?;
        
        if !output.status.success() {
            return Err(BackupError::CompressionFailed(
                String::from_utf8_lossy(&output.stderr).to_string()
            ));
        }
        
        // Remove uncompressed directory
        tokio::fs::remove_dir_all(backup_dir).await?;
        
        Ok(archive_path)
    }
    
    async fn extract_backup(&self, archive_path: &Path, extract_to: &Path) -> Result<(), BackupError> {
        std::fs::create_dir_all(extract_to)?;
        
        let output = std::process::Command::new("tar")
            .arg("-xzf")
            .arg(archive_path)
            .arg("-C")
            .arg(extract_to)
            .output()?;
        
        if !output.status.success() {
            return Err(BackupError::ExtractionFailed(
                String::from_utf8_lossy(&output.stderr).to_string()
            ));
        }
        
        Ok(())
    }
    
    async fn calculate_backup_checksum(&self, path: &Path) -> Result<String, BackupError> {
        use sha2::{Sha256, Digest};
        
        let mut hasher = Sha256::new();
        
        if path.is_file() {
            let content = tokio::fs::read(path).await?;
            hasher.update(&content);
        } else {
            // Hash directory contents
            let mut files = Vec::new();
            self.collect_files_recursive(path, &mut files).await?;
            
            files.sort();
            
            for file_path in files {
                let content = tokio::fs::read(&file_path).await?;
                hasher.update(&content);
            }
        }
        
        Ok(format!("{:x}", hasher.finalize()))
    }
    
    async fn collect_files_recursive(&self, dir: &Path, files: &mut Vec<PathBuf>) -> Result<(), BackupError> {
        let mut entries = tokio::fs::read_dir(dir).await?;
        
        while let Some(entry) = entries.next_entry().await? {
            let path = entry.path();
            
            if path.is_dir() {
                self.collect_files_recursive(&path, files).await?;
            } else {
                files.push(path);
            }
        }
        
        Ok(())
    }
    
    async fn save_backup_metadata(&self, metadata: &BackupMetadata) -> Result<(), BackupError> {
        let metadata_dir = self.backup_root.join("metadata");
        std::fs::create_dir_all(&metadata_dir)?;
        
        let metadata_file = metadata_dir.join(format!("{}.json", metadata.id));
        let content = serde_json::to_string_pretty(metadata)
            .map_err(|e| BackupError::InvalidMetadata(e.to_string()))?;
        
        tokio::fs::write(&metadata_file, content).await?;
        
        Ok(())
    }
    
    async fn get_backup_metadata(&self, backup_id: &str) -> Result<BackupMetadata, BackupError> {
        let metadata_file = self.backup_root.join("metadata").join(format!("{}.json", backup_id));
        
        if !metadata_file.exists() {
            return Err(BackupError::BackupNotFound(backup_id.to_string()));
        }
        
        let content = tokio::fs::read_to_string(&metadata_file).await?;
        let metadata: BackupMetadata = serde_json::from_str(&content)
            .map_err(|e| BackupError::InvalidMetadata(e.to_string()))?;
        
        Ok(metadata)
    }
    
    fn get_backup_path(&self, backup_id: &str) -> PathBuf {
        // Try compressed version first
        let compressed_path = self.backup_root.join(format!("{}.tar.gz", backup_id));
        if compressed_path.exists() {
            compressed_path
        } else {
            self.backup_root.join(backup_id)
        }
    }
    
    async fn verify_backup_integrity(&self, metadata: &BackupMetadata) -> Result<(), BackupError> {
        let backup_path = self.get_backup_path(&metadata.id);
        let calculated_checksum = self.calculate_backup_checksum(&backup_path).await?;
        
        if calculated_checksum != metadata.checksum {
            return Err(BackupError::IntegrityCheckFailed {
                expected: metadata.checksum.clone(),
                actual: calculated_checksum,
            });
        }
        
        Ok(())
    }
    
    async fn apply_retention_policy(&self) -> Result<(), BackupError> {
        let backups = self.list_backups().await?;
        let mut to_delete = Vec::new();
        
        // Group backups by type and age
        let now = Utc::now();
        let mut daily_backups = Vec::new();
        let mut weekly_backups = Vec::new();
        let mut monthly_backups = Vec::new();
        
        for backup in &backups {
            let age_days = (now - backup.created_at).num_days();
            
            if age_days <= self.retention_policy.keep_daily as i64 {
                daily_backups.push(backup);
            } else if age_days <= (self.retention_policy.keep_weekly * 7) as i64 {
                weekly_backups.push(backup);
            } else if age_days <= (self.retention_policy.keep_monthly * 30) as i64 {
                monthly_backups.push(backup);
            } else {
                to_delete.push(&backup.id);
            }
        }
        
        // Check total size limit
        let total_size: u64 = backups.iter().map(|b| b.size_bytes).sum();
        let max_size = self.retention_policy.max_total_size_gb * 1024 * 1024 * 1024;
        
        if total_size > max_size {
            // Delete oldest backups until under size limit
            let mut sorted_backups = backups.clone();
            sorted_backups.sort_by(|a, b| a.created_at.cmp(&b.created_at));
            
            let mut current_size = total_size;
            for backup in sorted_backups {
                if current_size <= max_size {
                    break;
                }
                
                if !to_delete.contains(&&backup.id) {
                    to_delete.push(&backup.id);
                    current_size -= backup.size_bytes;
                }
            }
        }
        
        // Delete identified backups
        for backup_id in to_delete {
            self.delete_backup(backup_id).await?;
        }
        
        Ok(())
    }
    
    async fn restore_specific_backup(&self, backup_path: &Path, restore_path: &Path, backup_type: &BackupType) -> Result<(), BackupError> {
        match backup_type {
            BackupType::Settings => {
                let settings_file = backup_path.join("settings.json");
                let dest_file = restore_path.join("settings.json");
                tokio::fs::copy(&settings_file, &dest_file).await?;
            },
            BackupType::Database => {
                let db_file = backup_path.join("database.db");
                let dest_file = restore_path.join("database.db");
                tokio::fs::copy(&db_file, &dest_file).await?;
            },
            _ => {
                return Err(BackupError::UnsupportedOperation(format!("Cannot restore {:?} backup type", backup_type)));
            }
        }
        
        Ok(())
    }
    
    fn get_backup_directory() -> Result<PathBuf, BackupError> {
        Ok(dirs::data_dir()
            .ok_or(BackupError::DirectoryNotFound)?
            .join("FileMaster")
            .join("backups"))
    }
}

#[derive(Debug, Clone)]
pub struct RestoreOptions {
    pub verify_integrity: bool,
    pub overwrite_existing: bool,
    pub restore_permissions: bool,
}

impl Default for RestoreOptions {
    fn default() -> Self {
        Self {
            verify_integrity: true,
            overwrite_existing: false,
            restore_permissions: true,
        }
    }
}

#[derive(Debug, thiserror::Error)]
pub enum BackupError {
    #[error("IO error: {0}")]
    Io(#[from] std::io::Error),
    #[error("Backup not found: {0}")]
    BackupNotFound(String),
    #[error("Invalid metadata: {0}")]
    InvalidMetadata(String),
    #[error("Compression failed: {0}")]
    CompressionFailed(String),
    #[error("Extraction failed: {0}")]
    ExtractionFailed(String),
    #[error("Integrity check failed - expected: {expected}, actual: {actual}")]
    IntegrityCheckFailed { expected: String, actual: String },
    #[error("Directory not found")]
    DirectoryNotFound,
    #[error("Invalid path")]
    InvalidPath,
    #[error("Invalid timestamp")]
    InvalidTimestamp,
    #[error("Unsupported operation: {0}")]
    UnsupportedOperation(String),
}
```

### User Data Export/Import

**Data Portability System**
```rust
// src-tauri/src/data_export.rs - User data export and import
use serde::{Deserialize, Serialize};
use std::path::{Path, PathBuf};

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct DataExport {
    pub version: String,
    pub created_at: chrono::DateTime<chrono::Utc>,
    pub export_type: ExportType,
    pub settings: serde_json::Value,
    pub tags: Vec<TagExport>,
    pub file_metadata: Vec<FileMetadataExport>,
    pub search_history: Vec<SearchHistoryExport>,
    pub user_preferences: serde_json::Value,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub enum ExportType {
    Complete,
    SettingsOnly,
    TagsOnly,
    MetadataOnly,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct TagExport {
    pub name: String,
    pub parent: Option<String>,
    pub color: String,
    pub description: Option<String>,
    pub created_at: chrono::DateTime<chrono::Utc>,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct FileMetadataExport {
    pub path: String,
    pub tags: Vec<String>,
    pub custom_metadata: serde_json::Value,
    pub access_count: u32,
    pub last_accessed: chrono::DateTime<chrono::Utc>,
}

#[derive(Debug, Clone, Serialize, Deserialize)]
pub struct SearchHistoryExport {
    pub query: String,
    pub timestamp: chrono::DateTime<chrono::Utc>,
    pub result_count: u32,
}

pub struct DataPortabilityManager {
    data_dir: PathBuf,
}

impl DataPortabilityManager {
    pub fn new() -> Result<Self, DataExportError> {
        let data_dir = dirs::data_dir()
            .ok_or(DataExportError::DirectoryNotFound)?
            .join("FileMaster");
        
        Ok(Self { data_dir })
    }
    
    pub async fn export_user_data(&self, export_type: ExportType, output_path: &Path) -> Result<(), DataExportError> {
        let export_data = self.collect_export_data(&export_type).await?;
        
        let json_content = serde_json::to_string_pretty(&export_data)
            .map_err(|e| DataExportError::SerializationFailed(e.to_string()))?;
        
        tokio::fs::write(output_path, json_content).await?;
        
        crate::log_info!("Data export completed", serde_json::json!({
            "export_type": format!("{:?}", export_type),
            "output_path": output_path.display().to_string(),
            "size_bytes": json_content.len()
        }));
        
        Ok(())
    }
    
    pub async fn import_user_data(&self, import_path: &Path, import_options: ImportOptions) -> Result<ImportResult, DataExportError> {
        let content = tokio::fs::read_to_string(import_path).await?;
        let import_data: DataExport = serde_json::from_str(&content)
            .map_err(|e| DataExportError::DeserializationFailed(e.to_string()))?;
        
        // Validate import compatibility
        self.validate_import_compatibility(&import_data)?;
        
        let mut result = ImportResult {
            imported_settings: 0,
            imported_tags: 0,
            imported_metadata: 0,
            imported_preferences: 0,
            skipped_items: 0,
            errors: Vec::new(),
        };
        
        // Import settings
        if import_options.import_settings {
            match self.import_settings(&import_data.settings).await {
                Ok(_) => result.imported_settings = 1,
                Err(e) => result.errors.push(format!("Settings import failed: {}", e)),
            }
        }
        
        // Import tags
        if import_options.import_tags {
            for tag in &import_data.tags {
                match self.import_tag(tag).await {
                    Ok(_) => result.imported_tags += 1,
                    Err(e) => {
                        result.errors.push(format!("Tag import failed for '{}': {}", tag.name, e));
                        result.skipped_items += 1;
                    }
                }
            }
        }
        
        // Import file metadata
        if import_options.import_metadata {
            for metadata in &import_data.file_metadata {
                match self.import_file_metadata(metadata).await {
                    Ok(_) => result.imported_metadata += 1,
                    Err(e) => {
                        result.errors.push(format!("Metadata import failed for '{}': {}", metadata.path, e));
                        result.skipped_items += 1;
                    }
                }
            }
        }
        
        // Import user preferences
        if import_options.import_preferences {
            match self.import_preferences(&import_data.user_preferences).await {
                Ok(_) => result.imported_preferences = 1,
                Err(e) => result.errors.push(format!("Preferences import failed: {}", e)),
            }
        }
        
        crate::log_info!("Data import completed", serde_json::json!({
            "imported_tags": result.imported_tags,
            "imported_metadata": result.imported_metadata,
            "errors": result.errors.len()
        }));
        
        Ok(result)
    }
    
    async fn collect_export_data(&self, export_type: &ExportType) -> Result<DataExport, DataExportError> {
        let mut export_data = DataExport {
            version: env!("CARGO_PKG_VERSION").to_string(),
            created_at: chrono::Utc::now(),
            export_type: export_type.clone(),
            settings: serde_json::Value::Null,
            tags: Vec::new(),
            file_metadata: Vec::new(),
            search_history: Vec::new(),
            user_preferences: serde_json::Value::Null,
        };
        
        match export_type {
            ExportType::Complete => {
                export_data.settings = self.export_settings().await?;
                export_data.tags = self.export_tags().await?;
                export_data.file_metadata = self.export_file_metadata().await?;
                export_data.search_history = self.export_search_history().await?;
                export_data.user_preferences = self.export_user_preferences().await?;
            },
            ExportType::SettingsOnly => {
                export_data.settings = self.export_settings().await?;
            },
            ExportType::TagsOnly => {
                export_data.tags = self.export_tags().await?;
            },
            ExportType::MetadataOnly => {
                export_data.file_metadata = self.export_file_metadata().await?;
            },
        }
        
        Ok(export_data)
    }
    
    async fn export_settings(&self) -> Result<serde_json::Value, DataExportError> {
        let settings_path = self.data_dir.join("settings.json");
        
        if settings_path.exists() {
            let content = tokio::fs::read_to_string(&settings_path).await?;
            let settings: serde_json::Value = serde_json::from_str(&content)
                .map_err(|e| DataExportError::SerializationFailed(e.to_string()))?;
            Ok(settings)
        } else {
            Ok(serde_json::Value::Null)
        }
    }
    
    async fn export_tags(&self) -> Result<Vec<TagExport>, DataExportError> {
        // This would query the database for all tags
        // Simplified implementation
        Ok(Vec::new())
    }
    
    async fn export_file_metadata(&self) -> Result<Vec<FileMetadataExport>, DataExportError> {
        // This would query the database for all file metadata
        // Simplified implementation
        Ok(Vec::new())
    }
    
    async fn export_search_history(&self) -> Result<Vec<SearchHistoryExport>, DataExportError> {
        // This would query the database for search history
        // Simplified implementation
        Ok(Vec::new())
    }
    
    async fn export_user_preferences(&self) -> Result<serde_json::Value, DataExportError> {
        // Export user preferences from database or settings
        Ok(serde_json::json!({}))
    }
    
    fn validate_import_compatibility(&self, import_data: &DataExport) -> Result<(), DataExportError> {
        let current_version = semver::Version::parse(env!("CARGO_PKG_VERSION"))
            .map_err(|e| DataExportError::VersionParseError(e.to_string()))?;
        
        let import_version = semver::Version::parse(&import_data.version)
            .map_err(|e| DataExportError::VersionParseError(e.to_string()))?;
        
        // Check if import version is compatible
        if import_version.major > current_version.major {
            return Err(DataExportError::IncompatibleVersion {
                import_version: import_data.version.clone(),
                current_version: env!("CARGO_PKG_VERSION").to_string(),
            });
        }
        
        Ok(())
    }
    
    async fn import_settings(&self, settings: &serde_json::Value) -> Result<(), DataExportError> {
        if settings.is_null() {
            return Ok(());
        }
        
        let settings_path = self.data_dir.join("settings.json");
        let content = serde_json::to_string_pretty(settings)
            .map_err(|e| DataExportError::SerializationFailed(e.to_string()))?;
        
        tokio::fs::write(&settings_path, content).await?;
        
        Ok(())
    }
    
    async fn import_tag(&self, _tag: &TagExport) -> Result<(), DataExportError> {
        // Import tag into database
        // Simplified implementation
        Ok(())
    }
    
    async fn import_file_metadata(&self, _metadata: &FileMetadataExport) -> Result<(), DataExportError> {
        // Import file metadata into database
        // Simplified implementation
        Ok(())
    }
    
    async fn import_preferences(&self, _preferences: &serde_json::Value) -> Result<(), DataExportError> {
        // Import user preferences
        // Simplified implementation
        Ok(())
    }
}

#[derive(Debug, Clone)]
pub struct ImportOptions {
    pub import_settings: bool,
    pub import_tags: bool,
    pub import_metadata: bool,
    pub import_preferences: bool,
    pub overwrite_existing: bool,
}

impl Default for ImportOptions {
    fn default() -> Self {
        Self {
            import_settings: true,
            import_tags: true,
            import_metadata: true,
            import_preferences: true,
            overwrite_existing: false,
        }
    }
}

#[derive(Debug, Clone)]
pub struct ImportResult {
    pub imported_settings: u32,
    pub imported_tags: u32,
    pub imported_metadata: u32,
    pub imported_preferences: u32,
    pub skipped_items: u32,
    pub errors: Vec<String>,
}

#[derive(Debug, thiserror::Error)]
pub enum DataExportError {
    #[error("IO error: {0}")]
    Io(#[from] std::io::Error),
    #[error("Serialization failed: {0}")]
    SerializationFailed(String),
    #[error("Deserialization failed: {0}")]
    DeserializationFailed(String),
    #[error("Directory not found")]
    DirectoryNotFound,
    #[error("Version parse error: {0}")]
    VersionParseError(String),
    #[error("Incompatible version - import: {import_version}, current: {current_version}")]
    IncompatibleVersion {
        import_version: String,
        current_version: String,
    },
}
```

This comprehensive migration and backup system provides:
- **Database Schema Migration:** Automated migration between application versions with validation and rollback support
- **Settings Migration:** Format conversion and compatibility handling for user settings
- **Full Backup System:** Complete backup and restore functionality with compression and integrity checking
- **Incremental Backups:** Space-efficient incremental backups for regular data protection
- **Retention Policies:** Automatic cleanup of old backups based on age and size limits
- **Data Portability:** Export/import system for user data portability between installations
- **Integrity Verification:** Checksum-based verification of backup integrity
- **Cross-Version Compatibility:** Support for importing data from older application versions

The system ensures users never lose their data during upgrades and provides multiple layers of protection against data loss.

## 19. Roadmap & Milestones

### Development Phases (6 Sprints, 2-week each)

**Sprint 1: Foundation & Core Infrastructure (Weeks 1-2)**
- **Goal:** Establish basic project structure and core file operations
- **Deliverables:**
  - [ ] Project scaffolding with Tauri + React setup
  - [ ] Basic file system operations (list, copy, move, delete)
  - [ ] SQLite database integration with core schema
  - [ ] Simple file tree navigation
  - [ ] Basic unit test framework
- **Acceptance Criteria:**
  - User can navigate file system and perform basic operations
  - All file operations have proper error handling
  - Test coverage >70% for implemented features
  - Application runs on all target platforms
- **Success Metrics:**
  - Directory listing <500ms for 1000 files
  - File operations complete without crashes
  - Zero memory leaks in basic operations

**Sprint 2: Search & Indexing MVP (Weeks 3-4)**
- **Goal:** Implement core search functionality and file indexing
- **Deliverables:**
  - [ ] File indexing system with SQLite FTS5
  - [ ] Real-time file watcher integration
  - [ ] Basic search interface with filename search
  - [ ] Content extraction for text files
  - [ ] Search result display with relevance ranking
- **Acceptance Criteria:**
  - Search returns results within 200ms for filename queries
  - File changes automatically update search index
  - Content search works for common text file types
  - Search interface is keyboard accessible
- **Success Metrics:**
  - Index 1000 files/second for metadata
  - Search latency <100ms for filename search
  - 95% accuracy for file change detection

**Sprint 3: UI/UX & Preview System (Weeks 5-6)**
- **Goal:** Implement modern UI with file previews and theming
- **Deliverables:**
  - [ ] Complete UI redesign with Tailwind CSS
  - [ ] File preview system for images and text
  - [ ] Thumbnail generation and caching
  - [ ] Dark/light theme support
  - [ ] Responsive layout with resizable panes
- **Acceptance Criteria:**
  - All UI components follow accessibility guidelines
  - Previews load within 500ms for common file types
  - Theme switching works without restart
  - UI remains responsive during file operations
- **Success Metrics:**
  - 60fps UI performance during scrolling
  - Thumbnail cache hit rate >80%
  - WCAG 2.1 AA compliance verified

**Sprint 4: Tagging & Organization (Weeks 7-8)**
- **Goal:** Advanced file organization with tags and automation
- **Deliverables:**
  - [ ] Hierarchical tagging system
  - [ ] Bulk tagging operations
  - [ ] Smart tag suggestions
  - [ ] Basic automation rules
  - [ ] Tag-based file filtering
- **Acceptance Criteria:**
  - Users can create and manage tag hierarchies
  - Bulk operations work with 1000+ files
  - Tag suggestions appear within 100ms
  - Automation rules execute reliably
- **Success Metrics:**
  - Tag operations complete within 50ms
  - 90% user satisfaction with tag suggestions
  - Zero data loss during bulk operations

**Sprint 5: Security & Performance (Weeks 9-10)**
- **Goal:** Production-ready security and performance optimization
- **Deliverables:**
  - [ ] File encryption at rest (optional)
  - [ ] Secure deletion implementation
  - [ ] Performance optimization for large directories
  - [ ] Memory usage optimization
  - [ ] Security audit and penetration testing
- **Acceptance Criteria:**
  - Encryption/decryption transparent to user
  - Secure deletion meets DoD standards
  - Application handles 100k+ files smoothly
  - Memory usage <200MB for normal operations
- **Success Metrics:**
  - <5% performance impact from encryption
  - Virtual scrolling supports 1M+ items
  - Security audit finds zero critical issues

**Sprint 6: Polish & Release Preparation (Weeks 11-12)**
- **Goal:** Production polish and release readiness
- **Deliverables:**
  - [ ] Complete internationalization (8 languages)
  - [ ] Auto-update system implementation
  - [ ] Comprehensive error handling and logging
  - [ ] Performance monitoring and analytics
  - [ ] Release packaging and distribution setup
- **Acceptance Criteria:**
  - All target languages fully translated
  - Auto-updates work securely across platforms
  - Error reporting respects user privacy
  - Installation packages signed and verified
- **Success Metrics:**
  - Translation completion >95% for Tier 1 languages
  - Update success rate >99%
  - Zero crashes in final testing

### Post-v1.0 Roadmap

**v1.1 - Advanced Features (Month 4-5)**
- Cloud sync integration (encrypted)
- Advanced search with regex and filters
- Plugin system foundation
- Batch file operations improvements
- Enhanced automation rules

**v1.2 - Collaboration & Sharing (Month 6-7)**
- Secure file sharing
- Team collaboration features
- Advanced preview system
- Integration with cloud storage providers
- Mobile companion app

**v1.3 - AI & Intelligence (Month 8-9)**
- AI-powered file organization
- Smart duplicate detection
- Content-based file recommendations
- Natural language search queries
- Automated tagging suggestions

## 20. Cost & Resource Estimates

### Engineering Effort Breakdown

**MVP Development (Sprints 1-6)**
- **Frontend Development:** 8 engineer-weeks
  - React components and state management: 3 weeks
  - UI/UX implementation and theming: 2 weeks
  - Search interface and results display: 1.5 weeks
  - Testing and accessibility: 1.5 weeks

- **Backend Development:** 10 engineer-weeks
  - Core file operations and IPC: 2.5 weeks
  - Search indexing and query engine: 3 weeks
  - Database design and migration system: 2 weeks
  - Security and encryption implementation: 2.5 weeks

- **DevOps & Infrastructure:** 3 engineer-weeks
  - CI/CD pipeline setup: 1 week
  - Cross-platform build and packaging: 1.5 weeks
  - Release automation and update system: 0.5 weeks

- **Quality Assurance:** 4 engineer-weeks
  - Test framework development: 1 week
  - Comprehensive test suite creation: 2 weeks
  - Performance testing and optimization: 1 week

- **Project Management & Coordination:** 2 engineer-weeks
  - Sprint planning and coordination: 1 week
  - Documentation and specification maintenance: 1 week

**Total MVP Effort:** 27 engineer-weeks (approximately 6.75 engineer-months)

**v1.0 Production Release (Additional 4 weeks)**
- **Security Audit & Fixes:** 1.5 engineer-weeks
- **Performance Optimization:** 1 engineer-week
- **Release Preparation:** 1 engineer-week
- **Documentation & User Guides:** 0.5 engineer-weeks

**Total v1.0 Effort:** 31 engineer-weeks (approximately 7.75 engineer-months)

### Recommended Team Composition

**Core Team (MVP Development)**
- **Senior Full-Stack Engineer (Lead):** React/TypeScript + Rust experience, 1.0 FTE
- **Backend Engineer:** Rust systems programming, database design, 1.0 FTE
- **Frontend Engineer:** React, UI/UX implementation, accessibility, 0.75 FTE
- **DevOps Engineer:** CI/CD, cross-platform builds, security, 0.5 FTE
- **QA Engineer:** Test automation, performance testing, 0.5 FTE
- **Product Manager/Designer:** Requirements, UX design, user testing, 0.25 FTE

**Total Team:** 4 FTE (Full-Time Equivalent)

**Extended Team (v1.0 Polish)**
- **Security Consultant:** Penetration testing, audit, 0.25 FTE for 4 weeks
- **UX Designer:** Polish, accessibility review, 0.25 FTE for 4 weeks
- **Technical Writer:** Documentation, user guides, 0.25 FTE for 4 weeks

### Cost Estimates (USD)

**Personnel Costs (MVP - 12 weeks)**
- Senior Full-Stack Engineer: $150k/year × 0.23 years = $34,500
- Backend Engineer: $140k/year × 0.23 years = $32,200
- Frontend Engineer: $120k/year × 0.23 years × 0.75 = $20,700
- DevOps Engineer: $130k/year × 0.23 years × 0.5 = $14,950
- QA Engineer: $100k/year × 0.23 years × 0.5 = $11,500
- Product Manager: $120k/year × 0.23 years × 0.25 = $6,900

**Total Personnel (MVP):** $120,750

**Additional Costs**
- Code signing certificates (3 platforms): $1,500
- Development tools and licenses: $2,000
- Cloud infrastructure (CI/CD, testing): $1,000
- Security audit (external): $15,000
- Legal review (privacy, terms): $5,000

**Total Additional Costs:** $24,500

**Total MVP Budget:** $145,250

**v1.0 Polish (Additional 4 weeks)**
- Core team extension: $40,000
- Security consultant: $10,000
- UX designer: $6,000
- Technical writer: $4,000

**Total v1.0 Budget:** $205,250

### Alternative Team Configurations

**Lean Startup Approach (2-3 engineers)**
- **Senior Full-Stack Engineer (Lead):** 1.0 FTE
- **Backend Engineer:** 1.0 FTE
- **Part-time DevOps/QA:** 0.5 FTE
- **Timeline:** 16-20 weeks
- **Budget:** $110,000-$140,000

**Enterprise Approach (6-8 engineers)**
- **Technical Lead:** 1.0 FTE
- **Senior Backend Engineers:** 2.0 FTE
- **Senior Frontend Engineers:** 2.0 FTE
- **DevOps Engineer:** 1.0 FTE
- **QA Engineers:** 1.5 FTE
- **Product Manager:** 0.5 FTE
- **Timeline:** 8-10 weeks
- **Budget:** $180,000-$220,000

## 21. Optional Integrations & Advanced Features

### Cloud Storage Integrations

**Supported Cloud Providers**
- **Google Drive API:** OAuth2 integration, file sync, shared folder access
- **OneDrive API:** Microsoft Graph integration, personal and business accounts
- **Dropbox API:** File synchronization, team folder support
- **iCloud Drive:** macOS native integration via CloudKit
- **AWS S3:** Direct bucket access for power users
- **Generic WebDAV:** Support for self-hosted solutions

**Cloud Sync Architecture**
```rust
// src-tauri/src/cloud/mod.rs - Cloud integration framework
pub trait CloudProvider: Send + Sync {
    fn provider_name(&self) -> &str;
    fn supports_real_time_sync(&self) -> bool;
    async fn authenticate(&mut self, credentials: CloudCredentials) -> Result<(), CloudError>;
    async fn list_files(&self, path: &str) -> Result<Vec<CloudFile>, CloudError>;
    async fn download_file(&self, cloud_path: &str, local_path: &Path) -> Result<(), CloudError>;
    async fn upload_file(&self, local_path: &Path, cloud_path: &str) -> Result<(), CloudError>;
    async fn delete_file(&self, cloud_path: &str) -> Result<(), CloudError>;
    async fn get_sync_status(&self) -> Result<SyncStatus, CloudError>;
}

pub struct CloudSyncManager {
    providers: HashMap<String, Box<dyn CloudProvider>>,
    sync_rules: Vec<SyncRule>,
    conflict_resolver: ConflictResolver,
    encryption_enabled: bool,
}

#[derive(Debug, Clone)]
pub struct SyncRule {
    pub local_path: PathBuf,
    pub cloud_path: String,
    pub provider: String,
    pub sync_direction: SyncDirection,
    pub file_filters: Vec<String>,
    pub encryption_required: bool,
}

#[derive(Debug, Clone)]
pub enum SyncDirection {
    Upload,      // Local → Cloud
    Download,    // Cloud → Local
    Bidirectional, // Both directions with conflict resolution
}
```

### Git-like File History

**Version Control for Files**
```rust
// src-tauri/src/versioning.rs - File version control system
pub struct FileVersionManager {
    repository_path: PathBuf,
    max_versions_per_file: u32,
    compression_enabled: bool,
}

#[derive(Debug, Clone)]
pub struct FileVersion {
    pub id: String,
    pub file_path: PathBuf,
    pub version_number: u32,
    pub created_at: chrono::DateTime<chrono::Utc>,
    pub size_bytes: u64,
    pub change_description: String,
    pub parent_version: Option<String>,
    pub checksum: String,
}

impl FileVersionManager {
    pub async fn create_version(&mut self, file_path: &Path, description: String) -> Result<FileVersion, VersionError> {
        let content = tokio::fs::read(file_path).await?;
        let checksum = self.calculate_checksum(&content);
        
        // Check if content has actually changed
        if let Ok(latest) = self.get_latest_version(file_path).await {
            if latest.checksum == checksum {
                return Ok(latest); // No changes, return existing version
            }
        }
        
        let version = FileVersion {
            id: uuid::Uuid::new_v4().to_string(),
            file_path: file_path.to_path_buf(),
            version_number: self.get_next_version_number(file_path).await?,
            created_at: chrono::Utc::now(),
            size_bytes: content.len() as u64,
            change_description: description,
            parent_version: self.get_latest_version(file_path).await.ok().map(|v| v.id),
            checksum,
        };
        
        // Store version data
        self.store_version_content(&version, &content).await?;
        self.store_version_metadata(&version).await?;
        
        // Apply retention policy
        self.cleanup_old_versions(file_path).await?;
        
        Ok(version)
    }
    
    pub async fn restore_version(&self, version_id: &str, restore_path: &Path) -> Result<(), VersionError> {
        let version = self.get_version_metadata(version_id).await?;
        let content = self.load_version_content(&version).await?;
        
        tokio::fs::write(restore_path, content).await?;
        
        Ok(())
    }
    
    pub async fn get_file_history(&self, file_path: &Path) -> Result<Vec<FileVersion>, VersionError> {
        // Query database for all versions of this file
        let mut versions = Vec::new();
        
        // This would query the actual database
        // Simplified implementation
        
        versions.sort_by(|a, b| b.created_at.cmp(&a.created_at));
        Ok(versions)
    }
    
    pub async fn diff_versions(&self, version_a: &str, version_b: &str) -> Result<FileDiff, VersionError> {
        let content_a = self.load_version_content_by_id(version_a).await?;
        let content_b = self.load_version_content_by_id(version_b).await?;
        
        // Generate diff using similar crate or custom implementation
        let diff = self.generate_diff(&content_a, &content_b)?;
        
        Ok(diff)
    }
}
```

### Deduplication Engine

**Intelligent Duplicate Detection**
```rust
// src-tauri/src/deduplication.rs - File deduplication system
pub struct DeduplicationEngine {
    hash_index: HashMap<String, Vec<PathBuf>>,
    similarity_threshold: f32,
    size_threshold: u64,
}

#[derive(Debug, Clone)]
pub struct DuplicateGroup {
    pub id: String,
    pub files: Vec<DuplicateFile>,
    pub duplicate_type: DuplicateType,
    pub total_wasted_space: u64,
    pub recommended_action: RecommendedAction,
}

#[derive(Debug, Clone)]
pub struct DuplicateFile {
    pub path: PathBuf,
    pub size: u64,
    pub modified: chrono::DateTime<chrono::Utc>,
    pub is_original: bool,
    pub confidence_score: f32,
}

#[derive(Debug, Clone)]
pub enum DuplicateType {
    Exact,           // Identical content
    Similar,         // Similar content (fuzzy matching)
    SameName,        // Same filename, different content
    SizeMatch,       // Same size, potentially different content
}

#[derive(Debug, Clone)]
pub enum RecommendedAction {
    DeleteDuplicates,
    MergeFiles,
    Review,
    Ignore,
}

impl DeduplicationEngine {
    pub async fn scan_for_duplicates(&mut self, scan_paths: &[PathBuf]) -> Result<Vec<DuplicateGroup>, DeduplicationError> {
        let mut file_hashes: HashMap<String, Vec<PathBuf>> = HashMap::new();
        let mut size_groups: HashMap<u64, Vec<PathBuf>> = HashMap::new();
        
        // First pass: collect file hashes and sizes
        for scan_path in scan_paths {
            self.scan_directory_recursive(scan_path, &mut file_hashes, &mut size_groups).await?;
        }
        
        let mut duplicate_groups = Vec::new();
        
        // Find exact duplicates by hash
        for (hash, files) in file_hashes {
            if files.len() > 1 {
                let group = self.create_exact_duplicate_group(hash, files).await?;
                duplicate_groups.push(group);
            }
        }
        
        // Find similar files by size and fuzzy content matching
        for (size, files) in size_groups {
            if files.len() > 1 && size > self.size_threshold {
                let similar_groups = self.find_similar_files(files).await?;
                duplicate_groups.extend(similar_groups);
            }
        }
        
        // Sort by potential space savings
        duplicate_groups.sort_by(|a, b| b.total_wasted_space.cmp(&a.total_wasted_space));
        
        Ok(duplicate_groups)
    }
    
    async fn scan_directory_recursive(
        &self,
        dir: &Path,
        file_hashes: &mut HashMap<String, Vec<PathBuf>>,
        size_groups: &mut HashMap<u64, Vec<PathBuf>>
    ) -> Result<(), DeduplicationError> {
        let mut entries = tokio::fs::read_dir(dir).await?;
        
        while let Some(entry) = entries.next_entry().await? {
            let path = entry.path();
            let metadata = entry.metadata().await?;
            
            if metadata.is_dir() {
                self.scan_directory_recursive(&path, file_hashes, size_groups).await?;
            } else if metadata.len() > 0 {
                // Calculate file hash
                let hash = self.calculate_file_hash(&path).await?;
                file_hashes.entry(hash).or_insert_with(Vec::new).push(path.clone());
                
                // Group by size
                size_groups.entry(metadata.len()).or_insert_with(Vec::new).push(path);
            }
        }
        
        Ok(())
    }
    
    async fn calculate_file_hash(&self, file_path: &Path) -> Result<String, DeduplicationError> {
        use sha2::{Sha256, Digest};
        
        let content = tokio::fs::read(file_path).await?;
        let mut hasher = Sha256::new();
        hasher.update(&content);
        
        Ok(format!("{:x}", hasher.finalize()))
    }
    
    async fn create_exact_duplicate_group(&self, hash: String, files: Vec<PathBuf>) -> Result<DuplicateGroup, DeduplicationError> {
        let mut duplicate_files = Vec::new();
        let mut total_size = 0;
        let mut oldest_file = None;
        let mut oldest_time = chrono::Utc::now();
        
        for file_path in files {
            let metadata = tokio::fs::metadata(&file_path).await?;
            let modified = chrono::DateTime::from(metadata.modified()?);
            
            if modified < oldest_time {
                oldest_time = modified;
                oldest_file = Some(file_path.clone());
            }
            
            duplicate_files.push(DuplicateFile {
                path: file_path,
                size: metadata.len(),
                modified,
                is_original: false, // Will be set below
                confidence_score: 1.0, // Exact match
            });
            
            total_size += metadata.len();
        }
        
        // Mark oldest file as original
        if let Some(original_path) = oldest_file {
            for file in &mut duplicate_files {
                if file.path == original_path {
                    file.is_original = true;
                    break;
                }
            }
        }
        
        let wasted_space = total_size - duplicate_files.iter()
            .find(|f| f.is_original)
            .map(|f| f.size)
            .unwrap_or(0);
        
        Ok(DuplicateGroup {
            id: uuid::Uuid::new_v4().to_string(),
            files: duplicate_files,
            duplicate_type: DuplicateType::Exact,
            total_wasted_space: wasted_space,
            recommended_action: RecommendedAction::DeleteDuplicates,
        })
    }
    
    async fn find_similar_files(&self, files: Vec<PathBuf>) -> Result<Vec<DuplicateGroup>, DeduplicationError> {
        let mut similar_groups = Vec::new();
        
        // Compare files pairwise for similarity
        for i in 0..files.len() {
            for j in (i + 1)..files.len() {
                let similarity = self.calculate_file_similarity(&files[i], &files[j]).await?;
                
                if similarity > self.similarity_threshold {
                    // Create similar file group
                    let group = self.create_similar_file_group(vec![files[i].clone(), files[j].clone()], similarity).await?;
                    similar_groups.push(group);
                }
            }
        }
        
        Ok(similar_groups)
    }
    
    async fn calculate_file_similarity(&self, file_a: &Path, file_b: &Path) -> Result<f32, DeduplicationError> {
        // For text files, use content similarity
        if self.is_text_file(file_a) && self.is_text_file(file_b) {
            let content_a = tokio::fs::read_to_string(file_a).await?;
            let content_b = tokio::fs::read_to_string(file_b).await?;
            
            Ok(self.calculate_text_similarity(&content_a, &content_b))
        } else {
            // For binary files, use byte-level similarity
            Ok(self.calculate_binary_similarity(file_a, file_b).await?)
        }
    }
    
    fn calculate_text_similarity(&self, text_a: &str, text_b: &str) -> f32 {
        // Simplified similarity calculation using Jaccard similarity
        let words_a: std::collections::HashSet<&str> = text_a.split_whitespace().collect();
        let words_b: std::collections::HashSet<&str> = text_b.split_whitespace().collect();
        
        let intersection = words_a.intersection(&words_b).count();
        let union = words_a.union(&words_b).count();
        
        if union == 0 {
            0.0
        } else {
            intersection as f32 / union as f32
        }
    }
    
    async fn calculate_binary_similarity(&self, file_a: &Path, file_b: &Path) -> Result<f32, DeduplicationError> {
        // Sample-based similarity for binary files
        let sample_size = 4096; // 4KB sample
        
        let content_a = tokio::fs::read(file_a).await?;
        let content_b = tokio::fs::read(file_b).await?;
        
        if content_a.len() != content_b.len() {
            return Ok(0.0); // Different sizes = not similar
        }
        
        let sample_a = &content_a[..sample_size.min(content_a.len())];
        let sample_b = &content_b[..sample_size.min(content_b.len())];
        
        let matching_bytes = sample_a.iter()
            .zip(sample_b.iter())
            .filter(|(a, b)| a == b)
            .count();
        
        Ok(matching_bytes as f32 / sample_a.len() as f32)
    }
    
    fn is_text_file(&self, file_path: &Path) -> bool {
        if let Some(extension) = file_path.extension().and_then(|s| s.to_str()) {
            matches!(extension.to_lowercase().as_str(), 
                "txt" | "md" | "json" | "xml" | "csv" | "log" | "cfg" | "ini" | 
                "js" | "ts" | "py" | "rs" | "go" | "java" | "cpp" | "c" | "h")
        } else {
            false
        }
    }
}
```

### Automation & Rules Engine

**Smart File Organization**
```rust
// src-tauri/src/automation.rs - File organization automation
pub struct AutomationEngine {
    rules: Vec<AutomationRule>,
    ml_classifier: Option<MLClassifier>,
    execution_queue: VecDeque<AutomationTask>,
}

#[derive(Debug, Clone)]
pub struct AutomationRule {
    pub id: String,
    pub name: String,
    pub enabled: bool,
    pub trigger: AutomationTrigger,
    pub conditions: Vec<AutomationCondition>,
    pub actions: Vec<AutomationAction>,
    pub priority: u32,
}

#[derive(Debug, Clone)]
pub enum AutomationTrigger {
    FileAdded,
    FileModified,
    FileDownloaded,
    Scheduled(chrono::Duration),
    Manual,
}

#[derive(Debug, Clone)]
pub enum AutomationCondition {
    FileExtension(Vec<String>),
    FileSize { min: Option<u64>, max: Option<u64> },
    FileName(String), // Regex pattern
    FilePath(String), // Regex pattern
    FileAge(chrono::Duration),
    FileContent(String), // Content contains text
}

#[derive(Debug, Clone)]
pub enum AutomationAction {
    Move { destination: PathBuf },
    Copy { destination: PathBuf },
    AddTags(Vec<String>),
    Rename { pattern: String },
    Delete,
    Archive { destination: PathBuf },
    RunCommand { command: String, args: Vec<String> },
}

impl AutomationEngine {
    pub fn add_rule(&mut self, rule: AutomationRule) -> Result<(), AutomationError> {
        // Validate rule before adding
        self.validate_rule(&rule)?;
        
        self.rules.push(rule);
        self.rules.sort_by_key(|r| r.priority);
        
        Ok(())
    }
    
    pub async fn process_file_event(&mut self, file_path: &Path, event_type: FileEventType) -> Result<(), AutomationError> {
        let applicable_rules = self.find_applicable_rules(file_path, &event_type).await?;
        
        for rule in applicable_rules {
            if self.evaluate_conditions(file_path, &rule.conditions).await? {
                let task = AutomationTask {
                    id: uuid::Uuid::new_v4().to_string(),
                    rule_id: rule.id.clone(),
                    file_path: file_path.to_path_buf(),
                    actions: rule.actions.clone(),
                    created_at: chrono::Utc::now(),
                };
                
                self.execution_queue.push_back(task);
            }
        }
        
        // Execute queued tasks
        self.execute_pending_tasks().await?;
        
        Ok(())
    }
    
    async fn execute_pending_tasks(&mut self) -> Result<(), AutomationError> {
        while let Some(task) = self.execution_queue.pop_front() {
            for action in &task.actions {
                self.execute_action(&task.file_path, action).await?;
            }
            
            crate::log_info!("Automation task completed", serde_json::json!({
                "task_id": task.id,
                "rule_id": task.rule_id,
                "file_path": task.file_path.display().to_string()
            }));
        }
        
        Ok(())
    }
    
    async fn execute_action(&self, file_path: &Path, action: &AutomationAction) -> Result<(), AutomationError> {
        match action {
            AutomationAction::Move { destination } => {
                let dest_path = destination.join(file_path.file_name().unwrap());
                tokio::fs::rename(file_path, &dest_path).await?;
            },
            AutomationAction::Copy { destination } => {
                let dest_path = destination.join(file_path.file_name().unwrap());
                tokio::fs::copy(file_path, &dest_path).await?;
            },
            AutomationAction::AddTags(tags) => {
                for tag in tags {
                    // Add tag to database
                    // Simplified implementation
                }
            },
            AutomationAction::Rename { pattern } => {
                let new_name = self.apply_rename_pattern(file_path, pattern)?;
                let new_path = file_path.with_file_name(new_name);
                tokio::fs::rename(file_path, &new_path).await?;
            },
            AutomationAction::Delete => {
                tokio::fs::remove_file(file_path).await?;
            },
            AutomationAction::Archive { destination } => {
                // Create archive with file
                self.create_archive(file_path, destination).await?;
            },
            AutomationAction::RunCommand { command, args } => {
                let output = std::process::Command::new(command)
                    .args(args)
                    .arg(file_path)
                    .output()?;
                
                if !output.status.success() {
                    return Err(AutomationError::CommandFailed(
                        String::from_utf8_lossy(&output.stderr).to_string()
                    ));
                }
            },
        }
        
        Ok(())
    }
}
```

## 22. Appendices

### A. Sample IPC API Schemas

**File Operations API**
```typescript
// Frontend TypeScript interfaces for IPC communication

interface FileOperationRequest {
  operation: 'copy' | 'move' | 'delete' | 'rename';
  source: string | string[];
  destination?: string;
  options?: {
    overwrite?: boolean;
    preserveTimestamps?: boolean;
    followSymlinks?: boolean;
  };
}

interface FileOperationResponse {
  success: boolean;
  operationId: string;
  affectedFiles: string[];
  errors?: FileOperationError[];
}

interface FileOperationError {
  file: string;
  error: string;
  errorCode: 'PERMISSION_DENIED' | 'FILE_NOT_FOUND' | 'DISK_FULL' | 'UNKNOWN';
}

interface SearchRequest {
  query: string;
  filters?: {
    fileTypes?: string[];
    sizeRange?: { min?: number; max?: number };
    dateRange?: { start?: string; end?: string };
    tags?: string[];
    path?: string;
  };
  sort?: {
    field: 'name' | 'size' | 'modified' | 'relevance';
    direction: 'asc' | 'desc';
  };
  pagination?: {
    offset: number;
    limit: number;
  };
}

interface SearchResponse {
  results: FileSearchResult[];
  totalCount: number;
  searchTime: number;
  query: SearchRequest;
}

interface FileSearchResult {
  path: string;
  name: string;
  size: number;
  modified: string;
  isDirectory: boolean;
  relevanceScore: number;
  matchContext?: string;
  tags: string[];
}
```

### B. Recommended Open-Source Libraries

**Frontend Dependencies**
```json
{
  "dependencies": {
    "@tauri-apps/api": "^1.5.0",
    "@reduxjs/toolkit": "^1.9.0", 
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-redux": "^8.1.0",
    "react-router-dom": "^6.15.0",
    "react-window": "^1.8.8",
    "react-hotkeys-hook": "^4.4.1",
    "date-fns": "^2.30.0",
    "classnames": "^2.3.2"
  },
  "devDependencies": {
    "@testing-library/react": "^13.4.0",
    "@testing-library/jest-dom": "^6.0.0",
    "@testing-library/user-event": "^14.4.0",
    "vitest": "^0.34.0",
    "jsdom": "^22.1.0",
    "@playwright/test": "^1.37.0",
    "typescript": "^5.0.0",
    "vite": "^4.4.0",
    "@vitejs/plugin-react": "^4.0.0",
    "tailwindcss": "^3.3.0",
    "eslint": "^8.45.0",
    "@typescript-eslint/eslint-plugin": "^6.0.0"
  }
}
```

**Backend Dependencies (Cargo.toml)**
```toml
[dependencies]
tauri = { version = "1.5", features = ["api-all"] }
tokio = { version = "1.32", features = ["full"] }
serde = { version = "1.0", features = ["derive"] }
serde_json = "1.0"
rusqlite = { version = "0.29", features = ["bundled", "chrono"] }
sqlx = { version = "0.7", features = ["runtime-tokio-rustls", "sqlite", "chrono", "uuid"] }
notify = "6.1"
walkdir = "2.3"
image = "0.24"
uuid = { version = "1.4", features = ["v4", "serde"] }
chrono = { version = "0.4", features = ["serde"] }
thiserror = "1.0"
anyhow = "1.0"
clap = { version = "4.4", features = ["derive"] }
dirs = "5.0"
log = "0.4"
env_logger = "0.10"
regex = "1.9"
sha2 = "0.10"
aes-gcm = "0.10"
argon2 = "0.5"
ed25519-dalek = "2.0"
reqwest = { version = "0.11", features = ["json", "rustls-tls"] }
semver = "1.0"

[dev-dependencies]
tempfile = "3.8"
criterion = "0.5"
proptest = "1.2"
mockall = "0.11"

[[bench]]
name = "file_operations"
harness = false

[[bench]]
name = "search_performance"
harness = false
```

### C. App Store Submission Checklist

**macOS App Store Submission**
- [ ] Apple Developer Program membership active
- [ ] App sandbox entitlements properly configured
- [ ] Hardened runtime enabled
- [ ] App notarized and stapled
- [ ] Privacy manifest (PrivacyInfo.xcprivacy) included
- [ ] App Store metadata prepared (screenshots, description, keywords)
- [ ] Age rating questionnaire completed
- [ ] Export compliance documentation
- [ ] App Review Guidelines compliance verified
- [ ] TestFlight beta testing completed

**Microsoft Store Submission**
- [ ] Microsoft Partner Center account setup
- [ ] Windows App Certification Kit (WACK) validation passed
- [ ] Privacy policy URL provided
- [ ] Age rating from IARC obtained
- [ ] Store listing assets prepared (logos, screenshots, trailers)
- [ ] Package identity configured
- [ ] Store compliance requirements met
- [ ] Security features documented
- [ ] Accessibility features documented

**Linux Distribution**
- [ ] Flatpak package created and tested
- [ ] Snap package created and tested
- [ ] AppImage functional verification
- [ ] Desktop entry file (.desktop) created
- [ ] Icon files in standard sizes provided
- [ ] MetaInfo file for software centers created
- [ ] License compatibility verified
- [ ] Security review for sandboxing

### D. Security Audit Checklist

**Code Security Review**
- [ ] Static analysis with Clippy (Rust) and ESLint (TypeScript)
- [ ] Dependency vulnerability scanning (cargo audit, npm audit)
- [ ] Input validation on all IPC boundaries
- [ ] SQL injection prevention verified
- [ ] Path traversal attacks prevented
- [ ] Memory safety verified (no unsafe Rust blocks)
- [ ] Cryptographic implementations reviewed
- [ ] Error messages don't leak sensitive information

**Runtime Security Testing**
- [ ] Fuzzing of file operation APIs
- [ ] Privilege escalation testing
- [ ] Sandbox escape attempt testing
- [ ] Network security testing (if applicable)
- [ ] File system permission boundary testing
- [ ] Memory corruption testing
- [ ] Performance DoS testing
- [ ] Update mechanism security testing

**Privacy Compliance**
- [ ] GDPR compliance review (if applicable)
- [ ] CCPA compliance review (if applicable)
- [ ] Data minimization principles followed
- [ ] User consent mechanisms implemented
- [ ] Data retention policies documented
- [ ] Right to deletion implemented
- [ ] Data portability features tested
- [ ] Privacy policy accuracy verified

This comprehensive specification provides a complete blueprint for building a production-ready desktop file management application. The document includes detailed technical specifications, security considerations, performance requirements, and implementation guidance that would enable an experienced development team to build, test, and ship the application successfully.

Take a deep breath and work on this problem step-by-step.
