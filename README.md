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

## Evaluation of GAN and Conditional GAN
1. 拿GAN來生成一段文字其實是最困難的！
### 如何去盼對現在的Generator是好或差呢？
1. Mode Collapse: train到後來發現generator只會產生某幾種結果

   為何會發生Mode Collapse？
   
   Generator發現了Discriminator的盲點，發現Discriminator在某些結果下無法去判斷真偽
2. FID

   假設真實的圖片與產生出來的圖片，他們都是高斯分佈，然後再去計算兩個分佈之間的FID，距離越小代表兩組圖片越接近、品質越高
   
### Conditional generation
1. Discriminator要多一個input(condition)

## CycleGAN
### 把GAN用在un-supervised learning上
1. 如何強化generator的input與output之間的關係呢？

   在Conditional GAN的時候有遇到類似的問題！但無法直接套用，因為在Conditional GAN中有成對的資料，但現在我們沒有成對的資料～
   
   -> Cycle GAN (Train兩個generators)
2. Cycle GAN

   經過兩次Generators的轉換之後，希望輸入跟輸出的結果越接近越好！

   Cycle GAN可以強迫Generator輸出的y domain的圖片跟輸入的x domain的圖片有一些關係！(但如何確認這個關係是我們要的？機器有沒有可能train到很奇怪的關係？)
   
   經過兩次Generators的轉換之後，希望輸入跟輸出的結果越接近越好！
