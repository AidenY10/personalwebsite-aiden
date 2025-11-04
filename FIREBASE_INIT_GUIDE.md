# Firebase Hosting Initialization Guide

## Why Your Public Folder Disappears

When you run `firebase init hosting`, your public folder can disappear if:

1. **You answer "Yes" to overwrite existing files** - Firebase will delete existing files
2. **You specify an existing folder that has conflicts** - Firebase may clear it
3. **The folder is being treated as a build output** - Build tools may clear it

## Safe Initialization Steps

### Option 1: Backup First (Recommended)
```bash
# Backup your public folder before initializing
cp -r public public_backup

# Then run firebase init
firebase init hosting

# When prompted:
# - Public directory: public (or your folder name)
# - Overwrite existing files? NO
# - Single-page app? Answer based on your needs
# - Set up automatic builds? Choose based on your needs
```

### Option 2: Use a Different Directory Name
```bash
# If you have a build output folder (like dist or build)
firebase init hosting

# When prompted:
# - Public directory: dist (or build, or whatever your build outputs to)
# - This avoids conflicts with your source public folder
```

### Option 3: Initialize with Existing Config
```bash
# Create firebase.json manually first
# Then run firebase init hosting and choose to keep existing config
```

## Recovery

If your public folder was deleted:

1. **Check Git history** (if using version control):
   ```bash
   git log --all --full-history -- public/
   git checkout HEAD~1 -- public/
   ```

2. **Check your backup** (if you created one)

3. **Check Time Machine** (if enabled on macOS)

4. **Check trash/recycle bin**

## Best Practices

- Always backup important folders before running `firebase init`
- Use version control (Git) to track your files
- Consider using a build output directory separate from source files
- Read prompts carefully during initialization

