---
Title: Speed Test Enhancement - Add Download Speed Chart
Created: 2026-01-11T15:10:00.000Z
Last Updated: 2026-01-11T15:10:00.000Z
Tags: tools, speed-test, enhancement
---

# Speed Test Enhancement Plan

## Goal

Add a download speed test alongside the existing latency monitor. Keep it simple - just add a second chart showing download throughput.

## Current State

- `connection-speed-tester.html` - Latency-only monitor
- Pings Google favicon every 1 second
- Shows 120-second rolling history
- Clean, minimal UI with uPlot charting

## Proposed Changes

### 1. Layout Change

**Current:** Single centered instrument panel (max-width 640px)

**New:** Two side-by-side panels
- Left: Existing latency monitor (unchanged)
- Right: New download speed monitor

```
┌─────────────────────────────────────────────────────────────────┐
│  ┌─────────────────────────┐   ┌─────────────────────────────┐  │
│  │  NETWORK LATENCY        │   │  DOWNLOAD SPEED             │  │
│  │  ────────────────────   │   │  ─────────────────────────  │  │
│  │                         │   │                             │  │
│  │      42 ms              │   │      12.5 Mbps              │  │
│  │    ● Optimal            │   │    ● Good                   │  │
│  │                         │   │                             │  │
│  │  [====== chart ======]  │   │  [======= chart ========]   │  │
│  │                         │   │                             │  │
│  │  Min | Max | Avg | %    │   │  Min | Max | Avg | Last     │  │
│  └─────────────────────────┘   └─────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
```

### 2. Download Speed Test Details

**Test File:** Cloudflare speed test endpoint
- URL: `https://speed.cloudflare.com/__down?bytes=2000000` (2MB)
- Why 2MB? Approximates typical web page load (~2-3MB average)
- Cache-busted with timestamp query param

**Test Interval:** Every 10 seconds (not every 1s like ping)
- Avoids bandwidth saturation
- More realistic for background monitoring

**Metrics to Display:**
- Current speed (Mbps)
- Min/Max/Avg over history window
- Status indicator (color-coded thresholds)

**Speed Thresholds:**
- Good (green): > 25 Mbps
- Moderate (yellow): 10-25 Mbps
- Poor (red): < 10 Mbps

### 3. Technical Implementation

```javascript
// Download speed test function
async function measureDownloadSpeed() {
    const FILE_SIZE = 2_000_000; // 2MB
    const url = `https://speed.cloudflare.com/__down?bytes=${FILE_SIZE}&t=${Date.now()}`;

    const start = performance.now();
    const response = await fetch(url, { cache: 'no-store' });
    await response.arrayBuffer();
    const duration = (performance.now() - start) / 1000; // seconds

    const mbps = (FILE_SIZE * 8) / (duration * 1_000_000); // Mbps
    return mbps;
}
```

### 4. Chart Configuration

- Same uPlot library as latency chart
- Y-axis: Mbps (0 to auto-scaled max)
- X-axis: Last 120 samples (at 10s intervals = 20 minutes history)
- Line color: Different from latency chart (e.g., blue vs black)

### 5. Responsive Behavior

**Desktop (> 900px):** Side-by-side panels
**Mobile (< 900px):** Stacked vertically

### 6. Files to Modify

Only one file: `connection-speed-tester.html`

Changes:
1. Update CSS for two-panel layout
2. Duplicate instrument panel HTML for speed test
3. Add new JavaScript for download speed measurement
4. Add second uPlot chart instance

## Implementation Steps

1. [x] Update CSS - flexbox container for side-by-side layout
2. [x] Add HTML - duplicate instrument panel for speed test
3. [x] Add JS - download speed test function
4. [x] Add JS - second uPlot chart for speed data
5. [x] Add JS - 30-second interval for speed tests
6. [x] Test - verify both charts work independently
7. [x] Responsive - add media query for mobile stacking

## User Decisions

1. **File size:** 2MB (confirmed)
2. **Interval:** 30 seconds
3. **Controls:** Same start/stop button for both
4. **Auto-start:** Speed test starts with latency test

## Status: COMPLETE

Implemented 2026-01-11.
