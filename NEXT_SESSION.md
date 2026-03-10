# SABDA — Next Session Context

## Build & Preview
```bash
cd ~/Documents/GitHub/sabda && git pull && python3 assemble_murmuration.py && open sabda_murmuration_full.html
```
Controls: R=360° room, Y=5x speed, T=30x speed, D=guides, P=projector strips

## Render (full 30-min loop)
```bash
cd ~/Documents/GitHub/sabda && node render_murmuration.js full
```
Output: `output/sabda_top.mp4 + sabda_bottom.mp4` (H.264 CRF 14)

## What Was Done This Session
1. **Balloon house: 3 crossings** at t=5min (1.10π), t=15min (0.01π), t=25min (1.56π)
2. **Balloon colors**: "Up" palette + 2 extra blues (7 colors), smoother materials
3. **Balloon shape**: narrower, rounder dome, computeVertexNormals
4. **Sky lanterns**: 70 lanterns filling 360° room at t=20:00 over 90s
   - Golden angle distribution, wall corner avoidance (60cm exclusion)
   - Real sky lantern GLB (optimized 340KB), emissive glow baked in
   - Natural rise physics: cubic ease-in, wind drift, paper wobble
5. **Shooting stars**: frequency 1.5-2.5s → 15-25s
6. **360° room viewer**: press R (Section 19 in manual)
   - Correct SABDA room geometry, matte gray floor
   - Identical post-processing pipeline as strip view (sRGB RT → blit)
   - Color-matched: same shader, same tone mapping, same pipeline
7. **Performance**: zero per-frame allocations, antialias off, optimized lantern model
8. **Color fix**: saturation 1.45→1.30, highlight ceiling 0.85→0.90 (less muddy purples)
9. **Saturn**: textures 2K→1K (25.5MB b64, no visible quality loss)
10. **Timer**: real-time elapsed, Y=5x speed, T=30x speed

## Scene: 63.9MB assembled

## Next Steps
- Run full 30-min render → load into Watchout
- Verify loop seam at t=1800→0
- Test on projectors

*Standard: 10/10 or nothing.*
