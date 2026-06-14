# SparseInst: Real-Time Instance Segmentation 重現實驗

這是課程期末報告的程式碼與實驗結果備份。
- **論文名稱**：Sparse Instance Activation for Real-Time Instance Segmentation (CVPR 2022)
- **實作硬體**：NVIDIA RTX 5080 (單卡)

## 實驗結果
因為算力與時間限制，最終取得 16.4 mAP。在訓練過程中，開啟 AMP (FP16) 遇到了梯度爆炸導致 NaN 溢出的問題。

權重連結:https://drive.google.com/file/d/1jmbKxawFOmatmPgAKxJeL1u296SDZMD6/view?usp=drive_link

## 💻 環境建置 (Environment Setup)

本專案於以下硬體與軟體環境測試通過：
- **OS**: Ubuntu 22.04
- **GPU**: NVIDIA RTX 5080 (16GB VRAM)
- **CUDA**: 12.8
- **Python**: 3.10 
- **PyTorch**: 2.5.1

### 安裝步驟
1. 建立並啟動虛擬環境（建議使用 Conda）：
   ```bash
   conda create -n sparseinst python=3.10 -y
   conda activate sparseinst
   ```
2. 安裝 PyTorch 與 Torchvision：
   ```bash
   pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
   ```
3. 安裝 Detectron2 (因應新版 PyTorch，需從源碼安裝)：
   ```bash
   python -m pip install 'git+https://github.com/facebookresearch/detectron2.git'
   ```
4. 安裝其餘依賴套件：
   ```bash
   pip install -r requirements.txt
   ```

---

## 🚀 測試與推論 (Inference / Demo)

如果您想使用我訓練好的模型權重進行圖片推論，請按照以下步驟操作：

1. 請先至上方「模型權重下載」區塊，下載 `model_final.pth` 並放置於專案根目錄的 `output/` 資料夾下。
2. 準備一張測試圖片（例如 `test_image.jpg`），然後執行以下指令：

```bash
python demo.py --config-file configs/sparseinst_r50_vd.yaml \
  --input test_image.jpg \
  --output result.jpg \
  --opts MODEL.WEIGHTS output/model_final.pth
```
3. 程式執行完畢後，預測結果會儲存為 `result.jpg`。

