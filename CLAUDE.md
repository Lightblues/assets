# Assets

Static assets repository for blog and wiki, served via jsdelivr CDN.

## Quick Reference

- Repo: `Lightblues/assets`
- CDN base: `https://cdn.jsdelivr.net/gh/lightblues/assets@main/`
- No build step — push to main and CDN serves files directly

## Directory Structure

```
assets/
├── blog/          # Blog images (covers, gallery, meta)
│   ├── _meta/     # favicon, avatar, about
│   ├── EVA/       # Cover images
│   ├── cosmos/
│   ├── GhostBlade-WLOP/
│   ├── CowboyBepop/
│   ├── SamuraiChamploo/
│   ├── Fate/
│   ├── Ukiyo-e/
│   ├── 2405-kubuqi/  # Photo gallery
│   └── movies/
├── wiki/          # Wiki/notes images (per-topic folders)
├── upload/        # Misc uploads
├── slidev/        # Slide assets
└── utils/         # Utility files
```

## URL Pattern

```
https://cdn.jsdelivr.net/gh/lightblues/assets@main/{project}/{category}/{file}
```

Examples:
- `https://cdn.jsdelivr.net/gh/lightblues/assets@main/blog/EVA/eva-00001.jpg`
- `https://cdn.jsdelivr.net/gh/lightblues/assets@main/wiki/Python-note/16087172700264.jpg`

## Adding New Images

```bash
# 1. Add files to appropriate directory
cp image.jpg blog/{category}/  # or wiki/{topic}/

# 2. Commit and push
git add . && git commit -m "Add images for ..." && git push

# 3. (Optional) Warm CDN cache for blog images
cd ~/Projects/output/blog/scripts/dns && python purge_jsdelivr.py
```

## CDN Notes

- jsdelivr caches files globally; new files may 404 briefly until CDN propagates
- Use `https://purge.jsdelivr.net/gh/lightblues/assets@main/{path}` to force refresh
- Batch purge script: `~/Projects/output/blog/scripts/dns/purge_jsdelivr.py`
- Max file size: 50MB per file
- Repo size: keep under 1GB total (currently ~230MB)

## Related Projects

- Blog: `~/Projects/output/blog` → `blog.easonsi.site`
- Wiki: `~/Projects/output/wiki` → `notes.easonsi.site`
