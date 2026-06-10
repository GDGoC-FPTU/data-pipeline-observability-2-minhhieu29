# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-XXXX
**Name:** Nguyễn Minh Hiếu
**Date:** 10/06/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Tra loi dung, chon san pham electronics co gia cao nhat hop ly |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Tra loi sai do outlier 999999 lam logic idxmax() chon nham |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi dung Garbage Data, Agent van chay duoc nhung tra loi sai hoan toan. Nguyen nhan chinh la du lieu chua nhieu loi chat luong ma pipeline ETL chua duoc ap dung de lam sach.

Duplicate ID (id=1 xuat hien 2 lan) lam Agent khong biet record nao la nguon dang tin cay. Wrong data type o cot price ("ten dollars" thay vi so) co the gay loi khi so sanh hoac lam lech ket qua tinh toan. Extreme outlier (Nuclear Reactor gia 999999) khien ham idxmax() chon san pham sai — day la loi ro nhat trong thi nghiem nay. Null values o id, category va price bang 0 cung co the lam crash hoac bo qua du lieu quan trong.

Trong khi do, Clean Data da qua validate (loai gia <= 0, category rong), transform (Title Case, discounted_price) nen Agent tim dung subset Electronics va chon Laptop — ket qua hop ly nhat.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Prompt chi dinh huong cau hoi, nhung Agent phu thuoc hoan toan vao du lieu CSV dau vao. Du prompt ro rang ("best electronic product"), neu du lieu co outlier, sai kieu hoac trung lap thi logic don gian cua Agent van tra loi sai hoac crash. ETL pipeline va data observability la buoc bat buoc truoc khi dua du lieu vao he thong AI.
