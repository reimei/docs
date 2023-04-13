
# TSRPC API 接口文档

## 通用说明

- 所有请求方法均为 `POST`
- 所有请求均需加入以下 Header :
    - `Content-Type: application/json`

## 目录

- analyze
    - [获取活跃人数](#/analyze/GetActive)
    - [获取新增人数](#/analyze/GetAdd)
    - [获取留存](#/analyze/GetRetain)
    - [获取概要](#/analyze/GetSummary)
- control
    - [添加点控](#/control/AddControl)
    - [移除点控](#/control/RemoveControl)
- game
    - [获取扯旋配置](#/game/GetCheXuan)
    - [获取五子棋配置](#/game/GetFIR)
    - [获取捕鱼配置](#/game/GetFish)
    - [设置扯旋](#/game/SetCheXuan)
    - [设置五子棋](#/game/SetFIR)
    - [配置捕鱼](#/game/SetFish)
- player
    - [获取玩家列表](#/player/Get)
    - [获取对局记录](#/player/GetMatchLog)
    - [获取实时在线](#/player/GetOnline)
    - [上分](#/player/GoldOperate)
    - [锁定/解锁玩家](#/player/Set)
- rank
    - [获取排名](#/rank/Get)
- store
    - [获取商品列表](#/store/Get)
    - [设置商品列表，只传修改的字段](#/store/Set)
- system
    - announce
        - [发送通知](#/system/announce/Send)
    - config
        - [获取后台开关](#/system/config/Get)
        - [设置后台开关](#/system/config/Set)
    - [获取任意记录](#/system/GetOperateLog)
    - [发送跑马灯](#/system/SendMarquee)
- verify
    - [查询验证码](#/verify/Get)

---

## analyze

### 获取活跃人数 <a id="/analyze/GetActive"></a>

**路径**
- POST `/analyze/GetActive`

**请求**
```ts
interface ReqGetActive {
    filter: {
        dateStart: /*datetime*/ string,
        dateEnd: /*datetime*/ string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetActive {
    /** 返回数据[...[dateNumber,value]...] */
    data: [number, number][],
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BAnalyze"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 获取新增人数 <a id="/analyze/GetAdd"></a>

**路径**
- POST `/analyze/GetAdd`

**请求**
```ts
interface ReqGetAdd {
    filter: {
        dateStart: /*datetime*/ string,
        dateEnd: /*datetime*/ string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetAdd {
    /** 返回数据[...[dateNumber,value]...] */
    data: [number, number][],
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BAnalyze"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 获取留存 <a id="/analyze/GetRetain"></a>

**路径**
- POST `/analyze/GetRetain`

**请求**
```ts
interface ReqGetRetain {
    filter: { date: /*datetime*/ string },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetRetain {
    /** 1日留存 */
    day1: number,
    /** 3日留存 */
    day3: number,
    /** 7日留存 */
    day7: number,
    /** 15日留存 */
    day15: number,
    /** 30日留存 */
    day30: number,
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BAnalyze"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 获取概要 <a id="/analyze/GetSummary"></a>

**路径**
- POST `/analyze/GetSummary`

**请求**
```ts
interface ReqGetSummary {
    filter: {
        dateStart: /*datetime*/ string,
        dateEnd: /*datetime*/ string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetSummary {
    /** 总玩家数 */
    totalPlayer: number,
    /** 总付费玩家数 */
    totalPayedPlayer: number,
    /** 总赠送金币 */
    totalSend: number,
    /** 游戏盈亏 */
    games: {
        /** 名称 */
        name: string,
        /** 活跃玩家 */
        activePlayer: number,
        /** 新增玩家 */
        addPlayer: number,
        /** 游戏局数 */
        matchCount: number,
        /** 玩家胜率 */
        playerWinRate: number,
        /** 玩家输赢 */
        playerMatchResult: number,
        /** 系统抽水 */
        tax: number
    }[],
    /** 房间盈亏 */
    rooms: {
        /** 名称 */
        name: string,
        /** 活跃玩家 */
        activePlayer: number,
        /** 新增玩家 */
        addPlayer: number,
        /** 游戏局数 */
        matchCount: number,
        /** 玩家胜率 */
        playerWinRate: number,
        /** 玩家输赢 */
        playerMatchResult: number,
        /** 系统抽水 */
        tax: number
    }[],
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BAnalyze"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

## control

### 添加点控 <a id="/control/AddControl"></a>

**路径**
- POST `/control/AddControl`

**请求**
```ts
interface ReqAddControl {
    UID: number[],
    step: {
        /** 概率权重（-1000~1000） */
        weight: number,
        value: number
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResAddControl {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "OControl"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 移除点控 <a id="/control/RemoveControl"></a>

**路径**
- POST `/control/RemoveControl`

**请求**
```ts
interface ReqRemoveControl {
    UID: number[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResRemoveControl {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "OControl"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

## game

### 获取扯旋配置 <a id="/game/GetCheXuan"></a>

**路径**
- POST `/game/GetCheXuan`

**请求**
```ts
interface ReqGetCheXuan {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetCheXuan {
    room: {
        /** 游戏名，不可更改 */
        game: string,
        /** 房间名，不可更改 */
        field: string,
        /** 入场分数下限，0不限 */
        minGold: number,
        /** 入场分数上限，0不限 */
        maxGold: number,
        /** 最小下注 */
        minBet: number
    }[],
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BGameSettings"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 获取五子棋配置 <a id="/game/GetFIR"></a>

**路径**
- POST `/game/GetFIR`

**请求**
```ts
interface ReqGetFIR {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetFIR {
    room: {
        /** 游戏名，不可更改 */
        game: string,
        /** 房间名，不可更改 */
        field: string,
        /** 入场分数下限，0不限 */
        minGold: number,
        /** 入场分数上限，0不限 */
        maxGold: number,
        /** 最小下注 */
        minBet: number
    }[],
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BGameSettings"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 获取捕鱼配置 <a id="/game/GetFish"></a>

**路径**
- POST `/game/GetFish`

**请求**
```ts
interface ReqGetFish {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetFish {
    room: {
        /** 当前奖池金额 */
        currentPool: number,
        /** 注入抽水比例 */
        taxRate: number,
        /** 注入奖池比例 */
        poolRate: number,
        /** 奖池上限 */
        topLimit: number,
        /** 奖池下限 */
        bottomLimit: number,
        /** 鱼设置 */
        Fish: {
            /** 最小倍率 */
            rateMin: number,
            /** 最大倍率 */
            rateMax: number,
            /** 击杀倍率 */
            killRate: number,
            /** 出现概率(100) */
            appearRate: number,
            /** 出现频率（秒） */
            appearInterval: number
        }[],
        /** 奖池概率修正 */
        Fix: {
            /** 档位 */
            level: number,
            /** 下限 */
            bottom: number,
            /** 上限 */
            top: number,
            /** 修正值 */
            fix: number
        }[],
        /** 游戏名，不可更改 */
        game: string,
        /** 房间名，不可更改 */
        field: string,
        /** 入场分数下限，0不限 */
        minGold: number,
        /** 入场分数上限，0不限 */
        maxGold: number,
        /** 最小下注 */
        minBet: number
    }[],
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BGameSettings"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 设置扯旋 <a id="/game/SetCheXuan"></a>

**路径**
- POST `/game/SetCheXuan`

**请求**
```ts
interface ReqSetCheXuan {
    room: {
        /** 游戏名，不可更改 */
        game: string,
        /** 房间名，不可更改 */
        field: string,
        /** 入场分数下限，0不限 */
        minGold: number,
        /** 入场分数上限，0不限 */
        maxGold: number,
        /** 最小下注 */
        minBet: number
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResSetCheXuan {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "OGameSettings"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 设置五子棋 <a id="/game/SetFIR"></a>

只传递当前修改的配置

**路径**
- POST `/game/SetFIR`

**请求**
```ts
interface ReqSetFIR {
    room: {
        /** 游戏名，不可更改 */
        game: string,
        /** 房间名，不可更改 */
        field: string,
        /** 入场分数下限，0不限 */
        minGold: number,
        /** 入场分数上限，0不限 */
        maxGold: number,
        /** 最小下注 */
        minBet: number
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResSetFIR {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "OGameSettings"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 配置捕鱼 <a id="/game/SetFish"></a>

只传递当前修改的房间数据

**路径**
- POST `/game/SetFish`

**请求**
```ts
interface ReqSetFish {
    room: {
        /** 当前奖池金额 */
        currentPool: number,
        /** 注入抽水比例 */
        taxRate: number,
        /** 注入奖池比例 */
        poolRate: number,
        /** 奖池上限 */
        topLimit: number,
        /** 奖池下限 */
        bottomLimit: number,
        /** 鱼设置 */
        Fish: {
            /** 最小倍率 */
            rateMin: number,
            /** 最大倍率 */
            rateMax: number,
            /** 击杀倍率 */
            killRate: number,
            /** 出现概率(100) */
            appearRate: number,
            /** 出现频率（秒） */
            appearInterval: number
        }[],
        /** 奖池概率修正 */
        Fix: {
            /** 档位 */
            level: number,
            /** 下限 */
            bottom: number,
            /** 上限 */
            top: number,
            /** 修正值 */
            fix: number
        }[],
        /** 游戏名，不可更改 */
        game: string,
        /** 房间名，不可更改 */
        field: string,
        /** 入场分数下限，0不限 */
        minGold: number,
        /** 入场分数上限，0不限 */
        maxGold: number,
        /** 最小下注 */
        minBet: number
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResSetFish {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "OGameSettings"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

## player

### 获取玩家列表 <a id="/player/Get"></a>

**路径**
- POST `/player/Get`

**请求**
```ts
interface ReqGet {
    /** 筛选方式 */
    filter: {
        /** 玩家uid */
        UID?: number,
        /** 昵称或邮箱地址 */
        account?: string,
        /** 登录时间开始 */
        loginTimeStart?: /*datetime*/ string,
        /** 登录时间结束 */
        loginTimeEnd?: /*datetime*/ string
    },
    /**
    * 排序方式
    * 1升序
    * -1倒序
    */
    sort: { loginTime?: number },
    /** 请求分页 */
    page?: {
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGet {
    /** 返回分页 */
    page?: {
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    list: {
        /** 玩家id */
        UID: number,
        /** 昵称 */
        nickname: string,
        /** 邮箱地址 */
        email: string,
        /** 注册时间 */
        registerTime: /*datetime*/ string,
        /** 上次登录时间 */
        loginTime: /*datetime*/ string,
        /** 持有金币 */
        gold: number,
        /** 保险箱金币 */
        safeboxGold: number,
        /** 持有钻石 */
        gem: number,
        /** 保险箱钻石 */
        safeboxGem: number,
        /** 总充值 */
        totalCharge: number,
        /** 总输赢 */
        totalMatch: number,
        /** 游戏时长 */
        gameTime: number
    }[],
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BSearchPlayer"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 获取对局记录 <a id="/player/GetMatchLog"></a>

**路径**
- POST `/player/GetMatchLog`

**请求**
```ts
interface ReqGetMatchLog {
    filter: {
        UID: number,
        dateStart: /*datetime*/ string,
        dateEnd: /*datetime*/ string
    },
    /** 请求分页 */
    page: {
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetMatchLog {
    list: {
        /** 对局id */
        id: number,
        /** 玩家id */
        UID: number,
        /** 玩家昵称 */
        nickname: string,
        /** 开始时间 */
        startTime: /*datetime*/ string,
        /** 结束时间 */
        endTime: /*datetime*/ string,
        /** 游戏 */
        game: string,
        /** 房间 */
        room: string,
        /** 开始金额 */
        startGold: number,
        /** 结束金额 */
        endGold: number,
        /** 输赢结果 */
        result: number,
        /** 备注 */
        remark: string
    }[],
    /** 返回分页 */
    page: {
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BSearchPlayer"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 获取实时在线 <a id="/player/GetOnline"></a>

**路径**
- POST `/player/GetOnline`

**请求**
```ts
interface ReqGetOnline {
    filter: {
        dateStart: /*datetime*/ string,
        dateEnd: /*datetime*/ string,
        /** UID或nickname */
        account: string,
        /** 时间粒度，最低5秒 */
        stamp: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetOnline {
    games: {
        game: string,
        chart: [number, number][]
    }[],
    total: [number, number][],
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BOnlinePlayer"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 上分 <a id="/player/GoldOperate"></a>

**路径**
- POST `/player/GoldOperate`

**请求**
```ts
interface ReqGoldOperate {
    /** 玩家uid */
    UID: number,
    /** 增减持有金币 */
    gold: number,
    /** 增减保险箱金币 */
    safeboxGold: number,
    /** 操作类型，只能是赠送|充值|补偿 */
    operate: "Send" | "ChargeRefound" | "Compensate",
    /** 备注 */
    remark: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGoldOperate {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "OPlayerScore"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 锁定/解锁玩家 <a id="/player/Set"></a>

**路径**
- POST `/player/Set`

**请求**
```ts
interface ReqSet {
    UID: number[],
    lock: boolean,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResSet {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "OPlayerBlock"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

## rank

### 获取排名 <a id="/rank/Get"></a>

**路径**
- POST `/rank/Get`

**请求**
```ts
interface ReqGet {
    data: /*datetime*/ string,
    /** 请求分页 */
    page: {
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGet {
    list: any,
    /** 返回分页 */
    page: {
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BRanking"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

## store

### 获取商品列表 <a id="/store/Get"></a>

**路径**
- POST `/store/Get`

**请求**
```ts
interface ReqGet {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGet {
    list: {
        id: number,
        name: string,
        icon: string,
        price: number
    }[],
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BStore"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 设置商品列表，只传修改的字段 <a id="/store/Set"></a>

**路径**
- POST `/store/Set`

**请求**
```ts
interface ReqSet {
    list: {
        id: number,
        name: string,
        icon: string,
        price: number
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResSet {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "OStore"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

## system

### announce

#### 发送通知 <a id="/system/announce/Send"></a>

**路径**
- POST `/system/announce/Send`

**请求**
```ts
interface ReqSend {
    title: string,
    content: string,
    targetUID?: number[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResSend {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BSystem",
    "BAnnounce"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### config

#### 获取后台开关 <a id="/system/config/Get"></a>

**路径**
- POST `/system/config/Get`

**请求**
```ts
interface ReqGet {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGet {
    /** 总设置 */
    config: {
        /** 显示排行榜 */
        showRanking?: boolean,
        /** 开放的游戏 */
        openList?: string[],
        /** 关闭的游戏 */
        closeList?: string[]
    },
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BConfig"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 设置后台开关 <a id="/system/config/Set"></a>

**路径**
- POST `/system/config/Set`

**请求**
```ts
interface ReqSet {
    /** 总设置 */
    config: {
        /** 显示排行榜 */
        showRanking?: boolean,
        /** 开放的游戏 */
        openList?: string[],
        /** 关闭的游戏 */
        closeList?: string[]
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResSet {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BConfig"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

### 获取任意记录 <a id="/system/GetOperateLog"></a>

根据记录类型返回相应的字段

**路径**
- POST `/system/GetOperateLog`

**请求**
```ts
interface ReqGetOperateLog {
    filter: {
        /** 目标uid */
        UID?: number,
        /** 操作者uid */
        operator?: number,
        /** 开始时间 */
        dateStart?: number,
        /** 结束时间 */
        dateEnd?: number,
        /** 操作类型 */
        operate: "ChargeRefound" | "Send" | "Compensate" | "AddControl" | "RemoveControl" | "LockAccount" | "UnlockAccount" | "SendMarquee" | "SenAnnounce" | "SetGame" | "SetConfig"[]
    },
    /** 请求分页 */
    page: {
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGetOperateLog {
    /** 日志 */
    list: ({
        /** 记录id */
        id: number,
        /** 目标uid 空则为全体玩家 */
        UID: number[],
        /** 目标昵称 */
        nickname: string,
        /** 操作者uid */
        operatorUID: number,
        /** 操作者昵称 */
        operatorNickname: string,
        /** 操作者ip */
        ip: string,
        /** 操作时间 */
        date: /*datetime*/ string,
        /** 操作类型 */
        operate: "ChargeRefound" | "Send" | "Compensate" | "AddControl" | "RemoveControl" | "LockAccount" | "UnlockAccount" | "SendMarquee" | "SenAnnounce" | "SetGame" | "SetConfig",
        /** 备注 */
        remark: string
    } & {
        /** 金钱操作[ChargeRefound|Send|Compensate] */
        currency?: {
            /** 记录id,与operatelog的id相同 */
            id: number,
            /** 货币类型 */
            currency: "Gold" | "Gem",
            /** 起始值 */
            startValue: number,
            /** 结束值 */
            endValue: number,
            /** 变化值 */
            value: number
        },
        /** 点控[AddControl|RemoveControl] */
        control?: {
            /** 操作id */
            id: number,
            control: boolean,
            /** 分步 */
            step?: {
                /** 权重 */
                weight: number,
                /** 目标金额 */
                value: number
            }[]
        },
        /** 账号[LockAccount|UnlockAccount] */
        account?: {
            id: number,
            /** 是否锁定 */
            lock: boolean
        },
        /** 跑马灯[SendMarquee] */
        marquee?: {
            /** id */
            id: number,
            /** 内容 */
            content: string,
            /** 重复次数 */
            repeat: number,
            /** 重复间隔 */
            interval: number
        },
        /** 通知[SendAnnounce] */
        announce?: {
            /** 通知ID,与operateLog的id相同 */
            id?: number,
            title?: string,
            content?: string
        },
        /** 设置游戏记录[SetGame] */
        game?: {
            /** 操作记录id */
            id: number,
            /** 游戏名，不可更改 */
            game: string,
            /** 房间名，不可更改 */
            field: string,
            /** 入场分数下限，0不限 */
            minGold: number,
            /** 入场分数上限，0不限 */
            maxGold: number,
            /** 最小下注 */
            minBet: number
        } | {
            /** 操作记录id */
            id: number,
            /** 当前奖池金额 */
            currentPool: number,
            /** 注入抽水比例 */
            taxRate: number,
            /** 注入奖池比例 */
            poolRate: number,
            /** 奖池上限 */
            topLimit: number,
            /** 奖池下限 */
            bottomLimit: number,
            /** 鱼设置 */
            Fish: {
                /** 最小倍率 */
                rateMin: number,
                /** 最大倍率 */
                rateMax: number,
                /** 击杀倍率 */
                killRate: number,
                /** 出现概率(100) */
                appearRate: number,
                /** 出现频率（秒） */
                appearInterval: number
            }[],
            /** 奖池概率修正 */
            Fix: {
                /** 档位 */
                level: number,
                /** 下限 */
                bottom: number,
                /** 上限 */
                top: number,
                /** 修正值 */
                fix: number
            }[],
            /** 游戏名，不可更改 */
            game: string,
            /** 房间名，不可更改 */
            field: string,
            /** 入场分数下限，0不限 */
            minGold: number,
            /** 入场分数上限，0不限 */
            maxGold: number,
            /** 最小下注 */
            minBet: number
        } | {
            id: number,
            /** 游戏名，不可更改 */
            game: string,
            /** 房间名，不可更改 */
            field: string,
            /** 入场分数下限，0不限 */
            minGold: number,
            /** 入场分数上限，0不限 */
            maxGold: number,
            /** 最小下注 */
            minBet: number
        }
    })[],
    /** 返回分页 */
    page: {
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needEncrypt": true,
  "needServer": true
}
```

---

### 发送跑马灯 <a id="/system/SendMarquee"></a>

**路径**
- POST `/system/SendMarquee`

**请求**
```ts
interface ReqSendMarquee {
    /** 跑马灯内容 */
    content: string,
    /** 重复次数 */
    repeat: number,
    /** 发送间隔 */
    interval: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResSendMarquee {
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BMarquee"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

---

## verify

### 查询验证码 <a id="/verify/Get"></a>

**路径**
- POST `/verify/Get`

**请求**
```ts
interface ReqGet {
    filter: {
        /** 根据uid查询 */
        UID?: number,
        /** 根据email查询 */
        email?: string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 用户角色，仅服务器使用不需要填写 */
    __permissions?: "Server" | "Player" | "BAnnounce" | "BConfig" | "BManager" | "BSystem" | "BAnalyze" | "BRanking" | "BSearchPlayer" | "BOnlinePlayer" | "BStore" | "BControl" | "BScoreOperate" | "BGameLog" | "BGameSettings" | "BMarquee" | "BVerifyCode" | "OControl" | "OPlayerScore" | "OPlayerBlock" | "OGameSettings" | "OManager" | "OStore"[],
    /** 签名 */
    __sign?: string,
    /** 时间戳 */
    __timestamp?: number
}
```

**响应**
```ts
interface ResGet {
    /** 用户uid */
    UID: number,
    /** 发送邮箱 */
    address: string,
    /** 验证码 */
    code: number,
    /** 发送时间 */
    date: /*datetime*/ string,
    __authToken?: string
}
```

**配置**
```ts
{
  "needLogin": true,
  "needPermission": [
    "BVerifyCode"
  ],
  "needEncrypt": true,
  "needServer": true
}
```

