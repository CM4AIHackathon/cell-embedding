# Cardiac Knowledge Graph + GEARS + (Experimental) CellFM

## Status Notice
- **CellFM zero-shot pipeline:** The included Colab/CPU version with MindSpore shims is present in this repo but is **not currently producing valid embeddings**. It's kept here for reference, debugging, and potential future fixes.
- **GEARS pipeline:** Runs end-to-end with cardiac KG inputs, but the predictions have **not yet been biologically validated**. Treat results as *demonstrations* only.

---

## What's Inside
- **GO/SIGNOR-based cardiac KG builder** with automatic coexpression fallback.
- **GEARS-ready export** (GraphML, PyG `.pt`, and `go_essential_*.csv`).
- **Candidate perturbation list** generation for downstream simulations.
- **Targeted install script** for MindSpore 2.4.0 + scanpy 1.10 + scib 1.1.5 (Colab-friendly).
- **Hardened CellFM zero-shot script**:
  - NumPy 2.x compatibility patch.
  - MindSpore import guard with fix instructions.
  - Memory-safe shard computation.
  - Metadata/column validation before model forward pass.

---
## Project
- knowledge-graph-CM4AI.ipynb # GO+SIGNOR+coexpression graph creation
- gears-cm4ai.ipynb # Perturbation filtering + model training
- cleaned-up.ipynb # Experimental CPU CellFM embedding script
- dataset used: KOLF2.1J_undifferentiated_untreated_chromatin.h5ad -- sourced from CM4AI 2024 release
  - https://drive.google.com/file/d/1F2Vh44WsYDairPgloPK8Hp6vfjR8YvTU/view?usp=drive_link

## Intended Workflow
1. **Build Cardiac KG**  
2. **Train GEARS (optional)**  
3. **Run Simulations**  
4. *(Optional)* Attempt CellFM embeddings — *currently not functional*.  

---

## Showcase Outputs
- Cardiac KG: `N` nodes × `M` edges (GO/SIGNOR/coexpression sources)
- GEARS predictions for cardiac perturbations (unvalidated)
- UMAP plots of baseline vs perturbed states
- Ranked gene effect tables

NOT VALIDATED YET:
<img width="612" height="437" alt="image" src="https://github.com/user-attachments/assets/62c994df-dbde-4bd9-9dc4-64d6db025773" />
<img width="4471" height="3566" alt="image" src="https://github.com/user-attachments/assets/37ea718b-54ff-4918-a779-badad431f697" />
<img width="4454" height="2965" alt="image" src="https://github.com/user-attachments/assets/be4c9234-bef9-4dbe-a823-e365389a9f27" />
<img width="812" height="520" alt="image" src="https://github.com/user-attachments/assets/53e240a6-4d55-4d8a-96b4-37af655eb46f" />


---

> This is an **active research/development repo**.  
> Scripts are kept in working order where possible, but some (CellFM pipeline) are included as *research artifacts* and will fail without further debugging.
