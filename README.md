# ML_Class5
## GAN: Basic
1. Simple distribution: distribution的形狀由自己決定，只要記住他是簡單的、可以sample他的即可
2. Generator: 可以輸出為一個distribution的network 
### 為什麼我們需要generator?為什麼需要輸出是一個分部呢？
1. 當任務需要一點創造力的時候！（我們想要找一個function，同樣的輸入有多種不同的輸出，而這些輸出都是對的、可被接受的）
### Generative Adversarial Network （GAN）
1. 除了要訓練Generator以外，還要訓練Discriminator
   
   Discriminator輸出是一個數值，數值越大代表越真，數值越小代表越假
   
2. GAN的基礎概念
  
    (1) Discriminator的作用：分辨Generator的輸出跟真實圖片的差異

    (2) Generator跟Discriminator之間有對抗(adversarial)的關係，亦敵亦友的關係
    
    (3) Discriminator訓練的目標：為了分辨真正的二次元人物與Generator產生的二次元人物之間的差異，可以當作分類的問題來做，也可以當作regression的問題來做
        
        Generator訓練的目標：為了讓Discriminator的輸出值越大越好！
