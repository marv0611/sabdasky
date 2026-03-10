# SABDA — Next Session Context

## Build
```bash
cd ~/Documents/GitHub/sabda && git pull && python3 assemble_murmuration.py && open sabda_murmuration_full.html
```
Scrub timeline at bottom (0-1800s). Balloon house appears at t=600 (10min).

## What Was Done This Session
1. **Removed murmuration** (735 lines of procedural bird sim) — 6 GLB bird flocks kept
2. **Added balloon house** (Up-inspired): house GLB + balloon cluster GLB, ice cream scoop shape from reference analysis, rises from y=-100→y=+80 at t=10min over 60s
3. **Fixed planet logo rotation**: disabled planetMixer, all rotation via planetGroup.rotation.y only (9.9 rotations per loop)
4. **Added SABDA symbol** (concentric circles) on opposite side of planet from text logo
5. **Manual updated to v12.4** with 3 generic pipeline lessons (Section 30)

## Key Parameters

### Balloon House
- Shape: `bhClusterR()` — power 0.75 bottom taper + sqrt dome top, widest at 65%
- `BH_HOUSE_SCALE=0.315, BH_CLUSTER_H=8.89, BH_MAX_R=2.40`
- `BH_EVENT_START=600, BH_EVENT_DUR=60` — single crossing at t=10min
- Position: distance 65, angle PI (left wall)

### Planet
- `planetGroup.rotation.y = (time/1800) * 2π * 9.9`
- Text logo: phi=PI/2, opacity 0.13, thetaOffset=0.12
- Symbol: phi=3*PI/2, opacity 0.3, thetaOffset=0.18, arc 0.80×0.95
- Both on planetGroup, additive blending, R=1.015

## Tomorrow's Agenda
1. **Balloon house timing** — reposition the crossing animation (currently only t=10min, may want different time or multiple passes)
2. **Planet logo review** — verify text logo + symbol in room preview, tweak opacity/size
3. **Finalize** — lock all parameters, verify full 30min loop, prepare for Watchout
