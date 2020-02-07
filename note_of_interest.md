## 20200208  
### source  
"How to teach AI to play Games: Deep Reinforcement Learning"  
[https://towardsdatascience.com/how-to-teach-an-ai-to-play-games-deep-reinforcement-learning-28f9b920440a]  
"In this article, we will see how to develop an AI Bot able to learn how to play the popular game Snake from scratch. To do it, we implement a Deep Reinforcement Learning algorithm using Keras on top of Tensorflow. This approach consists in giving the system parameters related to its state, and a positive or negative reward based on its actions. No rules about the game are given, and initially the Bot has no information on what it needs to do. The goal for the system is to figure it out and elaborate a strategy to maximize the score — or the reward."  
### summary  
  - ゲームエージェントとしての強化学習の概説と、シンプルな実装の解説  
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
      同時に、[s, action, state', reward, <the game is ended or not>]を取得. (後でNNのトレーニングに使用) (Replay Memoryと呼ばれるオペレーション)  
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
