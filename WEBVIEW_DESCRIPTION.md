# MÔ TẢ GIAO DIỆN PHẦN WEBVIEW

## VỊ TRÍ
Phần webview nằm giữa:
- **Phía trên**: Navigation link "GAMES" trong header
- **Phía dưới**: Footer (bottom navigation bar)

---

## CẤU TRÚC GIAO DIỆN

### 1. SEARCH BAR & FILTERS SECTION
**Vị trí**: Sticky ở đầu phần webview (sticky top: 88px)

#### 1.1 Search Bar
- **Container**: `.sticky-search` với background `var(--retro-bg-medium)`
- **Border**: 3px solid `var(--neon-magenta)` ở phía dưới
- **Box shadow**: Neon magenta glow effect
- **Padding**: 20px 0

**Search Input**:
- **ID**: `search-input`
- **Placeholder**: "SEARCH GAMES..."
- **Styling**:
  - Font: 'Press Start 2P', monospace
  - Font size: 10px
  - Background: `var(--retro-bg-dark)`
  - Border: 3px solid `var(--neon-cyan)`
  - Color: `var(--neon-cyan)`
  - Text align: center (khi không focus), left (khi focus)
  - Box shadow: Inset shadow + cyan glow
  - Max width: 500px
  - Padding: 15px 20px
- **Focus state**: 
  - Border color: `var(--neon-yellow)`
  - Color: `var(--neon-yellow)`
  - Box shadow: Yellow glow effect

**Toggle View Button**:
- **ID**: `toggle-view-btn`
- **Type**: Button
- **Icons**: 
  - Grid icon (SVG): 4 squares (2x2 grid)
  - List icon (SVG): 3 horizontal bars
- **Styling**:
  - Background: `var(--retro-bg-light)`
  - Border: 3px solid `var(--neon-yellow)`
  - Color: `var(--neon-yellow)`
  - Font: 'Press Start 2P', monospace
  - Font size: 10px
  - Padding: 15px 20px
  - Box shadow: 0 4px 0 `var(--neon-purple)`
- **Hover state**: 
  - Background: `var(--neon-yellow)`
  - Color: `var(--retro-bg-dark)`
  - Transform: translateY(2px)

#### 1.2 Filters
**Container**: `.filter-inline` trong `.search-bar-row`

**Platform Filter**:
- **ID**: `platform-filter`
- **Label**: "Platform"
- **Options**: 
  - "All" (default)
  - Dynamic options từ game data

**Region Filter**:
- **ID**: `region-filter`
- **Label**: "Region" (margin-left: 18px)
- **Options**:
  - "All" (default)
  - Dynamic options từ game data

**Filter Styling**:
- Select elements có styling từ form controls
- Background: `var(--retro-bg-dark)`
- Border: 3px solid `var(--neon-cyan)`
- Color: `var(--neon-cyan)`

---

### 2. GAMES GRID SECTION
**Container**: `.container` > `.grid#game-list`

#### 2.1 Grid Layout
- **Display**: CSS Grid
- **Grid template columns**: `repeat(auto-fill, minmax(250px, 1fr))`
- **Gap**: 30px
- **Margin top**: 30px
- **Responsive**:
  - Mobile (≤768px): `minmax(180px, 1fr)`, gap: 20px
  - Small mobile (≤480px): `repeat(2, 1fr)`, gap: 15px

#### 2.2 Game Card (`.game`)
**Structure**:
```
<div class="game">
  <div class="game-image-container">
    <img src="[thumbnail]" alt="[title]">
    [Popular Badge - optional]
  </div>
  <div class="game-info">
    <h3>[Game Title]</h3>
    <p><strong>Platform:</strong> [Platform]</p>
    <a href="[download_link]" class="download-btn" target="_blank">
      <span class="download-spinner"></span>
      <span class="download-text">Download</span>
    </a>
  </div>
</div>
```

**Card Styling**:
- **Background**: `var(--retro-bg-light)`
- **Border**: 4px solid `var(--neon-cyan)`
- **Box shadow**: 
  - 0 8px 0 `var(--neon-magenta)`
  - 0 0 20px rgba(0, 217, 255, 0.3)
- **Position**: Relative
- **Transition**: all 0.2s ease
- **Pseudo-element**: `::before` với border 2px solid `var(--retro-bg-dark)` để tạo double border effect

**Hover State**:
- **Transform**: translateY(-5px)
- **Border color**: `var(--neon-yellow)`
- **Box shadow**:
  - 0 12px 0 `var(--neon-purple)`
  - 0 0 30px rgba(255, 234, 0, 0.5)

**Game Image Container**:
- **Position**: Relative
- **Overflow**: Hidden
- **Border bottom**: 4px solid `var(--neon-magenta)`

**Game Image**:
- **Width**: 100%
- **Aspect ratio**: 1/1 (square)
- **Object fit**: Cover
- **Image rendering**: Pixelated (retro effect)
- **Filter**: contrast(1.1) saturate(1.2)

**Game Info**:
- **Padding**: 20px 15px
- **Text align**: Center

**Game Title (h3)**:
- **Font**: 'Press Start 2P', monospace
- **Font size**: 10px (desktop), 8px (tablet), 7px (mobile)
- **Color**: `var(--neon-cyan)`
- **Margin**: 0 0 15px 0
- **Line height**: 1.6
- **Min height**: 3em (desktop), 2.5em (mobile)
- **Text shadow**:
  - 2px 2px 0 rgba(0, 0, 0, 0.8)
  - 0 0 10px `var(--neon-cyan)`

**Platform Info (p)**:
- **Display**: None (ẩn trong grid view)

**Popular Badge**:
- **Class**: `.popular-badge`
- **Position**: Absolute, top: 10px, right: 10px
- **Background**: `var(--neon-yellow)`
- **Color**: `var(--retro-bg-dark)`
- **Font**: 'Press Start 2P', monospace
- **Font size**: 8px (desktop), 6px (mobile)
- **Padding**: 5px 10px (desktop), 3px 6px (mobile)
- **Border**: 3px solid `var(--retro-bg-dark)`
- **Box shadow**: 
  - 0 0 15px `var(--neon-yellow)`
  - 0 4px 0 `var(--neon-magenta)`
- **Z-index**: 10
- **Animation**: badge-blink 2s infinite (opacity 1 ↔ 0.7)
- **Text**: "🔥 Popular"

**Download Button**:
- **Class**: `.download-btn`
- **Display**: Inline-block
- **Padding**: 12px 25px (desktop), 10px 15px (tablet), 8px 12px (mobile)
- **Background**: `var(--neon-green)`
- **Color**: `var(--retro-bg-dark)`
- **Font**: 'Press Start 2P', monospace
- **Font size**: 9px (desktop), 7px (tablet), 6px (mobile)
- **Text transform**: Uppercase
- **Border**: 3px solid `var(--retro-bg-dark)`
- **Box shadow**:
  - 0 5px 0 `var(--neon-cyan)`
  - 0 0 15px rgba(57, 255, 20, 0.5)
- **Pseudo-element**: `::before` với content "▼" (download icon)
- **Hover state**:
  - Background: `var(--neon-yellow)`
  - Transform: translateY(2px)
  - Box shadow: Yellow glow
- **Active state**:
  - Transform: translateY(5px)
  - Box shadow: Reduced

**List View Mode**:
- Khi toggle sang list view, grid có class `.list-view`
- Game cards có class `.list-item`
- Layout thay đổi thành horizontal layout

---

### 3. PAGINATION SECTION
**Container**: `#pagination.pagination-bar`

#### 3.1 Pagination Bar
- **Display**: Flex
- **Justify content**: Center
- **Align items**: Center
- **Margin**: 40px 0
- **Gap**: 10px
- **Visibility**: Chỉ hiển thị khi có nhiều hơn 1 trang

#### 3.2 Pagination Buttons
**Class**: `.pagination-btn`

**Styling**:
- **Padding**: 12px 20px
- **Background**: `var(--retro-bg-light)`
- **Border**: 3px solid `var(--neon-cyan)`
- **Color**: `var(--neon-cyan)`
- **Font**: 'Press Start 2P', monospace
- **Font size**: 10px
- **Cursor**: Pointer
- **Box shadow**: 0 4px 0 `var(--neon-magenta)`
- **Transition**: all 0.2s ease

**Active State**:
- **Background**: `var(--neon-cyan)`
- **Color**: `var(--retro-bg-dark)`
- **Transform**: translateY(2px)
- **Box shadow**: 0 2px 0 `var(--neon-magenta)`

**Disabled State**:
- **Opacity**: 0.3
- **Cursor**: not-allowed

**Pagination Logic**:
- **Games per page**: 50
- **Buttons**: 
  - Previous (`&laquo;`)
  - Page numbers (1, 2, 3...)
  - Ellipsis (`...`) khi có nhiều trang
  - Next (`&raquo;`)
- **Smart pagination**: Chỉ hiển thị trang hiện tại ± 2 trang

---

## BACKGROUND EFFECTS

### CRT Screen Effect
- **Pseudo-element**: `body::before`
- **Effect**: Repeating linear gradient scanlines
- **Animation**: scanline 8s linear infinite
- **Z-index**: 9999
- **Pointer events**: None

### Pixel Grid Background
- **Pseudo-element**: `body::after`
- **Effect**: Pixel grid pattern với cyan glow
- **Background size**: 50px 50px
- **Z-index**: -1

---

## RESPONSIVE BREAKPOINTS

### Desktop (> 768px)
- Grid: `repeat(auto-fill, minmax(250px, 1fr))`
- Gap: 30px
- Game card border: 4px
- Font sizes: Full size

### Tablet (≤ 768px)
- Grid: `repeat(auto-fill, minmax(180px, 1fr))`
- Gap: 20px
- Mobile menu button hiển thị
- Font sizes: Giảm nhẹ

### Mobile (≤ 480px)
- Grid: `repeat(2, 1fr)`
- Gap: 15px
- Game card border: 3px
- Font sizes: Nhỏ nhất
- Logo tagline ẩn

---

## INTERACTIVE FEATURES

### Search Functionality
- **Real-time search**: Tìm kiếm khi gõ (oninput)
- **Search scope**: Title và Platform
- **Case insensitive**: Tất cả chuyển về lowercase

### Filter Functionality
- **Platform filter**: Lọc theo platform
- **Region filter**: Lọc theo region
- **Combined filters**: Kết hợp search + platform + region
- **Auto-reset**: Reset về trang 1 khi filter

### View Toggle
- **Grid view**: Default, hiển thị cards dạng grid
- **List view**: Horizontal layout với thông tin chi tiết hơn
- **Toggle button**: Chuyển đổi giữa 2 chế độ

### Pagination
- **Page navigation**: Click vào số trang hoặc prev/next
- **Smooth scroll**: Scroll to top khi chuyển trang
- **Current page**: Highlight trang hiện tại

### Game Card Interactions
- **Hover effect**: Lift up với glow effect
- **Touch handling**: Optimized cho mobile
- **Download button**: Ripple effect khi click
- **Loading state**: Spinner khi download

---

## COLOR SCHEME

### Primary Colors
- **Background dark**: `#0f0f1e` (`--retro-bg-dark`)
- **Background medium**: `#1a1a2e` (`--retro-bg-medium`)
- **Background light**: `#16213e` (`--retro-bg-light`)

### Neon Colors
- **Cyan**: `#00d9ff` (`--neon-cyan`) - Primary accent
- **Magenta**: `#ff0080` (`--neon-magenta`) - Secondary accent
- **Yellow**: `#ffea00` (`--neon-yellow`) - Highlight
- **Green**: `#39ff14` (`--neon-green`) - Success/Download
- **Purple**: `#b537f2` (`--neon-purple`) - Tertiary accent

### Text Colors
- **Primary**: `#f0f0f0` (`--text-primary`)
- **Glow**: `#00d9ff` (`--text-glow`)

---

## TYPOGRAPHY

### Fonts
- **Primary**: 'Press Start 2P', monospace (8-bit pixel font)
- **Secondary**: 'VT323', monospace (retro terminal font)

### Font Sizes
- **Search input**: 10px
- **Game title**: 10px (desktop), 8px (tablet), 7px (mobile)
- **Download button**: 9px (desktop), 7px (tablet), 6px (mobile)
- **Pagination**: 10px
- **Popular badge**: 8px (desktop), 6px (mobile)

---

## ANIMATIONS

### Badge Blink
- **Duration**: 2s
- **Iteration**: Infinite
- **Effect**: Opacity 1 ↔ 0.7

### Pixel Glow
- **Duration**: 3s
- **Iteration**: Infinite
- **Effect**: Brightness và text-shadow pulse

### Scanline
- **Duration**: 8s
- **Iteration**: Infinite
- **Effect**: Vertical scanline movement

### Heartbeat (Footer)
- **Duration**: 1.5s
- **Iteration**: Infinite
- **Effect**: Scale 1 ↔ 1.3

---

## DATA STRUCTURE

### Game Object
```javascript
{
  title: string,
  platform: string,
  region: string,
  thumbnail: string (URL),
  download_link: string (URL)
}
```

### Popular Games
- Danh sách 50+ games được ưu tiên hiển thị đầu tiên
- Có badge "🔥 Popular"
- Sắp xếp theo thứ tự trong POPULAR_GAMES array

---

## PERFORMANCE OPTIMIZATIONS

### Pagination
- Chỉ render 50 games mỗi trang
- Giảm DOM nodes
- Cải thiện scroll performance

### Image Loading
- Lazy loading (từ browser)
- Pixelated rendering
- Aspect ratio fixed (1:1)

### Touch Handling
- Passive event listeners
- Optimized scroll detection
- Prevent context menu on long press

---

## LOADING STATES

### Initial Load
- Loading overlay với pixel spinner
- "LOADING GAMES..." text
- Reload button nếu timeout

### Error States
- Error message với retry button
- Fallback files: games.json → gbaroms.json → sgame.json
- Network detection

### Empty States
- "No games found." message
- Styled với magenta color

---

## ACCESSIBILITY

### Keyboard Navigation
- Tab navigation cho search và filters
- Enter để submit search
- Arrow keys cho pagination (có thể implement)

### Screen Readers
- Alt text cho images
- ARIA labels cho buttons
- Semantic HTML structure

---

## BROWSER COMPATIBILITY

### CSS Features Used
- CSS Grid
- CSS Variables
- Flexbox
- Transform & Transitions
- Box-shadow
- Pseudo-elements

### JavaScript Features Used
- ES6+ (Arrow functions, const/let, template literals)
- Fetch API
- DOM APIs
- Event listeners
- MutationObserver

---

## NOTES

1. **Retro Theme**: Toàn bộ giao diện theo phong cách retro 8-bit/16-bit
2. **Pixel Perfect**: Image rendering pixelated để giữ retro aesthetic
3. **Neon Glow**: Nhiều glow effects để tạo arcade feel
4. **Mobile First**: Responsive design với breakpoints rõ ràng
5. **Performance**: Pagination và lazy loading để optimize
6. **User Experience**: Smooth transitions, hover effects, touch optimization
