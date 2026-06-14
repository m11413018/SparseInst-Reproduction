# SparseInst: Real-Time Instance Segmentation 重現實驗

這是課程期末報告的程式碼與實驗結果備份。
- **論文名稱**：Sparse Instance Activation for Real-Time Instance Segmentation (CVPR 2022)
- **實作硬體**：NVIDIA RTX 5080 (單卡)

## 實驗結果
因為算力與時間限制，最終取得 16.4 mAP。在訓練過程中，開啟 AMP (FP16) 遇到了梯度爆炸導致 NaN 溢出的問題。

