# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600898
**Name: Truong Hai Quan**
**Date:** 10th Jun 2026.

***

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario                          | Agent Response                                                    | Accuracy (1-10) | Notes                        |
| --------------------------------- | ----------------------------------------------------------------- | --------------- | ---------------------------- |
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at \$1200.            | 10              | Correct                      |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at \$999999. | 1               | Failed because of input data |

***

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent sai vi khong co buoc validation, coi toan bo garbage data la hop le. Outlier (Nuclear Reactor 999999) khien `idxmax()` chon ngay no lam "deal tot nhat". Sai kieu du lieu (`'ten dollars'`) lam ca cot `price` thanh text, so sanh tim max chay sai logic. Duplicate ID pha vo tinh toan ven, con null values le ra phai bi loai bo. Agent khong tu nhan biet duoc du lieu ban nen xu ly rac y nhu su that.

***

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Dong y. Du prompt co viet hoan hao den dau, neu du lieu dau vao la rac thi agent van tra loi sai, vi cau tra loi duoc rut ra truc tiep tu du lieu chu khong phai tu prompt. Cung mot logic agent: voi clean data (da qua validate/transform) thi tra loi dung, con voi garbage data thi sai hoan toan. Vi vay chat luong du lieu la nen tang — mot pipeline ETL co validation tot quan trong hon viec toi uu prompt.
