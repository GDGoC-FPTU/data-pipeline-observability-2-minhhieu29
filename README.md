[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112874&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student ID:** AI20K-2A202600705
**Student Email:** minnhhieulc29@.com
**Name:** Nguyễn Minh Hiếu

---

## Mo ta

Bai lab xay dung mot ETL pipeline tu dong: doc du lieu JSON, validate chat luong,
transform (giam gia 10%, chuan hoa category, them timestamp), va luu ra CSV.
Sau do thuc hien stress test so sanh phan hoi cua mot Agent don gian khi dung
du lieu sach (`processed_data.csv`) va du lieu rac (`garbage_data.csv`).

---

## Cach chay (How to Run)

### Prerequisites
```bash
python -m venv venv
# Windows:
.\venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```

Ket qua chi tiet duoc ghi trong `experiment_report.md`.

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── raw_data.json            # Du lieu dau vao
├── processed_data.csv       # Output cua pipeline (clean data)
├── garbage_data.csv         # Du lieu rac cho stress test
├── agent_simulation.py      # Mo phong Agent tra loi cau hoi
├── generate_garbage.py      # Tao file garbage_data.csv
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Input:** 5 records tu `raw_data.json`
- **Valid:** 3 records (Laptop, Chair, Monitor)
- **Dropped:** 2 records (Mystery Box: gia am; Phone: category rong)
- **Transform:** Them `discounted_price` (giam 10%), `category` Title Case, `processed_at`
- **Stress test:** Agent tra loi dung voi clean data (Laptop $1200), tra loi sai voi garbage data (Nuclear Reactor $999999 do outlier)
