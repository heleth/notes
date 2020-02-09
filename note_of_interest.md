## To do  
* markdown内での数式(疑似数式含む)の良い書き方を見つけたい気がする  

## 2020XXXX  
### source  
### summary  
### content  


## 20200209  
### source  
MarIQ -- Q-Learning Neural Network for Mario Kart -- 2M Sub Special  
https://www.youtube.com/watch?v=Tnu4O_xEmVk  
### summary  
MarIQ (マリオカートをプレイするAI (Deep Q Learning) )の紹介 (コード, ドキュメントあり)  
### content  
- MarIQ  
  - RNN  
  - 2つのLSTM (Long Short Term Memory) を持つ
  - Requirement  
    - Python 3.5.0 (64bit)
    - CUDA Development Tools 8.0.61 (64bit)
    - CuNN 6 (64bit)
      - For some reason downloading this requires creating an account.
      - With the release of Tensorflow 1.4, you may need CuNN 7 instead.
    - Visual C++ 2015 Redistributable
    - tensorflow-gpu/tensorflow 1.3 (can be installed with pip etc.)
    - pygame (can be installed with pip etc: pip install pygame)
    - Bizhawk 1.12.2
    - Super Mario Kart ROM.
      - You’ll need to acquire dsp1b.rom as well, and install it into the Bizhawk.



## 20200209  
### source  
A step-by-step guide to building a simple chess AI
https://www.freecodecamp.org/news/simple-chess-ai-step-by-step-1d55a9266977/  
### summary
JSを用いてチェスAI (minimax法) を実装する方法の紹介 (コードあり)  


## 20200209  
### source  
遺伝的アルゴリズムでソニック・ザ・ヘッジホッグを攻略  
https://note.com/npaka/n/n9c0377b1e560  
原文 https://www.freecodecamp.org/news/how-to-use-ai-to-play-sonic-the-hedgehog-its-neat-9d862a2aef98/  
### summary  
- Gym Retroを用いてソニックのゲームをプレイするAIを作る方法の概説  
### content  
-  Gym Retro  
  - Gym環境でレトロゲームを実行するツール  
    強化学習を用いてゲームAIを作成することができる  
  - エミュレーター用のROMが存在するレトロゲーム(の一部)をGym環境で実行できる  


## 20200209  
### source  
I created an AI to Play Chess  
https://www.youtube.com/watch?v=DZfv0YgLJ2Q  
### summary  
- JSで実装したチェスAI (MiniMax法)の紹介  
### content  
- Java Scriptで実装  
- Minimax  
  - チェスAIが次の1手を決める方法  
  - 評価関数があり、自分はその最大化を、相手はその最小化を目指すと仮定する.  
    その上で、｢相手が常に最善の手を打つ｣という前提のもとで自分が打てる最善の手を考える.  
- Alpha-beta pruning  
  - Minimaxにおいて計算量を削減する方法  
### note  
- コーディング実況 (おもしろい)  


## 20200209  
### source  
MarI/O - Machine Learning for Video Games  
https://youtu.be/qv6UVOQ0F44  
  - source code : https://pastebin.com/ZZmSNaHX  
### summary  
- NEATを用いた、スーパーマリオをプレイするNNの解説  
### content  
- NEAT (Neuro Evolution of Auguenting Topologies)  
  - Neuroevolution (NNをgeneric algorithm (遺伝的アルゴリズム) でトレーニングする方法) の1つ  
  - NNの構造を予め最適化する必要がない  
  - genomeをspeciesに分割する  
  - 論文 : http://nn.cs.utexas.edu/downloads/papers/stanley.ec02.pdf (Stanley and Miikkulainen, 2002)  
- Lua  
  - プログラミング言語の1つ  
  - 1993年リリース  
  - 特にゲームの実装言語におけるシェアが高いらしい  
  - 構文はPascalによく似ているらしい  
- NEATの考え方によりNNをトレーニング.  
- Fitness : キャラの進んだ距離とそこに到達する早さの関数.   
  Fitnessの点数が高いNNが次世代のNNを育てるもととなる.   
- 投稿主はMarI/OをLua (BizHawk emulator用プラグイン) でスクラッチから実装  


## 20200208  
### source  
How to teach AI to play Games: Deep Reinforcement Learning  
https://towardsdatascience.com/how-to-teach-an-ai-to-play-games-deep-reinforcement-learning-28f9b920440a  
"In this article, we will see how to develop an AI Bot able to learn how to play the popular game Snake from scratch. To do it, we implement a Deep Reinforcement Learning algorithm using Keras on top of Tensorflow. This approach consists in giving the system parameters related to its state, and a positive or negative reward based on its actions. No rules about the game are given, and initially the Bot has no information on what it needs to do. The goal for the system is to figure it out and elaborate a strategy to maximize the score — or the reward."  
### summary  
- ゲームエージェントとしての強化学習の概説と、シンプルな実装の解説  
### next  
- サンプルコードがあるので、そのコードを理解したい  
### content  
* Artificial intelligenceとArtificial behaviorは異なる. ゲームAIはMLの限界に挑戦する必要はなく、人間プレイヤーの相手を務められる程度に賢ければ良い.   
* Pygame : Pythonで簡単なゲームをコードできるライブラリ.  
* 強化学習  
  - Markov Decision Processに基づく  
  - システムはactionに対してrewardを受け取り、rewardを最大化するactionを学習する.  
* Deep Q-Learning  
  - 強化学習の1手法  
  - Q-table : Deep Q-Learningのコンポーネント?  
    - agentのstateと取りうるactionのペアに対して、｢トレーニング中に得たrewardに基づくactionの成功確率｣? Q-value Q(s,a) をまとめた表  
    - Q-tableを更新していくことでQ-Learningの性能?が上がる  
  - アルゴリズムのワークフロー  
    1. ゲーム開始時、Q-tableを乱数で初期化  
    2. システムが現在のstate s を取得  
    3. システムが現在のsに基づきactionを実行  
      (actionの選択はランダムまたはNNによって行われる. 傾向として、トレーニングの初期は探索範囲の最大化のためにランダムに選択され、トレーニング終盤はNNによって選択される)  
    4. システムは実行したactionに対してrewardを獲得し、新しいstate state' を取得. Bellman equationに基づきQ-tableを更新する. 
      - Bellman equation  
        <New Q-value> =  
          <Current Q-value> +  
          <Learning rate> * (  
            <reward> +  
            <Discount rate> * <maximum predicted reward, given new state and all possible actions> -  
            <Current Q-value>  
            )  
      同時に、[s, action, state', reward, <the game is ended or not>] を取得. (後でNNのトレーニングに使用) (Replay Memoryと呼ばれるオペレーション)  
    5. 一定の条件を満たすまで上2つを繰り返す  
  - 状態 state  
    - agentがいる状況の表現  
    - NNのインプット  
  - action  
    - NNのアウトプット  
  - NN  
    - loss  
      - NNの推論したQ-valueと実際のQ-valueの差を最小化するようにLossを設定する.  
    - 記事での実装  
      - loss = (r + gammma * <maximum predicted Q-value in all possible actions(?)> - <real Q-value>)^2
      - layers  
        3 hidden layers of 120 neurons  
        3 dropout layers  
        laster layer uses Softmax  
      - learning rate  
        starts at 0.0005, decreases to 0.000005  
      - implementation  
        記事内に掲載  
  - Deep Q-Learningはより正確なconvergenceのためにDouble Deep Q-Learningに置き換えることもできる.  


