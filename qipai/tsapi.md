
# TSRPC API 接口文档

## 通用说明

- 所有请求方法均为 `POST`
- 所有请求均需加入以下 Header :
    - `Content-Type: application/json`

## 目录

- backend
    - agent
        - [获取代理列表](#/backend/agent/Get)
        - [设置代理](#/backend/agent/Modify)
    - analyze
        - [获取活跃人数](#/backend/analyze/GetActive)
        - [获取新增人数](#/backend/analyze/GetAdd)
        - [获取留存](#/backend/analyze/GetRetain)
        - [获取概要](#/backend/analyze/GetSummary)
    - game
        - [解散房间](#/backend/game/DisbandRoom)
        - [获取游戏设置](#/backend/game/GetGame)
        - [获取房间列表](#/backend/game/GetRoom)
        - [邀请玩家](#/backend/game/Invite)
        - [游戏规则设置](#/backend/game/SetGame)
        - [设置房间规则](#/backend/game/SetRoom)
    - player
        - [获取玩家列表](#/backend/player/Get)
        - [获取对局记录](#/backend/player/GetMatchLog)
        - [获取实时在线](#/backend/player/GetOnline)
        - [上分](#/backend/player/GoldOperate)
        - [锁定/解锁玩家](#/backend/player/Set)
    - rank
        - [获取排名](#/backend/rank/Get)
    - store
        - [获取商品列表](#/backend/store/Get)
        - [设置商品列表，只传修改的字段](#/backend/store/Set)
    - system
        - announce
            - [发送通知](#/backend/system/announce/Send)
        - config
            - [获取后台开关](#/backend/system/config/Get)
            - [设置后台开关](#/backend/system/config/Set)
        - currency
            - [通过兑换订单](#/backend/system/currency/ApplyExchange)
            - [获取充值记录](#/backend/system/currency/ChargeLog)
            - [获取兑换记录](#/backend/system/currency/GetExchangeLog)
            - [获取汇率](#/backend/system/currency/GetExchangeRate)
            - [设置汇率](#/backend/system/currency/SetExchangeRate)
        - [获取任意记录](#/backend/system/GetOperateLog)
        - [发送跑马灯](#/backend/system/SendMarquee)
        - [设置联系我们](#/backend/system/SetContactUs)
    - verify
        - [查询验证码](#/backend/verify/Get)
- [GetServers](#/GetServers)
- [RegisterServer](#/RegisterServer)
- [UnRegisterServer](#/UnRegisterServer)
- [UpdateNodeInfo](#/UpdateNodeInfo)

---

## backend

### agent

#### 获取代理列表 <a id="/backend/agent/Get"></a>

**路径**
- POST `/backend/agent/Get`

**请求**
```ts
interface ReqGet {
    /** 筛选方式 */
    filter: {
        /** 以玩家uid查询 */
        uid?: number[],
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
    sort?: { loginTime?: -1 | 1 },
    /** 请求分页 */
    page: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGet {
    list: {
        _id?: /*ObjectId*/ string,
        /** 团队金额 */
        groupGold?: number,
        /** 下属代理 */
        childAgent?: number[],
        /** 下属普通会员 */
        childPlayer?: number[],
        /** 团队盈亏 */
        groupResult?: number,
        /** 游戏总对局数 */
        groupMatchCount?: number,
        /** 抽水总金额 */
        groupTax?: number,
        /** 账号编号 */
        account_sn?: number,
        /** 用户uid */
        uid?: number,
        /** 是否锁定 */
        lock?: boolean,
        /** 昵称 */
        nickName?: string,
        /** 头像 */
        icon?: string,
        /** 是否是代理 */
        isAgent?: boolean,
        /** 邀请码 */
        invitationCode?: number,
        /** 代理邀请码 */
        agentInvitationCode?: number,
        /** 登录验证密钥 */
        authToken?: string,
        /** 游戏房间密钥 */
        roomToken?: string,
        /**
        * 当前游戏
        * 大厅
        * 牛牛
        * 十三水...
        */
        playingGame?: string,
        /** 锁定金币 */
        lockGold?: number,
        /** 金币 */
        gold?: number,
        /** 保险箱金币 */
        safeBoxGold?: number,
        /** 保险箱密码 */
        safeBoxPassword?: string,
        /** 登录时间 */
        loginTime?: /*datetime*/ string,
        /** 注册时间 */
        registerTime?: /*datetime*/ string,
        /** 总充值数 */
        totalCharge?: number,
        /** 总输赢情况 */
        totalMatchResult?: number,
        /** 当日输赢情况 */
        dailyMatchResult?: number,
        /** 赢钱次数 */
        winCount?: number,
        /** 输次数 */
        loseCount?: number,
        /** 游戏时长（秒） */
        gameTime?: number,
        /** 上级代理uid */
        parentAgentUID?: number,
        /** 返利 (0~1) */
        rebates?: number,
        /** 返利类型 */
        rebateType?: "Instant" | "Delay24Hours" | "Manual",
        /** 个人抽水金额 */
        tax?: number,
        /** 是否充值 */
        isPayed?: boolean
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 设置代理 <a id="/backend/agent/Modify"></a>

**路径**
- POST `/backend/agent/Modify`

**请求**
```ts
interface ReqModify {
    /** 玩家uid */
    uid: number,
    /** 返利0~100 */
    rebates: number,
    /** 是否是代理 */
    isAgent: boolean,
    /** 能否解散房间 */
    canDisbandRoom: boolean,
    /** 返利类型 */
    rebateType: "Instant" | "Delay24Hours" | "Manual",
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResModify {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

---

### analyze

#### 获取活跃人数 <a id="/backend/analyze/GetActive"></a>

**路径**
- POST `/backend/analyze/GetActive`

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
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetActive {
    /** 返回数据[...[dateNumber,value]...] */
    data: [string, number][],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 获取新增人数 <a id="/backend/analyze/GetAdd"></a>

**路径**
- POST `/backend/analyze/GetAdd`

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
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetAdd {
    /** 返回数据[...[dateNumber,value]...] */
    data: [string, number][],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 获取留存 <a id="/backend/analyze/GetRetain"></a>

**路径**
- POST `/backend/analyze/GetRetain`

**请求**
```ts
interface ReqGetRetain {
    filter: { date: /*datetime*/ string },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
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
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 获取概要 <a id="/backend/analyze/GetSummary"></a>

**路径**
- POST `/backend/analyze/GetSummary`

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
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
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
    /** 玩家总持有金币 */
    totalGold: number,
    /** 时间段内赠送的金币 */
    filteredSend: number,
    /** 游戏盈亏 */
    games: {
        /** 记录日期 */
        date: /*datetime*/ string | string,
        /** 名称 */
        name: string,
        /** 活跃玩家 */
        activePlayer: number,
        /** 新增玩家 */
        addPlayer: number,
        /** 玩家赢的次数 */
        playerWinCount: number,
        /** 游戏局数 */
        matchCount: number,
        /** 玩家胜率 */
        playerWinRate: number,
        /** 玩家输赢 */
        playerMatchResult: number,
        /** 系统抽水 */
        tax: number,
        /** 游戏输赢 */
        gameMatchResult: number,
        /** 机器人抽水 */
        botTax: number,
        /** 真人抽水 */
        realTax: number
    }[],
    /** 房间盈亏 */
    rooms: {
        /** 记录日期 */
        date: /*datetime*/ string | string,
        /** 名称 */
        name: string,
        /** 活跃玩家 */
        activePlayer: number,
        /** 新增玩家 */
        addPlayer: number,
        /** 玩家赢的次数 */
        playerWinCount: number,
        /** 游戏局数 */
        matchCount: number,
        /** 玩家胜率 */
        playerWinRate: number,
        /** 玩家输赢 */
        playerMatchResult: number,
        /** 系统抽水 */
        tax: number,
        /** 游戏输赢 */
        gameMatchResult: number,
        /** 机器人抽水 */
        botTax: number,
        /** 真人抽水 */
        realTax: number
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

### game

#### 解散房间 <a id="/backend/game/DisbandRoom"></a>

**路径**
- POST `/backend/game/DisbandRoom`

**请求**
```ts
interface ReqDisbandRoom {
    roomId: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResDisbandRoom {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

---

#### 获取游戏设置 <a id="/backend/game/GetGame"></a>

**路径**
- POST `/backend/game/GetGame`

**请求**
```ts
interface ReqGetGame {
    game: string,
    scene: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetGame {
    room: {
        /** 游戏名 */
        game: string,
        /** 游戏场次 */
        scene: string,
        /** 是否私有，只有服务器调用 */
        isPrivate?: boolean,
        /** 房间id，只有服务器调用 */
        roomId?: number,
        /** 节点链接，只有服务器调用 */
        url?: string,
        /** 抽水，只有服务器调用 */
        tax?: number,
        /** 房费，只有服务器调用 */
        fee?: number,
        /** 每局携带金额 */
        takeGold: number,
        /** 房主uid */
        masterUID: number,
        /** 密码 */
        password: string,
        /** 底注 */
        baseBet: number,
        /** 最低进入金额 */
        minGold: number,
        maxGold: number,
        /** 局数 */
        round: number,
        /** 最大回合数 */
        maxStep: number,
        /** 抢庄倍率 */
        hostBetRate: number[],
        /** 抽水方式 */
        taxRule: 0 | 1 | 2,
        /** 下注倍率 */
        betRate: number[],
        /** 允许观战 */
        enableWatch: boolean,
        minPlayerCount?: number,
        maxPlayerCount?: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 获取房间列表 <a id="/backend/game/GetRoom"></a>

**路径**
- POST `/backend/game/GetRoom`

**请求**
```ts
interface ReqGetRoom {
    filter: {
        /** 撞见日期 */
        date?: /*datetime*/ string,
        /** 房主uid */
        masterUID?: number,
        /** 游戏名 */
        game?: string
    },
    /** 请求分页 */
    page: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRoom {
    list: {
        /** 房间id */
        roomId: number,
        /** 游戏名 */
        game: string,
        /** 房主id */
        masterUID: number,
        /** 创建日期 */
        date: /*datetime*/ string,
        /** 房费 */
        fee: number,
        /** 抽水 */
        tax: number,
        /** 玩家id */
        playerId: number[],
        /** 当前局数 */
        round: number,
        /** 底分 */
        baseBet: number,
        /** 最大局数 */
        maxRound: number,
        /** 推注 */
        betRate: number[],
        /** 抢庄 */
        hostBet: number[],
        /** 抽水规则 */
        taxRule: 0 | 1 | 2,
        /** 允许观战 */
        enableWatch: boolean,
        /** 最低入场金额 */
        goldLimitMin: number,
        /** 最高入场金额 */
        goldLimitMax: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

---

#### 邀请玩家 <a id="/backend/game/Invite"></a>

**路径**
- POST `/backend/game/Invite`

**请求**
```ts
interface ReqInvite {
    /** 房间id */
    roomId: number,
    /** 邀请玩家id */
    uid: number[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResInvite {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

---

#### 游戏规则设置 <a id="/backend/game/SetGame"></a>

**路径**
- POST `/backend/game/SetGame`

**请求**
```ts
interface ReqSetGame {
    game: string,
    scene: string,
    room: {
        /** 游戏名 */
        game: string,
        /** 游戏场次 */
        scene: string,
        /** 是否私有，只有服务器调用 */
        isPrivate?: boolean,
        /** 房间id，只有服务器调用 */
        roomId?: number,
        /** 节点链接，只有服务器调用 */
        url?: string,
        /** 抽水，只有服务器调用 */
        tax?: number,
        /** 房费，只有服务器调用 */
        fee?: number,
        /** 每局携带金额 */
        takeGold: number,
        /** 房主uid */
        masterUID: number,
        /** 密码 */
        password: string,
        /** 底注 */
        baseBet: number,
        /** 最低进入金额 */
        minGold: number,
        maxGold: number,
        /** 局数 */
        round: number,
        /** 最大回合数 */
        maxStep: number,
        /** 抢庄倍率 */
        hostBetRate: number[],
        /** 抽水方式 */
        taxRule: 0 | 1 | 2,
        /** 下注倍率 */
        betRate: number[],
        /** 允许观战 */
        enableWatch: boolean,
        minPlayerCount?: number,
        maxPlayerCount?: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetGame {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 设置房间规则 <a id="/backend/game/SetRoom"></a>

**路径**
- POST `/backend/game/SetRoom`

**请求**
```ts
interface ReqSetRoom {
    /** 房间id */
    roomId: number,
    /** 底分 */
    baseBet: number,
    /** 最大局数 */
    maxRound: number,
    /** 最大推注 */
    maxBetRate: number,
    /** 最大抢庄 */
    maxHostBet: number,
    /** 抽水规则 */
    taxRule: 0 | 1 | 2,
    /** 允许观战 */
    enableWatch: boolean,
    /** 最低入场金额 */
    goldLimitMin: number,
    /** 最高入场金额 */
    goldLimitMax: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetRoom {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

---

### player

#### 获取玩家列表 <a id="/backend/player/Get"></a>

**路径**
- POST `/backend/player/Get`

**请求**
```ts
interface ReqGet {
    /** 筛选方式 */
    filter: {
        /** 以玩家uid查询 */
        UID?: number[],
        /** 昵称或邮箱地址 */
        account?: string,
        /** 登录时间开始 */
        loginTimeStart?: /*datetime*/ string,
        /** 登录时间结束 */
        loginTimeEnd?: /*datetime*/ string,
        /** 是否在线 */
        isOnline?: boolean
    },
    /**
    * 排序方式
    * 1升序
    * -1倒序
    */
    sort?: { loginTime?: -1 | 1 },
    /** 请求分页 */
    page: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGet {
    list: {
        _id?: /*ObjectId*/ string,
        /** 账号编号 */
        account_sn?: number,
        /** 用户uid */
        uid?: number,
        /** 是否锁定 */
        lock?: boolean,
        /** 昵称 */
        nickName?: string,
        /** 头像 */
        icon?: string,
        /** 是否是代理 */
        isAgent?: boolean,
        /** 邀请码 */
        invitationCode?: number,
        /** 代理邀请码 */
        agentInvitationCode?: number,
        /** 登录验证密钥 */
        authToken?: string,
        /** 游戏房间密钥 */
        roomToken?: string,
        /**
        * 当前游戏
        * 大厅
        * 牛牛
        * 十三水...
        */
        playingGame?: string,
        /** 锁定金币 */
        lockGold?: number,
        /** 金币 */
        gold?: number,
        /** 保险箱金币 */
        safeBoxGold?: number,
        /** 保险箱密码 */
        safeBoxPassword?: string,
        /** 登录时间 */
        loginTime?: /*datetime*/ string,
        /** 注册时间 */
        registerTime?: /*datetime*/ string,
        /** 总充值数 */
        totalCharge?: number,
        /** 总输赢情况 */
        totalMatchResult?: number,
        /** 当日输赢情况 */
        dailyMatchResult?: number,
        /** 赢钱次数 */
        winCount?: number,
        /** 输次数 */
        loseCount?: number,
        /** 游戏时长（秒） */
        gameTime?: number,
        /** 上级代理uid */
        parentAgentUID?: number,
        /** 返利 (0~1) */
        rebates?: number,
        /** 返利类型 */
        rebateType?: "Instant" | "Delay24Hours" | "Manual",
        /** 个人抽水金额 */
        tax?: number,
        /** 是否充值 */
        isPayed?: boolean
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 获取对局记录 <a id="/backend/player/GetMatchLog"></a>

**路径**
- POST `/backend/player/GetMatchLog`

**请求**
```ts
interface ReqGetMatchLog {
    filter: {
        /** 玩家uid */
        UID?: number,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string,
        /** 通过游戏筛选 */
        game?: string[]
    },
    /** 请求分页 */
    page: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetMatchLog {
    list: {
        /** 游戏名 */
        game: string,
        /** 场景 */
        scene: string,
        /** 消息序列 */
        messages: string,
        /** 战报结果 */
        result: {
            roundId: number,
            /** 对局结果计分 */
            result: {
                /** 用户uid */
                uid: number,
                /** 输赢 */
                score: number,
                /** 总分 */
                totalScore: number,
                /** 额外信息：牌型等 */
                ext?: string
            }[],
            /** 开始时玩家快照 */
            playerSnapshot: {
                uid: number,
                playerId: number,
                gold: number
            }[]
        }[],
        /** 日期 */
        date?: /*datetime*/ string,
        /** 房间选项 */
        options: {
            /** 游戏名 */
            game: string,
            /** 游戏场次 */
            scene: string,
            /** 是否私有，只有服务器调用 */
            isPrivate?: boolean,
            /** 房间id，只有服务器调用 */
            roomId?: number,
            /** 节点链接，只有服务器调用 */
            url?: string,
            /** 抽水，只有服务器调用 */
            tax?: number,
            /** 房费，只有服务器调用 */
            fee?: number,
            /** 每局携带金额 */
            takeGold: number,
            /** 房主uid */
            masterUID: number,
            /** 密码 */
            password: string,
            /** 底注 */
            baseBet: number,
            /** 最低进入金额 */
            minGold: number,
            maxGold: number,
            /** 局数 */
            round: number,
            /** 最大回合数 */
            maxStep: number,
            /** 抢庄倍率 */
            hostBetRate: number[],
            /** 抽水方式 */
            taxRule: 0 | 1 | 2,
            /** 下注倍率 */
            betRate: number[],
            /** 允许观战 */
            enableWatch: boolean,
            minPlayerCount?: number,
            maxPlayerCount?: number
        },
        /** 所有玩家信息 */
        playerInfo?: {
            uid: number,
            nickName: string,
            icon: string,
            totalScore: number
        }[]
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    /** 玩家赢局数 */
    playerWin: number,
    /** 玩家输局数 */
    playerLose: number,
    /** 输赢总和 */
    resultSum: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 获取实时在线 <a id="/backend/player/GetOnline"></a>

**路径**
- POST `/backend/player/GetOnline`

**请求**
```ts
interface ReqGetOnline {
    filter: {
        dateStart: /*datetime*/ string,
        dateEnd: /*datetime*/ string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetOnline {
    games: {
        game: string,
        chart: [string, number][]
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 上分 <a id="/backend/player/GoldOperate"></a>

**路径**
- POST `/backend/player/GoldOperate`

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
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGoldOperate {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 锁定/解锁玩家 <a id="/backend/player/Set"></a>

**路径**
- POST `/backend/player/Set`

**请求**
```ts
interface ReqSet {
    UID: number[],
    lock: boolean,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSet {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

### rank

#### 获取排名 <a id="/backend/rank/Get"></a>

**路径**
- POST `/backend/rank/Get`

**请求**
```ts
interface ReqGet {
    filter: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 排序方式 */
        sort?: {
            /** 以输赢结果排序1，-1 */
            result?: -1 | 1,
            /** 持有金币 */
            gold?: -1 | 1,
            /** 持有钻石 */
            gem?: -1 | 1,
            /** 保险箱金币 */
            safeboxGold?: -1 | 1,
            /** 保险箱钻石 */
            safeboxGem?: -1 | 1
        }
    },
    /** 请求分页 */
    page: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGet {
    /** 输赢条目 */
    list: {
        /** 记录日期 */
        date: /*datetime*/ string | string,
        /** 用户id */
        UID?: number,
        /** 昵称 */
        nickname?: string,
        /** 背包内金币 */
        gold?: number,
        /** 背包内钻石 */
        gem?: number,
        /** 保险箱内金币 */
        safeboxGold?: number,
        /** 保险箱内钻石 */
        safeboxGem?: number,
        /** 输赢情况 */
        result?: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

### store

#### 获取商品列表 <a id="/backend/store/Get"></a>

**路径**
- POST `/backend/store/Get`

**请求**
```ts
interface ReqGet {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGet {
    list: {
        _id?: /*ObjectId*/ string,
        /** 商品id */
        id?: number,
        /** 道具id */
        itemId?: number,
        /** 名称 */
        name?: string,
        /** 描述 */
        desc?: string,
        /** 描述 */
        icon?: string,
        /** 价格 */
        price?: number,
        /** 折扣 */
        discount?: number
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 设置商品列表，只传修改的字段 <a id="/backend/store/Set"></a>

**路径**
- POST `/backend/store/Set`

**请求**
```ts
interface ReqSet {
    list: {
        /** 商品id */
        id: number,
        /** 道具id */
        itemId: number,
        /** 名称 */
        name?: string,
        /** 描述 */
        desc?: string,
        /** 描述 */
        icon?: string,
        /** 价格 */
        price: number,
        /** 折扣 */
        discount: number
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSet {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

### system

#### 获取任意记录 <a id="/backend/system/GetOperateLog"></a>

根据记录类型返回相应的字段

**路径**
- POST `/backend/system/GetOperateLog`

**请求**
```ts
interface ReqGetOperateLog {
    filter: {
        /** 目标uid */
        UID?: number,
        /** 操作者uid */
        operator?: number,
        /** 开始时间 */
        dateStart?: /*datetime*/ string,
        /** 结束时间 */
        dateEnd?: /*datetime*/ string,
        /** 操作类型 */
        operate: "ChargeRefound" | "Send" | "Compensate" | "Rebate" | "LockAccount" | "UnlockAccount" | "SendMarquee" | "SenAnnounce" | "SetGame" | "SetConfig"[],
        /** 返利相关 */
        rebate?: {
            /** 返利类型 */
            type: "Instant" | "Delay24Hours" | "Manual",
            /** 返利状态 */
            state: 0 | 1
        }
    },
    /** 请求分页 */
    page: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetOperateLog {
    /** 日志 */
    list: ({
        /** 日期 */
        date?: /*datetime*/ string | string,
        /** 记录id */
        id: number,
        /** 目标uid 空则为全体玩家 */
        targetUID?: number,
        /** 目标昵称 */
        nickname: string,
        /** 操作者uid */
        operatorUID: number,
        /** 操作者昵称 */
        operatorNickname: string,
        /** 操作者ip */
        ip: string,
        /** 操作类型 */
        operate: "ChargeRefound" | "Send" | "Compensate" | "Rebate" | "LockAccount" | "UnlockAccount" | "SendMarquee" | "SenAnnounce" | "SetGame" | "SetConfig",
        /** 备注 */
        remark: string
    } & {
        /** 金钱操作[ChargeRefound|Send|Compensate] */
        currency?: {
            /** 日期 */
            date?: /*datetime*/ string,
            /** 目标uid */
            uid: number,
            /** 货币类型 */
            currency: "Gold" | "Gem",
            /** 起始值 */
            startValue: number,
            /** 结束值 */
            endValue: number,
            /** 变化值 */
            value: number,
            /** 使用场景 */
            scene: 0 | 1 | 2 | 3 | 4 | 5,
            /** 备注 */
            notes?: string
        },
        /** 账号[LockAccount|UnlockAccount] */
        user?: {
            /** 日期 */
            date: /*datetime*/ string,
            /** 目标uid */
            uid?: number,
            /** 是否锁定 */
            lock: boolean
        },
        /** 跑马灯[SendMarquee] */
        marquee?: {
            /** 优先级 */
            Priority?: number,
            /** 日期 */
            Date?: number,
            /** 内容 */
            content: string,
            /** 重复次数 */
            repeat: number,
            /** 重复间隔 */
            interval: number
        },
        /** 通知[SendAnnounce] */
        announce?: {
            targetUID: number[],
            /** 日期 */
            date: /*datetime*/ string,
            /** 标题 */
            title: string,
            /** 内容 */
            content: string
        },
        /** 设置游戏记录[SetGame] */
        game?: {
            /** 游戏名 */
            game: string,
            /** 游戏场次 */
            scene: string,
            /** 是否私有，只有服务器调用 */
            isPrivate?: boolean,
            /** 房间id，只有服务器调用 */
            roomId?: number,
            /** 节点链接，只有服务器调用 */
            url?: string,
            /** 抽水，只有服务器调用 */
            tax?: number,
            /** 房费，只有服务器调用 */
            fee?: number,
            /** 每局携带金额 */
            takeGold: number,
            /** 房主uid */
            masterUID: number,
            /** 密码 */
            password: string,
            /** 底注 */
            baseBet: number,
            /** 最低进入金额 */
            minGold: number,
            maxGold: number,
            /** 局数 */
            round: number,
            /** 最大回合数 */
            maxStep: number,
            /** 抢庄倍率 */
            hostBetRate: number[],
            /** 抽水方式 */
            taxRule: 0 | 1 | 2,
            /** 下注倍率 */
            betRate: number[],
            /** 允许观战 */
            enableWatch: boolean,
            minPlayerCount?: number,
            maxPlayerCount?: number
        },
        /** 设置运营记录[SetConfig] */
        config?: {
            /** 显示排行榜 */
            showRanking?: boolean,
            /** 开放的游戏 */
            openList?: string[],
            /** 关闭的游戏 */
            closeList?: string[]
        },
        /** 返利记录 */
        rebate?: {
            /** 玩家uid */
            UID: number,
            /** 昵称 */
            nickName: string,
            /** 操作时间 */
            date: /*datetime*/ string | string,
            /** 金额 */
            gold: number,
            /** 游戏 */
            game: string,
            /** 返利类型 */
            type: "Instant" | "Delay24Hours" | "Manual",
            /** 返利状态 */
            state: 0 | 1
        }
    })[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 发送跑马灯 <a id="/backend/system/SendMarquee"></a>

**路径**
- POST `/backend/system/SendMarquee`

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
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSendMarquee {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 设置联系我们 <a id="/backend/system/SetContactUs"></a>

**路径**
- POST `/backend/system/SetContactUs`

**请求**
```ts
interface ReqSetContactUs {
    content: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetContactUs {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

### system/announce

#### 发送通知 <a id="/backend/system/announce/Send"></a>

**路径**
- POST `/backend/system/announce/Send`

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
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSend {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

### system/config

#### 获取后台开关 <a id="/backend/system/config/Get"></a>

**路径**
- POST `/backend/system/config/Get`

**请求**
```ts
interface ReqGet {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
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
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 设置后台开关 <a id="/backend/system/config/Set"></a>

**路径**
- POST `/backend/system/config/Set`

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
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSet {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

### system/currency

#### 通过兑换订单 <a id="/backend/system/currency/ApplyExchange"></a>

**路径**
- POST `/backend/system/currency/ApplyExchange`

**请求**
```ts
interface ReqApplyExchange {
    /** 订单id */
    orderId: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResApplyExchange {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

---

#### 获取充值记录 <a id="/backend/system/currency/ChargeLog"></a>

**路径**
- POST `/backend/system/currency/ChargeLog`

**请求**
```ts
interface ReqChargeLog {
    filter: {
        /** 开始时间 */
        startTime: /*datetime*/ string,
        /** 结束时间 */
        endTime: /*datetime*/ string,
        /** 玩家uid */
        uid?: number,
        /** 订单号 */
        orderId?: string
    },
    /** 页面参数 */
    page: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResChargeLog {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 订单id */
        orderId: string,
        /** 商品名 */
        commodityName: string,
        /** 商品id */
        commodityId: string,
        /** 数量 */
        count: number,
        /** 支付金额 */
        pay: number,
        /** 玩家uid */
        uid: number,
        /** 昵称 */
        nickName: string
    },
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 获取兑换记录 <a id="/backend/system/currency/GetExchangeLog"></a>

**路径**
- POST `/backend/system/currency/GetExchangeLog`

**请求**
```ts
interface ReqGetExchangeLog {
    filter: {
        /** 开始时间 */
        startTime: /*datetime*/ string,
        /** 结束时间 */
        endTime: /*datetime*/ string,
        /** 玩家uid */
        uid?: number,
        /** 订单号 */
        orderId?: string
    },
    /** 请求分页 */
    page: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetExchangeLog {
    list: {
        orderId: string,
        /** 玩家uid */
        uid: number,
        /** 昵称 */
        nickName: string,
        /** 日期 */
        date: /*datetime*/ string,
        /** 金额 */
        gold: number,
        /** 等价的usd */
        usd: number,
        /** 汇率 */
        rate: number,
        /** 钱包地址 */
        walletAddress: string,
        /** 交易地址 */
        transactionAddress: string,
        /** 状态：通过|未通过 */
        state: "passed" | "pending"
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

---

#### 获取汇率 <a id="/backend/system/currency/GetExchangeRate"></a>

**路径**
- POST `/backend/system/currency/GetExchangeRate`

**请求**
```ts
interface ReqGetExchangeRate {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetExchangeRate {
    /** 渠道 */
    channels: {
        /** 渠道名 */
        id: string,
        /** 1u=金币数 */
        rate: number,
        /** 开关 */
        open: boolean
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

#### 设置汇率 <a id="/backend/system/currency/SetExchangeRate"></a>

**路径**
- POST `/backend/system/currency/SetExchangeRate`

**请求**
```ts
interface ReqSetExchangeRate {
    /** 渠道名 */
    id: string,
    /** 1u=金币数 */
    rate: number,
    /** 开关 */
    open: boolean,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetExchangeRate {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

### verify

#### 查询验证码 <a id="/backend/verify/Get"></a>

**路径**
- POST `/backend/verify/Get`

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
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGet {
    /** 用户uid */
    UID?: number,
    /** 发送邮箱 */
    address?: string,
    /** 验证码 */
    code: string,
    /** 发送时间 */
    date: /*datetime*/ string | string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needEncrypt": true,
  "needServer": true
}
```

---

## GetServers <a id="/GetServers"></a>

**路径**
- POST `/GetServers`

**请求**
```ts
interface ReqGetServers {
    app?: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetServers {
    list: {
        app: string,
        url: string,
        connectionCount: number
    }[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needServer": true
}
```

---

## RegisterServer <a id="/RegisterServer"></a>

**路径**
- POST `/RegisterServer`

**请求**
```ts
interface ReqRegisterServer {
    app: string,
    url: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResRegisterServer {
    serverId: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needServer": true
}
```

---

## UnRegisterServer <a id="/UnRegisterServer"></a>

**路径**
- POST `/UnRegisterServer`

**请求**
```ts
interface ReqUnRegisterServer {
    serverId: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResUnRegisterServer {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

**配置**
```ts
{
  "needServer": true
}
```

---

## UpdateNodeInfo <a id="/UpdateNodeInfo"></a>

**路径**
- POST `/UpdateNodeInfo`

**请求**
```ts
interface ReqUpdateNodeInfo {
    serverId: number,
    connectionCount: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户uid，仅服务器使用不需要填写 */
    __uid?: number,
    /** 昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResUpdateNodeInfo {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string
}
```

