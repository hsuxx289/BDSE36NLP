# 中文短句情緒分類

## 訓練資料來源
- [Datasets:Johnson8187/Chinese_Multi-Emotion_Dialogue_Dataset](https://huggingface.co/datasets/Johnson8187/Chinese_Multi-Emotion_Dialogue_Dataset)

## 基礎模型
- [google-bert/bert-base-chinese](https://huggingface.co/google-bert/bert-base-chinese)

## 安裝套件
- torch (2.6.0)
- torchvision (0.21.0)
- torchaudio (2.6.0)
- transformers (4.48.3)
- datasets (3.2.0)
- evaluate (0.4.3)
- accelerate (1.3.0)
- scikit-learn (1.5.5)

## 說明
將中文短句分為下列8個分類
```
    0: "平淡語氣",
    1: "關切語調",
    2: "開心語調",
    3: "憤怒語調",
    4: "悲傷語調",
    5: "疑問語調",
    6: "驚奇語調",
    7: "厭惡語調"

由於資料只有4000筆
num_train_epochs 從 3 調整為 5 增加訓練輪數
per_device_train_batch_size 從 32 調整為 16 依GPU記憶體大小調整
gradient_accumulation_steps 從 2 調整為 3 由於batch size 較小
warmup_steps 從 100 調整為 500 讓模型前期學習穩定
```

## 成果
[NLP-中文短句情緒分類](https://youtu.be/9sgoz7YoPzU)
```
我每天都能跟她一起上學，我好開心！ => 開心語調 (0.99)
最好的朋友要離開臺灣了，以後可能不容易再見面... => 悲傷語調 (0.97)
我覺得我快不行了... => 悲傷語調 (0.98)
剛剛收到研究所錄取的通知書！ => 開心語調 (0.92)
今年的冬天好像比較晚來。 => 平淡語氣 (0.97)
```