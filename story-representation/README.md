# Story Representation

物語を文章ではなく、AIが扱える構造データとして管理する実験です。

## Concept

桃太郎を題材に、以下を分解して管理します。

- world: 世界・場所
- characters: 登場人物
- factions: 勢力
- items: アイテム・宝物・生活道具
- events: 出来事
- claims: 各勢力の言い分
- narratives: 物語のイベント列
- schemas: データ構造のテンプレート

## Directory

```txt
story-representation/
├── README.md
├── schemas/
│   └── item.schema.yml
└── worlds/
    └── momotaro/
        ├── story.yml
        ├── factions/
        │   └── oni_clan.yml
        └── items/
            ├── peach.yml
            ├── kibidango.yml
            ├── boat.yml
            ├── flag.yml
            ├── axe.yml
            └── treasures/
                ├── golden_mallet.yml
                ├── coral_branch.yml
                └── treasure_chest.yml
```

## Core Idea

アイテムは単なる小道具ではなく、物語を動かすノードです。

- 物理情報
- 所有権
- 物語上の役割
- 象徴
- 各勢力の解釈
- 二次創作フック

を持たせることで、AIが世界を再構成しやすくなります。
