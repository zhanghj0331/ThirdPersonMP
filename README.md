### Git LFS 使用方法

1. 下载git lfs https://git-lfs.com/

2. https://help.aliyun.com/document_detail/206889.html
   git lfs install
   git lfs track "*.uasset"
   git add .
   git commit -m "Add \"*.uasset\" LFS config "

   git add .
   git commit -m "setup project"

### Git 的基础指令

将远端的分支合并到本地 git merge origin/main

# UE 网络

1. 只在服务器端执行

```cpp
if (GetLocalRole() == ROLE_Authority)
```

2. 只在本地客户端执行

```cpp
if (IsLocallyControlled())
```

3. Current Health发生变化同步给所有客户端，OnRep_ 只在对应变化的那一个客户端调用

```cpp
/** 玩家的当前生命值。降到0就表示死亡。*/
UPROPERTY(ReplicatedUsing=OnRep_CurrentHealth)
float CurrentHealth;

/** RepNotify，用于同步对当前生命值所做的更改。*/
UFUNCTION()
void OnRep_CurrentHealth();
```

