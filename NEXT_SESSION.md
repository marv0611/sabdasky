# SABDA — Next Session Context

## Build
```bash
cd ~/Documents/GitHub/sabda && git pull && python3 assemble_murmuration.py && open sabda_murmuration_full.html
```
Scrub timeline at bottom (0-1800s). Balloon house appears at t=300 (5min), t=900 (15min), t=1500 (25min).

## Render (full 30-min loop)
```bash
cd ~/Documents/GitHub/sabda && node render_murmuration.js full
```
Output: `output/sabda_top.mp4 + sabda_bottom.mp4` (H.264 CRF 14, ~4-8 GB total)

## What Was Done This Session
1. **Balloon house: 3 crossings** at t=5min, t=15min, t=25min (was single crossing at t=10min)
   - t=5min: Left wall B @ 30% (1.01π)
   - t=15min: Right wall D @ 30% (0.01π)
   - t=25min: Left/Front boundary (1.52π)
2. **Balloon colors**: exact "Up" movie palette (magenta, cyan, green, lime, orange), uniform distribution
3. **Balloon shape**: 10% narrower + 8% narrower (total ~36%), rounder dome top (t² hemisphere)
4. **Balloon shininess**: roughness 0.315, metalness 0.05 (10% shinier)
5. **Shooting stars**: frequency reduced from every 1.5-2.5s to every 15-25s
6. **Code audit**: antialias enabled, cubemap mipmaps disabled (sharper), dead code removed, console.logs cleaned
7. **Edge blending verified**: all values match Manual v12.4 Section 29.6 safe ranges for Watchout
8. **Render pipeline**: H.264 MP4 CRF 14 (Watchout recommended format)

## Key Parameters

### Balloon House
- Shape: `bhClusterR()` — power 0.75 bottom taper + sqrt(1-t²) dome top
- `BH_HOUSE_SCALE=0.315, BH_CLUSTER_H=8.89, BH_MAX_R=2.81*0.855*0.90*0.92`
- 3 events: BH_EVENTS array with start/angle/dist per crossing
- Colors: 5 "Up" palette colors, uniform random, no adjacent duplicates
- Rising bottom→top, 60s per crossing, distance 65

### Planet
- `planetGroup.rotation.y = (time/1800) * 2π * 9.9`
- Text logo: phi=PI/2, opacity 0.13, thetaOffset=0.12
- Symbol: phi=3*PI/2, opacity 0.3, thetaOffset=0.18, arc 0.80×0.95

### Shooting Stars
- Frequency: every 15-25 seconds (timer = 15 + rand(10))
- Duration: 3.5-6 seconds each

## Next Steps
- Run full 30-min render → load into Watchout
- Verify loop seam at t=1800→0
- Test on projectors — check edge blending with Watchout soft edge settings

*Standard: 10/10 or nothing.*
