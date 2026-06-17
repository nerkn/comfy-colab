# comfy-colab

Generate images with **SDXL** on a free **Google Colab T4 GPU**, no local GPU needed.

One self-contained notebook — all logic lives in the cells, nothing external.

## Use it

Click → opens in Colab, ready to run:

**[comfy_colab.ipynb](https://colab.research.google.com/github/nerkn/comfy-colab/blob/main/comfy_colab.ipynb)**

1. **Runtime → Change runtime type → T4 GPU** (free tier)
2. **Runtime → Run all**

First run clones ComfyUI + downloads SDXL (~6.5 GB, ~2 min). Then it boots the
server and generates one image. Subsequent runs in the same session are instant.

## Iterate

Edit the **`prompt`** field in cell 3, re-run cells **3 + 4** only. Change `seed`
for variations. The `#@param` fields (seed, width, height, steps, cfg) give a form UI.

## Cells

| # | Cell | What it does |
|---|------|--------------|
| 1 | Setup | Clone ComfyUI, pip install, download SDXL base |
| 2 | Start server | Boot ComfyUI on `:8188` in the background |
| 3 | Generate | Build workflow, POST to API, poll, save PNG |
| 4 | Display | Show the result inline |

## Notes

- Output PNGs are saved to `ComfyUI/output/` on the Colab VM — **ephemeral**.
  To keep an image, download it via the Colab file browser (sidebar → 📁) or mount
  Google Drive and copy there.
- The notebook is idempotent: re-running cell 1 skips already-downloaded files.
- Server survives cell exits (launched with `start_new_session=True`).
