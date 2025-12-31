# Building OrangeFox for SM-A022F (A02)

This repo includes a ready-to-run GitHub Actions workflow to attempt building OrangeFox for Samsung SM-A022F (codename `a02`).

How to run
1. Push `main` (or use the `Run workflow` button in Actions) to trigger `.github/workflows/build-orangefox-a022f.yml`.
2. The workflow will:
   - checkout this repository
   - sync a minimal TWRP manifest
   - clone the OrangeFox device tree (`device_samsung_a02`) and patch bootable/vendor recovery to OrangeFox
   - attempt to build `recoveryimage`
3. On success, `OrangeFox*.zip` and `recovery.img` are uploaded as workflow artifacts.

Customizing
- Edit `.github/workflows/build-orangefox-a022f.yml` to change `MANIFEST_BRANCH` or `FOX_BRANCH` if needed (Android/TWRP/OrangeFox versions).
- If you want to use a different device tree, change `DT_LINK` and `DT_PATH` environment variables in the workflow.

Notes and troubleshooting
- Builds require a lot of memory/time — prefer using a self-hosted runner or CI with plenty of resources.
- If the build fails due to missing device/kernel blobs, consider pointing `DT_LINK` to a tree that contains prebuilt kernels/DTBO or add those blobs to the workflow.
- You can also use the `Recovery-Builder-NoKernel` or `OrangeFox-CI` projects if you prefer their CI templates.

If you want, I can:
- Add a small status badge to `README.md` that points to the workflow, and/or
- Add a GitHub Actions matrix with multiple `FOX_BRANCH` / `MANIFEST_BRANCH` combinations to try different OrangeFox versions automatically.
