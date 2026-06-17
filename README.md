## Dataset

The pre-generated 100-household SynthNILM corpus (`synthnilm_v2.h5`, ~300 MB, plus per-house CSV folders) is too large for GitHub's file size limit and is hosted externally.

**Download:** [Google Drive — SynthNILM Dataset](https://drive.google.com/drive/folders/18KRzfxDkHQ-Cq4hsbGV7AEPr9KfThu_D?usp=sharing)

Includes:
- `synthnilm_v2.h5` — full corpus in NILMTK-compatible HDF5 format
- `house_001/` – `house_100/` — per-house CSV files (`aggregate.csv` + one CSV per appliance)
- `dataset_metadata.json` — full manifest with per-house profile, seed, and appliance list
- `dataset_metadata.yaml` — same manifest in YAML

> **Note:** This dataset can be regenerated exactly using `seed=42` and the generation code/library in this repository — see [Quick Start](#quick-start) above. A permanent, DOI-citable archive of this dataset will be published on Zenodo; this link will be updated once that is live.

**To use it:**

```python
import pandas as pd

store = pd.HDFStore('synthnilm_v2.h5', 'r')
agg   = store['/building1/elec/meter1']   # aggregate power, house 1
app   = store['/building1/elec/meter2']   # first appliance, house 1
store.close()
```

Or load the CSVs directly:

```python
import pandas as pd

agg = pd.read_csv('house_001/aggregate.csv', parse_dates=['timestamp'])
```
