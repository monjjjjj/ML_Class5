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

## Theory of GAN and WGAN
### 訓練的目標：P(G)跟P(data)的分佈越小越好
1. GAN告訴我們，只要你知道如何從P(G)跟P(data)這兩個分佈sample東西出來，就能夠計算他們的divergence
2. 藉由discriminator就能算出divergence
3. Objective function: maximize

   Loss function: minimize
4. 不知道如何算divergence? 只要train完discriminator之後，看他的ibjective function可以到多大，此值就跟divergence有關

### 訓練GAN的小技巧
1. 我們對P(G)跟P(data)分佈的理解，其實是來自sample
   假設sample的點不夠多、不夠密，即使這兩個分佈實際上有重疊，對discriminator來說他們兩個是沒有重疊的！
2. 不管兩個分佈長什麼樣子，只要沒有重疊，JS divergence算出來就是log2
   可能會是generator無法去更新參數來達到比較好的結果
3. Wasserstein distance
   會窮舉所有的moving plan，找出最小的moving distance，該距離即為Wasserstein distance
4. 計算Wasserstein distance的好處： 可以觀察到Generator表現越來越好，解決了JS Divergence帶來的問題

### Evaluation of GAN and Conditional GAN
