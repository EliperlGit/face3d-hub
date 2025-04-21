# HRN 3D Face Reconstruction

This repository contains a modernized version of the Hierarchical Representation Network (HRN) for 3D facial reconstruction, ready for use with Docker, FastAPI, and GitHub Codespaces.

## Quick Start (Codespaces)

1. **Open in Codespaces:** Click the green "Code" button in GitHub and select "Open with Codespaces".
2. **(Optional) Change Machine Type:** In the Codespaces dashboard, select a larger machine (e.g. 4-core) for faster builds.
3. **Build Docker Image:**
   ```sh
   docker build -t hrn-gpu ./backend/HRN
   ```
4. **Run HRN Pipeline (CPU-only on free tier):**
   ```sh
   docker run --rm -v $(pwd)/backend/HRN/assets:/workspace/assets -v $(pwd)/backend/HRN/output:/workspace/output hrn-gpu python3 demo.py --input_root ./assets/examples/single_view_image --output_root ./output
   ```
5. **Commit & Push:** Edit code, commit, and push from Codespaces as usual.

## Local Development

- Clone this repo and follow the same Docker build/run instructions above.
- For GPU support, run on a machine with NVIDIA GPU and drivers.

## Automated Checks

- On every push, GitHub Actions will build the Docker image and lint Python code to catch errors early.

## Troubleshooting

- If assets/models are missing, check your Downloads folder for asset packs and move them to the correct directory.
- For full GPU Codespaces, upgrade your plan and select a GPU-enabled machine.

---

For more help, open an issue or check the workflow logs in GitHub Actions.
