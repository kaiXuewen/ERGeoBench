# Upload Instructions

This package is ready to upload to GitHub.

## Option A: Upload through GitHub web UI

1. Create a repository named `ERGeoBench` under `kaiXuewen`.
2. Upload all files and folders in this package to the repository root.
3. Go to `Settings -> Pages`.
4. Set:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/docs`
5. Save.
6. Wait a few minutes and visit:

https://kaiXuewen.github.io/ERGeoBench/

GitHub Pages requires an entry file such as `index.html` at the root of the publishing source folder. This package already provides `docs/index.html`.

## Option B: Push with git

```bash
git clone https://github.com/kaiXuewen/ERGeoBench.git
cd ERGeoBench
cp -r /path/to/ERGeoBench_GitHub_Ready/* .
git add .
git commit -m "Initialize ERGeoBench project page and repository placeholder"
git push origin main
```

Then configure GitHub Pages as described above.
