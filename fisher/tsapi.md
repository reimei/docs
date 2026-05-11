
# TSRPC API 接口文档

## 通用说明

- 所有请求方法均为 `POST`
- 所有请求均需加入以下 Header :
    - `Content-Type: application/json`

## 目录

- data
    - [获取背包道具总计](#/data/GetBackCount)
    - [获取救济金](#/data/GetBenefits)
    - [获取爆发记录](#/data/GetBoomLogs)
    - [获取爆发统计](#/data/GetBoomStat)
    - [获取玩家爆发值](#/data/GetBoomValue)
    - [获取弹头消耗](#/data/GetBulletConsume)
    - [获取货币统计](#/data/GetCurrencyCount)
    - [获取玩家分布](#/data/GetDistribution)
    - [获取鱼雷奖金统计](#/data/GetFishBonusCount)
    - [获取鱼雷排行榜](#/data/GetFishChars)
    - [获取渔场输赢](#/data/GetFishWin)
    - [获取礼包兑换](#/data/GetGiftExchange)
    - [获取礼包概况](#/data/GetGiftSummary)
    - [获取积分信息](#/data/GetIntegral)
    - [获取积分统计](#/data/GetIntegralCount)
    - [获取登录日志](#/data/GetLoginLog)
    - [获取嘉年华数据监控](#/data/GetMiniGameHappy)
    - [获取水浒数据监控](#/data/GetMiniGameShuiHu)
    - [获取在线人数](#/data/GetOnline)
    - [获取商城购买](#/data/GetPaid)
    - [获取小游戏输赢](#/data/GetPlayWin)
    - [获取玩家信息](#/data/GetPlayers)
    - [获取赠送记录](#/data/GetPresentLogs)
    - [获取道具消耗](#/data/GetPropConsume)
    - [获取道具购买](#/data/GetPropPurchaseLogs)
    - [获取充值明细](#/data/GetRecharges)
    - [获取iOS充值明细](#/data/GetRechargesIOS)
    - [获取充值统计](#/data/GetRechargesMore)
    - [获取模拟充值明细](#/data/GetRechargesSimu)
    - [获取资源日志](#/data/GetResLog)
    - [获取背包资源信息](#/data/GetResources)
    - [获取仓库存取日志](#/data/GetSafeLog)
    - [获取仓库资源信息](#/data/GetSafeResources)
    - [获取仓库道具总计](#/data/GetStoreCount)
    - [获取金币统计](#/data/GoldCount)
    - [获取核心用户统计](#/data/Vips)
- game
    - [获取绑定解绑账号](#/game/GetBindSdkId)
    - [获取公告发送列表](#/game/GetBulletinList)
    - [获取已发送公告列表](#/game/GetBulletins)
    - [获取兑换码总览](#/game/GetDhmzl)
    - [获取邮件申请列表](#/game/GetEmailApplyList)
    - [获取兑换管理](#/game/GetExchange)
    - [获取兑换记录](#/game/GetExchangeRecord)
    - [获取清理鱼雷](#/game/GetFlushFish)
    - [获取封号](#/game/GetFroze)
    - [获取踢人](#/game/GetKickOut)
    - [获取邮件审核列表](#/game/GetMailAudit)
    - [获取刷新配置](#/game/GetRefreshConfig)
    - [获取充值账号密码](#/game/GetResetPassword)
    - [获取重置赠送密码](#/game/GetResetPresentPassword)
    - [获取SDK角色](#/game/GetSdkRole)
    - [获取设置角色类型](#/game/GetSetRole)
    - [获取屏蔽兑换码](#/game/GetShieldExchange)
    - [获取屏蔽兑换道具](#/game/GetShieldExchangeProp)
    - [获取屏蔽充值](#/game/GetShieldPay)
    - [获取屏蔽赠送](#/game/GetShieldPresent)
    - [获取禁言](#/game/GetShieldSpeak)
    - [获取系统入口开关设置](#/game/GetSysEntry)
    - [修改绑定解绑账号](#/game/SetBindSdkId)
    - [操作发送列表](#/game/SetBulletinList)
    - [设置已发送公告状态](#/game/SetBulletins)
    - [sdkid角色渠道设置](#/game/SetChannel)
    - [兑换码生成](#/game/SetDhmsc)
    - [邮件申请](#/game/SetEmailApply)
    - [推广号设置](#/game/SetExtend)
    - [模拟充值](#/game/SetFishRecharge)
    - [清理鱼雷](#/game/SetFlushFish)
    - [封号](#/game/SetFroze)
    - [踢人](#/game/SetKickOut)
    - [邮件审核](#/game/SetMailAudit)
    - [刷新配置](#/game/SetRefreshConfig)
    - [重置账号密码](#/game/SetResetPassword)
    - [重置账号密码](#/game/SetResetPresentPassword)
    - [重置仓库密码](#/game/SetResetSafePwd)
    - [重置SDK密码（账号密码）](#/game/SetResetSdkPwd)
    - [设置SDK类型](#/game/SetSdkRole)
    - [发布公告](#/game/SetSendBulletin)
    - [设置角色类型](#/game/SetSetRole)
    - [屏蔽兑换码](#/game/SetShieldExchange)
    - [屏蔽兑换道具](#/game/SetShieldExchangeProp)
    - [屏蔽充值](#/game/SetShieldPay)
    - [屏蔽赠送](#/game/SetShieldPresent)
    - [屏蔽发言](#/game/SetShieldSpeak)
    - [系统入口开关设置](#/game/SetSysEntry)
- player
    - [获取经验值排行榜](#/player/GetRankExp)
    - [获取金币排行榜](#/player/GetRankGold)
    - [获取魔力排行榜](#/player/GetRankMagic)
    - [获取充值排行榜](#/player/GetRankRecharge)
    - [获取钻石排行榜](#/player/GetRankRing)
    - [获取鱼雷排行榜](#/player/GetRankTorpedo)
    - [获取vip排行榜](#/player/GetRankVIP)
- [获取总数据](#/TotalData)

---

## data

### 获取背包道具总计 <a id="/data/GetBackCount"></a>

**路径**
- POST `/data/GetBackCount`

**请求**
```ts
interface ReqGetBackCount {
    filter?: {
        /** 开始日期 */
        startDate?: /*datetime*/ string,
        /** 结束日期 */
        endDate?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetBackCount {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 奖券 */
        ticket: number,
        /** 钻石包 */
        gemPack: number,
        /** 号角 */
        horn: number,
        /** 锁定 */
        lockon: number,
        /** 冰冻 */
        freeze: number,
        /** 狂暴 */
        rage: number,
        /** 神灯 */
        lamp: number,
        /** 青铜弹头 */
        bronzeTorpedo: number,
        /** 白银弹头 */
        silverTorpedo: number,
        /** 黄金弹头 */
        goldTorpedo: number,
        /** 白金弹头 */
        platinumTorpedo: number,
        /** 金刚石 */
        diamond: number,
        /** 宝石 */
        ruby: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取救济金 <a id="/data/GetBenefits"></a>

**路径**
- POST `/data/GetBenefits`

**请求**
```ts
interface ReqGetBenefits {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetBenefits {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** 昵称 */
        nickname: string,
        /** 剩余救济金 */
        remainingBenefits: number,
        /** 今日消耗救济金 */
        consumedBenefitsToday: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取爆发记录 <a id="/data/GetBoomLogs"></a>

**路径**
- POST `/data/GetBoomLogs`

**请求**
```ts
interface ReqGetBoomLogs {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetBoomLogs {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** vip等级 */
        vipLevel: number,
        /** 充值总额 */
        totalRecharge: number,
        /** 炮台等级 */
        cannonLevel: number,
        /** 计费点 */
        commodityId: number,
        /** 计费点金额 */
        commodityAmount: number,
        /** 爆发倍数 */
        boomMultiplier: number,
        /** 总爆发次数 */
        totalBoomCount: number,
        /** 时间 */
        date: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取爆发统计 <a id="/data/GetBoomStat"></a>

**路径**
- POST `/data/GetBoomStat`

**请求**
```ts
interface ReqGetBoomStat {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetBoomStat {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 日期 */
        date: /*datetime*/ string,
        /** 付费用户数 */
        payingUsers: number,
        /** 付费次数 */
        payingTimes: number,
        /** 充值爆发次数 */
        rechargeBoomTimes: number,
        /** 付费总额 */
        totalPayment: number,
        /** 爆发总额（万） */
        totalBoomAmount: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取玩家爆发值 <a id="/data/GetBoomValue"></a>

**路径**
- POST `/data/GetBoomValue`

**请求**
```ts
interface ReqGetBoomValue {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetBoomValue {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家ID */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** 打鱼爆发值 */
        fishingBoomValue: number,
        /** 水浒爆发值 */
        shuihuBoomValue: number,
        /** 嘉年华爆发值 */
        carnivalBoomValue: number,
        /** 打boss爆发值 */
        bossBoomValue: number,
        /** 通用爆发值 */
        commonBoomValue: number,
        /** 历史总爆发值 */
        totalBoomValue: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取弹头消耗 <a id="/data/GetBulletConsume"></a>

**路径**
- POST `/data/GetBulletConsume`

**请求**
```ts
interface ReqGetBulletConsume {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetBulletConsume {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 日期 */
        date: /*datetime*/ string,
        /** 青铜总数 */
        bronzeAmount: number,
        /** 白银总数 */
        silverAmount: number,
        /** 黄金总数 */
        goldAmount: number,
        /** 白金总数 */
        platinumAmount: number,
        /** 每日产出青铜 */
        bronzeDailyAmount: number,
        /** 每日消耗青铜 */
        bronzeDailyConsume: number,
        /** 每日产出白银 */
        silverDailyAmount: number,
        /** 每日消耗白银 */
        silverDailyConsume: number,
        /** 每日产出黄金 */
        goldDailyAmount: number,
        /** 每日消耗黄金 */
        goldDailyConsume: number,
        /** 每日产出白金 */
        platinumDailyAmount: number,
        /** 每日消耗白金 */
        platinumDailyConsume: number,
        /** 赠送青铜数量 */
        bronzeGiftAmount: number,
        /** 赠送白银数量 */
        silverGiftAmount: number,
        /** 赠送黄金数量 */
        goldGiftAmount: number,
        /** 赠送白金数量 */
        platinumGiftAmount: number,
        /** 储存数量 */
        stockAmount: number,
        /** 核心用户数量 */
        vipPlayerCount: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取货币统计 <a id="/data/GetCurrencyCount"></a>

**路径**
- POST `/data/GetCurrencyCount`

**请求**
```ts
interface ReqGetCurrencyCount {
    filter?: {
        /** 开始日期 */
        startDate?: /*datetime*/ string,
        /** 结束日期 */
        endDate?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetCurrencyCount {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 钻石 */
        gem: number,
        /** 金币 */
        coin: number,
        /** 魔力 */
        magic: number,
        /** 鱼币 */
        fishCoin: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取玩家分布 <a id="/data/GetDistribution"></a>

**路径**
- POST `/data/GetDistribution`

**请求**
```ts
interface ReqGetDistribution {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /**
        * 分布类型
        * 1：等级分布
        * 2：炮倍分布
        * 3：VIP等级分布
        */
        type?: 1 | 2 | 3
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetDistribution {
    /** 分布类型对应的key值列表，顺序与分布数据中的数量顺序一致 */
    keys: string[],
    /** 分布数据 */
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 分布数据，key为分布类型对应的值，value为数量 */
        distribution: number[]
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取鱼雷奖金统计 <a id="/data/GetFishBonusCount"></a>

**路径**
- POST `/data/GetFishBonusCount`

**请求**
```ts
interface ReqGetFishBonusCount {
    filter?: {
        /** 开始日期 */
        startDate?: /*datetime*/ string,
        /** 结束日期 */
        endDate?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetFishBonusCount {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 剩余鱼雷奖金 */
        remainingFishBonus: number,
        /** 昨天炸鱼雷数量 */
        explodedFishBonusYesterday: number,
        /** 今天炸鱼雷数量 */
        explodedFishBonusToday: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取鱼雷排行榜 <a id="/data/GetFishChars"></a>

**路径**
- POST `/data/GetFishChars`

**请求**
```ts
interface ReqGetFishChars {
    filter?: { date?: /*datetime*/ string },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetFishChars {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 排名 */
        rank: number,
        /** 账号 */
        playerName: string,
        /** 昵称 */
        nickname: string,
        /** vip等级 */
        vipLevel: number,
        /** 青铜鱼雷数 */
        bronzeTorpedo: number,
        /** 白银鱼雷数 */
        silverTorpedo: number,
        /** 黄金鱼雷数 */
        goldTorpedo: number,
        /** 白金鱼雷数 */
        platinumTorpedo: number,
        /** 鱼雷总价值 */
        totalTorpedoValue: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取渔场输赢 <a id="/data/GetFishWin"></a>

**路径**
- POST `/data/GetFishWin`

**请求**
```ts
interface ReqGetFishWin {
    filter?: {
        /** 账号 */
        accountName?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetFishWin {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 账号 */
        accountName: string,
        /** 昵称 */
        nickname: string,
        /** 消耗金币 */
        consumedCoins: number,
        /** 赢得金币 */
        wonCoins: number,
        /** 赢得青铜鱼雷 */
        wonBronzeTorpedo: number,
        /** 赢得白银鱼雷 */
        wonSilverTorpedo: number,
        /** 赢得黄金鱼雷 */
        wonGoldTorpedo: number,
        /** 赢得白金鱼雷 */
        wonPlatinumTorpedo: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取礼包兑换 <a id="/data/GetGiftExchange"></a>

**路径**
- POST `/data/GetGiftExchange`

**请求**
```ts
interface ReqGetGiftExchange {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        playerName?: string,
        /** 礼包码 */
        giftCode?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetGiftExchange {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        playerName: string,
        /** 设备id */
        deviceId: string,
        /** 礼包码 */
        giftCode: string,
        /** 礼包id */
        giftId: number,
        /** 礼包类型 */
        giftType: number,
        /** 礼包内容 */
        giftContent: string,
        /** 兑换时间 */
        exchangeTime: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取礼包概况 <a id="/data/GetGiftSummary"></a>

**路径**
- POST `/data/GetGiftSummary`

**请求**
```ts
interface ReqGetGiftSummary {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 礼包ID */
        giftId?: number
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetGiftSummary {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 礼包ID */
        giftId: number,
        /** 礼包码类型 */
        giftType: string,
        /** 礼包内容 */
        giftContent: string,
        /** 总数 */
        totalCount: number,
        /** 使用数量 */
        usedCount: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取积分信息 <a id="/data/GetIntegral"></a>

**路径**
- POST `/data/GetIntegral`

**请求**
```ts
interface ReqGetIntegral {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 上级SDKID */
        parentAccountID?: number,
        /** 下级SDKID */
        childAccountID?: number
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetIntegral {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 上级SDKID */
        parentAccountID: number,
        /** 下级SDKID */
        childAccountID: number,
        /** 下级积分数 */
        childIntegral: number,
        /** 下级金币数 */
        childGold: number,
        /** 下级消耗金币余数 */
        childGoldConsumed: number,
        /** 上级当前总积分 */
        parentIntegral: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取积分统计 <a id="/data/GetIntegralCount"></a>

**路径**
- POST `/data/GetIntegralCount`

**请求**
```ts
interface ReqGetIntegralCount {
    filter?: {
        /** 开始日期 */
        startDate?: /*datetime*/ string,
        /** 结束日期 */
        endDate?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetIntegralCount {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 历史积分 */
        historicalIntegral: number,
        /** 当前积分 */
        currentIntegral: number,
        /** 消耗积分 */
        consumedIntegral: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取登录日志 <a id="/data/GetLoginLog"></a>

**路径**
- POST `/data/GetLoginLog`

**请求**
```ts
interface ReqGetLoginLog {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /** IP */
        ip?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetLoginLog {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** 昵称 */
        nickname: string,
        /** IP */
        ip: string,
        /** 登录时间 */
        loginTime: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取嘉年华数据监控 <a id="/data/GetMiniGameHappy"></a>

**路径**
- POST `/data/GetMiniGameHappy`

**请求**
```ts
interface ReqGetMiniGameHappy {
    filter?: {/** 用户id */
        playerId?: number
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetMiniGameHappy {
    list: {
        /** 用户id */
        playerId: number,
        /** 猜牌总押注 */
        totalBet: number,
        /** 猜牌总赢取 */
        totalWin: number,
        /** 猜大小总押注 */
        totalBigSmallBet: number,
        /** 猜大小总赢取 */
        totalBigSmallWin: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取水浒数据监控 <a id="/data/GetMiniGameShuiHu"></a>

**路径**
- POST `/data/GetMiniGameShuiHu`

**请求**
```ts
interface ReqGetMiniGameShuiHu {
    filter?: {/** 用户id */
        playerId?: number
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetMiniGameShuiHu {
    list: {
        /** 用户id */
        playerId: number,
        /** 当天输赢 */
        dailyWinLoss: number,
        /** 总押注 */
        totalBet: number,
        /** 押注输赢 */
        betWinLoss: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取在线人数 <a id="/data/GetOnline"></a>

**路径**
- POST `/data/GetOnline`

**请求**
```ts
interface ReqGetOnline {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
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
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 最大在线人数 */
        onlineCount: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取商城购买 <a id="/data/GetPaid"></a>

**路径**
- POST `/data/GetPaid`

**请求**
```ts
interface ReqGetPaid {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetPaid {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 商品id */
        commodityId: number,
        /** 商品名称 */
        commodityName: string,
        /** 购买数量 */
        amount: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取小游戏输赢 <a id="/data/GetPlayWin"></a>

**路径**
- POST `/data/GetPlayWin`

**请求**
```ts
interface ReqGetPlayWin {
    filter?: {
        /** 账号 */
        accountName?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetPlayWin {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 账号 */
        accountName: string,
        /** 昵称 */
        nickname: string,
        /** 牛牛输赢 */
        niuNiuWin: number,
        /** 嘉年华输赢 */
        carnivalWin: number,
        /** 德州扑克输赢 */
        pokerWin: number,
        /** 水浒输赢 */
        shuiHuWin: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取玩家信息 <a id="/data/GetPlayers"></a>

**路径**
- POST `/data/GetPlayers`

**请求**
```ts
interface ReqGetPlayers {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /** SDKID */
        accountID?: number,
        /** VIP等级 */
        vipLevel?: number,
        /** 工会号 */
        agentId?: number
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetPlayers {
    list: {
        /** 账号 */
        playerName: string,
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** SDKID */
        accountID: number,
        /** 昵称 */
        nickname: string,
        /** 等级 */
        level: number,
        /** VIP等级 */
        vipLevel: number,
        /** 角色经验 */
        experience: number,
        /** 炮倍数 */
        cannonBet: number,
        /** 钻石数 */
        gem: number,
        /** 金币数 */
        coin: number,
        /** 魔力 */
        magic: number,
        /** 渔币 */
        fishCoin: number,
        /** 奖券初始上限 */
        ticketOriginLimit: number,
        /** 奖券当前上限 */
        ticketCurrentLimit: number,
        /** 已消费奖券 */
        ticketConsumed: number,
        /** 注册时间 */
        registerTime: number,
        /** 贵族结束时间,月卡结束时间 */
        dailyVipEndTime: number,
        /** 充值金额 */
        rechargeAmount: number,
        /** 最后登录时间 */
        lastLoginTime: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取赠送记录 <a id="/data/GetPresentLogs"></a>

**路径**
- POST `/data/GetPresentLogs`

**请求**
```ts
interface ReqGetPresentLogs {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 赠送人昵称 */
        senderNickname?: string,
        /** 接收人昵称 */
        receiverNickname?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetPresentLogs {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 赠送人昵称 */
        senderNickname: string,
        /** 接收人昵称 */
        receiverNickname: string,
        /** 道具id */
        itemId: number,
        /** 道具名称 */
        itemName: string,
        /** 数量 */
        amount: number,
        /** 赠送时间 */
        time: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取道具消耗 <a id="/data/GetPropConsume"></a>

**路径**
- POST `/data/GetPropConsume`

**请求**
```ts
interface ReqGetPropConsume {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetPropConsume {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 号角总数 */
        hornAmount: number,
        /** 钻石包总数 */
        gemPackAmount: number,
        /** 狂暴总数 */
        rageAmount: number,
        /** 锁定总数 */
        lockonAmount: number,
        /** 冰冻总数 */
        freezeAmount: number,
        /** 神灯总数 */
        lampAmount: number,
        /** 宝石总数 */
        rubyAmount: number,
        /** 每天产出号角 */
        hornDailyAmount: number,
        /** 每天消耗号角 */
        hornDailyConsumeAmount: number,
        /** 每天产出钻石包 */
        gemPackDailyAmount: number,
        /** 每天消耗钻石包 */
        gemPackDailyConsumeAmount: number,
        /** 每天产出狂暴 */
        rageDailyAmount: number,
        /** 每天消耗狂暴 */
        rageDailyConsumeAmount: number,
        /** 每天产出锁定 */
        lockonDailyAmount: number,
        /** 每天消耗锁定 */
        lockonDailyConsumeAmount: number,
        /** 每天产出冰冻 */
        freezeDailyAmount: number,
        /** 每天消耗冰冻 */
        freezeDailyConsumeAmount: number,
        /** 每天产出神灯 */
        lampDailyAmount: number,
        /** 每天消耗神灯 */
        lampDailyConsumeAmount: number,
        /** 每天产出宝石 */
        rubyDailyAmount: number,
        /** 每天消耗宝石 */
        rubyDailyConsumeAmount: number,
        /** 赠送号角 */
        hornGiftAmount: number,
        /** 赠送钻石包 */
        gemPackGiftAmount: number,
        /** 赠送狂暴 */
        rageGiftAmount: number,
        /** 赠送锁定 */
        lockonGiftAmount: number,
        /** 赠送冰冻 */
        freezeGiftAmount: number,
        /** 赠送神灯 */
        lampGiftAmount: number,
        /** 赠送宝石 */
        rubyGiftAmount: number
    }[],
    /** 返回分页 */
    page?: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取道具购买 <a id="/data/GetPropPurchaseLogs"></a>

**路径**
- POST `/data/GetPropPurchaseLogs`

**请求**
```ts
interface ReqGetPropPurchaseLogs {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetPropPurchaseLogs {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** 昵称 */
        nickname: string,
        /** 道具id */
        itemId: number,
        /** 道具名称 */
        itemName: string,
        /** 购买数量 */
        amount: number,
        /** 总数量 */
        total: number,
        /** 购买时间 */
        time: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取充值明细 <a id="/data/GetRecharges"></a>

**路径**
- POST `/data/GetRecharges`

**请求**
```ts
interface ReqGetRecharges {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /** 玩家ID */
        accountId?: number,
        /** VIP等级 */
        vipLevel?: number,
        /** 支付方式 */
        paymentMethod?: "wechat" | "alipay" | "vivo" | "alipay1",
        /** 到账状态 */
        orderStatus?: "pending" | "completed" | "all",
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRecharges {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** SDKID */
        accountId: number,
        /** VIP等级 */
        vipLevel: number,
        /** 支付方式 */
        paymentMethod: "wechat" | "alipay" | "vivo" | "alipay1",
        /** 充值金额 */
        rechargeAmount: number,
        /** 充值时间 */
        rechargeTime: /*datetime*/ string,
        /** 商品id */
        commodityId: number,
        /** 订单号 */
        orderId: string,
        /** 充值时间 */
        rechargeDate: string,
        /** 到账状态 */
        orderStatus: "pending" | "completed",
        /** 到账时间 */
        completeDate: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取iOS充值明细 <a id="/data/GetRechargesIOS"></a>

**路径**
- POST `/data/GetRechargesIOS`

**请求**
```ts
interface ReqGetRechargesIOS {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /** 玩家ID */
        accountId?: number,
        /** VIP等级 */
        vipLevel?: number,
        /** 到账状态 */
        orderStatus?: "pending" | "completed" | "all",
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRechargesIOS {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** SDKID */
        accountId: number,
        /** VIP等级 */
        vipLevel: number,
        /** 充值金额 */
        rechargeAmount: number,
        /** 充值时间 */
        rechargeTime: /*datetime*/ string,
        /** 商品id */
        commodityId: number,
        /** 订单号 */
        orderId: string,
        /** 充值时间 */
        rechargeDate: string,
        /** 到账状态 */
        orderStatus: "pending" | "completed",
        /** 到账时间 */
        completeDate: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取充值统计 <a id="/data/GetRechargesMore"></a>

**路径**
- POST `/data/GetRechargesMore`

**请求**
```ts
interface ReqGetRechargesMore {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRechargesMore {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 新增玩家 */
        newPlayers: number,
        /** 活跃玩家 */
        activePlayers: number,
        /** 付费金额 */
        paymentAmount: number,
        /** 付费人数 */
        payingPlayers: number,
        /** ARPU */
        arpu: number,
        /** ARPPU */
        arppu: number,
        /** 付费率 */
        paymentRate: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取模拟充值明细 <a id="/data/GetRechargesSimu"></a>

**路径**
- POST `/data/GetRechargesSimu`

**请求**
```ts
interface ReqGetRechargesSimu {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /** 玩家ID */
        accountId?: number,
        /** VIP等级 */
        vipLevel?: number,
        /** 到账状态 */
        orderStatus?: "pending" | "completed" | "all",
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRechargesSimu {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** SDKID */
        accountId: number,
        /** VIP等级 */
        vipLevel: number,
        /** 充值金额 */
        rechargeAmount: number,
        /** 充值时间 */
        rechargeTime: /*datetime*/ string,
        /** 商品id */
        commodityId: number,
        /** 订单号 */
        orderId: string,
        /** 充值时间 */
        rechargeDate: string,
        /** 到账状态 */
        orderStatus: "pending" | "completed",
        /** 到账时间 */
        completeDate: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取资源日志 <a id="/data/GetResLog"></a>

**路径**
- POST `/data/GetResLog`

**请求**
```ts
interface ReqGetResLog {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /** 道具id */
        itemId?: number,
        /** 操作标记 */
        action?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetResLog {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** 昵称 */
        nickname: string,
        /** 道具id */
        itemId: number,
        /** 道具名称 */
        itemName: string,
        /** 操作标记 */
        action: string,
        /** 数量 */
        amount: number,
        /** 当前总数 */
        total: number,
        /** 行为参数 */
        params: string,
        /** 操作时间 */
        time: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取背包资源信息 <a id="/data/GetResources"></a>

**路径**
- POST `/data/GetResources`

**请求**
```ts
interface ReqGetResources {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /**
        * 请求的道具id
        * 4     1002    105   101   102   103   104   111       112       113       114       6       5     124
        * 奖券，钻石包，号角，锁定，冰冻，狂暴，神灯，青铜鱼雷，白银鱼雷，黄金鱼雷，白金鱼雷，金刚石，宝石，白金碎片
        * 若不指定道具id，则返回所有道具数量
        * 目前可固定[4,1002,105,101,102,103,104,111,112,113,114,6,5,124]
        */
        itemIds?: number[],
        /** 按道具数量排序,填写道具id，分别为：奖券，钻石包，号角，宝石，金刚石，黄金鱼雷，白金鱼雷，白金碎片 */
        sortBy?: 4 | 1002 | 105 | 5 | 6 | 113 | 114 | 124
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetResources {
    /** 数据列表的key值列表，顺序与数据列表中的数量顺序一致 */
    keys: string[],
    /** 数据列表 */
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** 昵称 */
        nickname: string,
        /** vip等级 */
        vipLevel: number,
        /**
        * 道具
        * 根据请求道具id返回对应的道具数量，若请求中未指定道具id，则返回所有道具数量
        */
        items: number[]
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取仓库存取日志 <a id="/data/GetSafeLog"></a>

**路径**
- POST `/data/GetSafeLog`

**请求**
```ts
interface ReqGetSafeLog {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号ID */
        playerId?: string,
        /** 道具id */
        itemId?: number,
        /** SDKID */
        accountId?: string,
        /** 操作类型:全部/存入/取出 */
        actionType?: "all" | "deposit" | "withdraw",
        /**
        * 排序
        * 按照sdkid升序
        * 按照操作时间降序
        */
        orderBy?: "accountIdIncrease" | "actionTime",
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetSafeLog {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 仓库SDKID */
        storeAccountId: number,
        /** 仓库数量变更前 */
        storeAmountBefore: number,
        /** 仓库数量变更后 */
        storeAmountAfter: number,
        /** 操作者SDKID */
        actionAccountId: number,
        /** 操作者账号id */
        playerId: number,
        /** 操作者账号 */
        playerName: string,
        /** 操作者昵称 */
        nickname: string,
        /** 操作者道具总数变更前 */
        actionAmountBefore: number,
        /** 操作者道具总数变更后 */
        actionAmountAfter: number,
        /** 道具id */
        itemId: number,
        /** 道具名称 */
        itemName: string,
        /** 操作类型:存入/取出 */
        actionType: "deposit" | "withdraw",
        /** 操作数量 */
        actionAmount: number,
        /** 操作时间 */
        actionTime: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取仓库资源信息 <a id="/data/GetSafeResources"></a>

**路径**
- POST `/data/GetSafeResources`

**请求**
```ts
interface ReqGetSafeResources {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** SDKID */
        accountId?: number,
        /**
        * 请求的道具id
        * 4     1002    105   101   102   103   104   111       112       113       114       6       5
        * 奖券，钻石包，号角，锁定，冰冻，狂暴，神灯，青铜鱼雷，白银鱼雷，黄金鱼雷，白金鱼雷，金刚石，宝石
        * 若不指定道具id，则返回所有道具数量
        * 目前可固定[4,1002,105,101,102,103,104,111,112,113,114,6,5]
        */
        itemIds?: number[],
        /** 按道具数量排序,填写道具id，分别为：奖券，钻石包，号角，宝石，金刚石，黄金鱼雷，白金鱼雷 */
        sortBy?: 4 | 1002 | 105 | 5 | 6 | 113 | 114
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetSafeResources {
    /** 数据列表的key值列表，顺序与数据列表中的数量顺序一致 */
    keys: string[],
    /** 数据列表 */
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** SDKID */
        accountId: number,
        /**
        * 仓库状态
        * 保险箱开关状态0关1开
        */
        status: number,
        /**
        * 道具
        * 根据请求道具id返回对应的道具数量，若请求中未指定道具id，则返回所有道具数量
        */
        items: number[]
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取仓库道具总计 <a id="/data/GetStoreCount"></a>

**路径**
- POST `/data/GetStoreCount`

**请求**
```ts
interface ReqGetStoreCount {
    filter?: {
        /** 开始日期 */
        startDate?: /*datetime*/ string,
        /** 结束日期 */
        endDate?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetStoreCount {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 奖券 */
        ticket: number,
        /** 号角 */
        horn: number,
        /** 锁定 */
        lockon: number,
        /** 冰冻 */
        freeze: number,
        /** 狂暴 */
        rage: number,
        /** 神灯 */
        lamp: number,
        /** 青铜弹头 */
        bronzeTorpedo: number,
        /** 白银弹头 */
        silverTorpedo: number,
        /** 黄金弹头 */
        goldTorpedo: number,
        /** 白金弹头 */
        platinumTorpedo: number,
        /** 金刚石 */
        diamond: number,
        /** 宝石 */
        ruby: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取金币统计 <a id="/data/GoldCount"></a>

**路径**
- POST `/data/GoldCount`

**请求**
```ts
interface ReqGoldCount {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 开始日期 */
        dateStart?: /*datetime*/ string,
        /** 结束日期 */
        dateEnd?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGoldCount {
    list: {
        /** 日期 */
        date: /*datetime*/ string,
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 商城充值金币 */
        paidGold: number,
        /** 充值赠送金币 */
        paidGiftGold: number,
        /** 兑换获得金币 */
        exchangedGold: number,
        /** 发送资源的金币 */
        sentGold: number,
        /** 每日登录奖励金币 */
        dailyLoginRewardGold: number,
        /** 救济金 */
        reliefGold: number,
        /** 升级炮台赠送金币 */
        upgradeCannonRewardGold: number,
        /** vip赠送金币 */
        vipRewardGold: number,
        /** 悬赏任务奖励金币 */
        bountyRewardGold: number,
        /** 启航礼包奖励金币 */
        embarkGiftRewardGold: number,
        /** 特惠礼包每日奖励金币 */
        specialOfferGiftDailyRewardGold: number,
        /** 爆发总值 */
        boomTotalValue: number,
        /** 活动赠送的金币，以及赠送的弹头换算金币 */
        eventRewardGold: number,
        /** 下分 */
        deductGold: number,
        /** 当前剩余金币 */
        remainingGold: number,
        /** 当前拥有弹头换算金币 */
        remainingTorpedoValue: number,
        /** 抽奖奖池金币 */
        lotteryPoolGold: number,
        /** 剩余爆发值 */
        remainingBoomValue: number,
        /** 未到账弹头换算金币 */
        pendingTorpedoValue: number,
        /** 当前奖劵换成金币 */
        currentCouponToGold: number,
        /** 打鱼消耗金币 */
        fishingCostGold: number,
        /** 打鱼获得金币 */
        fishingRewardGold: number,
        /** 打鱼获得的弹头换算金币 */
        fishingRewardTorpedoValue: number,
        /** 牛牛总押 */
        niuniuTotalBet: number,
        /** 嘉年华总押 */
        carnivalTotalBet: number,
        /** 德州扑克总押 */
        pokerTotalBet: number,
        /** 水浒传总押 */
        shuiHuTotalBet: number,
        /** 牛牛总盈 */
        niuniuTotalProfit: number,
        /** 嘉年华总盈 */
        carnivalTotalProfit: number,
        /** 德州扑克总盈 */
        pokerTotalProfit: number,
        /** 水浒传总盈 */
        shuiHuTotalProfit: number,
        /** 炸金币使用的弹头换算金币 */
        bombGoldTorpedoValue: number,
        /** 抽奖奖池消耗金币 */
        lotteryPoolCostGold: number,
        /** 使用的弹头换算奖券 */
        usedTorpedoToCoupon: number,
        /** 炸奖券使用的弹头换算金币 */
        bombCouponTorpedoValue: number,
        /** 转盘消耗金币 */
        wheelCostGold: number,
        /** 抓娃娃消耗金币 */
        clawMachineCostGold: number,
        /** 转盘获得金币 */
        wheelRewardGold: number,
        /** 抓娃娃获得金币 */
        clawMachineRewardGold: number,
        /** 使用弹头获得的金币 */
        usedTorpedoToGold: number,
        /** 抽奖获得的金币，以及获得的弹头换算金币 */
        lotteryRewardGold: number,
        /** 使用弹头获得奖券 */
        usedTorpedoToLotteryCoupon: number,
        /** 奖券折换成金币 */
        lotteryCouponToGold: number,
        /** 剩余魔法值换成金币 */
        remainingMagicValueToGold: number,
        /** 打鱼消耗魔法石 */
        fishingCostMagicToGold: number,
        /** 打鱼获取魔法石 */
        fishingRewardMagicToGold: number,
        /** 魔法场打鱼获得的弹头换算金币 */
        fishingRewardMagicTorpedoToGold: number,
        /** 打渔消耗救济金 */
        fishingCostReliefToGold: number,
        /** 水浒消耗救济金 */
        shuiHuCostReliefToGold: number,
        /** 水浒魔法场总压 */
        shuiHuMagicTotalBet: number,
        /** 水浒魔法场总赢 */
        shuiHuMagicTotalProfit: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取核心用户统计 <a id="/data/Vips"></a>

**路径**
- POST `/data/Vips`

**请求**
```ts
interface ReqVips {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResVips {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 账号 */
        playerName: string,
        /** 昵称 */
        nickname: string,
        /** 创建时间 */
        createTime: /*datetime*/ string,
        /** 充值金额 */
        rechargeAmount: number,
        /** 首次交易时间 */
        firstTransactionTime: /*datetime*/ string,
        /** 交易总次数 */
        transactionCount: number,
        /** 本周交易次数 */
        weeklyTransactionCount: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

## game

### 获取绑定解绑账号 <a id="/game/GetBindSdkId"></a>

**路径**
- POST `/game/GetBindSdkId`

**请求**
```ts
interface ReqGetBindSdkId {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    }[],
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetBindSdkId {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** SDK ID */
        accountId: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取公告发送列表 <a id="/game/GetBulletinList"></a>

**路径**
- POST `/game/GetBulletinList`

**请求**
```ts
interface ReqGetBulletinList {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 开始时间 */
        startDate?: /*datetime*/ string,
        /** 结束时间 */
        endDate?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetBulletinList {
    list: {
        /** 公告id */
        bulletinId: string,
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 公告内容 */
        content: string,
        /** 发送次数 */
        sendTimes: number,
        /** 发送频率 */
        sendFrequency: number,
        /** 发布时间 */
        publishDate: /*datetime*/ string,
        /**
        * 状态
        * draft: 草稿
        * send：已发送
        */
        status: "draft" | "send"
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取已发送公告列表 <a id="/game/GetBulletins"></a>

**路径**
- POST `/game/GetBulletins`

**请求**
```ts
interface ReqGetBulletins {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 开始时间 */
        startDate?: /*datetime*/ string,
        /** 结束时间 */
        endDate?: /*datetime*/ string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetBulletins {
    list: {
        /** 公告id */
        bulletinId: string,
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 公告内容 */
        content: string,
        /** 发送次数 */
        sendTimes: number,
        /** 发送频率 */
        sendFrequency: number,
        /** 发布时间 */
        publishDate: /*datetime*/ string,
        /**
        * 状态
        * sent: 发送成功
        * deleted: 已删除
        */
        status: "sent" | "deleted"
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取兑换码总览 <a id="/game/GetDhmzl"></a>

**路径**
- POST `/game/GetDhmzl`

**请求**
```ts
interface ReqGetDhmzl {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 生成日期 */
        generateDate?: /*datetime*/ string,
        /** 兑换码 */
        exchangeCode?: string,
        /** 批次 */
        batchId?: number,
        /**
        * 状态:
        * 全部
        * 已兑换
        * 未兑换
        */
        status?: "all" | "exchanged" | "unexchanged"
    }[],
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetDhmzl {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 生成时间 */
        generateDate: /*datetime*/ string,
        /** 批次id */
        batchId: number,
        /** 礼包id */
        giftId: number,
        /** 兑换码 */
        exchangeCode: string,
        /** 状态 */
        status: "exchanged" | "unexchanged",
        /** 奖励内容 */
        rewardContent: string,
        /** 要求注册时间开始 */
        registerTimeStart: /*datetime*/ string,
        /** 要求注册时间结束 */
        registerTimeEnd: /*datetime*/ string,
        /** 兑换玩家id */
        playerId: string,
        /** 兑换玩家昵称 */
        playerName: string,
        /** 兑换时间 */
        exchangeTime: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取邮件申请列表 <a id="/game/GetEmailApplyList"></a>

**路径**
- POST `/game/GetEmailApplyList`

**请求**
```ts
interface ReqGetEmailApplyList {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetEmailApplyList {
    list: {
        /** 邮件id */
        mailId: string,
        /** 申请日期 */
        applyDate: /*datetime*/ string,
        /** 申请人 */
        applicant: string,
        /** 渠道：0为全部，1为官方 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 接收人 */
        recipient: string,
        /** 附件 */
        attachment: string,
        /** 标题 */
        title: string,
        /** 内容 */
        content: string,
        /** 状态：草稿，审核中，审核通过，驳回 */
        status: "draft" | "pending" | "approved" | "rejected"
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取兑换管理 <a id="/game/GetExchange"></a>

**路径**
- POST `/game/GetExchange`

**请求**
```ts
interface ReqGetExchange {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 开始时间 */
        startTime?: string,
        /** 结束时间 */
        endTime?: string,
        /** 账号 */
        playerName?: string,
        /** 电话号码 */
        phone?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetExchange {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: number,
        /** 玩家昵称 */
        nickname: string,
        /** 道具名称 */
        itemName: string,
        /** 订单ID */
        orderId: string,
        /** 卡号 */
        cardNo: string,
        /** 卡密 */
        cardPwd: string,
        /** 电话号码 */
        phone: string,
        /** 收货人 */
        receiver: string,
        /** 收货地址 */
        address: string,
        /** 创建时间 */
        createTime: string,
        /** 处理时间 */
        handleTime: string,
        /**
        * 状态：
        * 待处理
        * 已处理
        */
        status: "pending" | "handled"
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取兑换记录 <a id="/game/GetExchangeRecord"></a>

**路径**
- POST `/game/GetExchangeRecord`

**请求**
```ts
interface ReqGetExchangeRecord {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 开始时间 */
        startTime?: string,
        /** 结束时间 */
        endTime?: string,
        /** 账号 */
        playerName?: string,
        /** 电话号码 */
        phone?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetExchangeRecord {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: number,
        /** 玩家昵称 */
        nickname: string,
        /** 道具名称 */
        itemName: string,
        /** 订单ID */
        orderId: string,
        /** 卡号 */
        cardNo: string,
        /** 卡密 */
        cardPwd: string,
        /** 电话号码 */
        phone: string,
        /** 收货人 */
        receiver: string,
        /** 收货地址 */
        address: string,
        /** 创建时间 */
        createTime: string,
        /** 处理时间 */
        handleTime: string,
        /**
        * 状态：
        * 待处理
        * 已处理
        */
        status: "pending" | "handled"
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取清理鱼雷 <a id="/game/GetFlushFish"></a>

**路径**
- POST `/game/GetFlushFish`

**请求**
```ts
interface ReqGetFlushFish {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetFlushFish {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** 昵称 */
        nickname: string,
        /** 青铜鱼雷 */
        bronzeTorpedo: number,
        /** 白银鱼雷 */
        silverTorpedo: number,
        /** 黄金鱼雷 */
        goldTorpedo: number,
        /** 白金鱼雷 */
        platinumTorpedo: number,
        /** 鱼雷总价值 */
        totalValue: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取封号 <a id="/game/GetFroze"></a>

**路径**
- POST `/game/GetFroze`

**请求**
```ts
interface ReqGetFroze {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetFroze {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家id */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 状态:0正常，1已封号 */
        status: 0 | 1,
        /** 封号时间 */
        frozeTime: /*datetime*/ string,
        /** 封号结束时间 */
        frozeEndTime: /*datetime*/ string,
        /** 封号时长（小时） */
        frozeDuration: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取踢人 <a id="/game/GetKickOut"></a>

**路径**
- POST `/game/GetKickOut`

**请求**
```ts
interface ReqGetKickOut {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetKickOut {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家ID */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 状态:0正常，1已踢出 */
        status: 0 | 1,
        /** 操作时间 */
        actionTime: /*datetime*/ string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取邮件审核列表 <a id="/game/GetMailAudit"></a>

**路径**
- POST `/game/GetMailAudit`

**请求**
```ts
interface ReqGetMailAudit {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetMailAudit {
    list: {
        /** 邮件id */
        mailId: string,
        /** 申请日期 */
        applyDate: /*datetime*/ string,
        /** 申请人 */
        applicant: string,
        /** 渠道：0为全部，1为官方 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 接收人 */
        recipient: string,
        /** 附件 */
        attachment: string,
        /** 标题 */
        title: string,
        /** 内容 */
        content: string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取刷新配置 <a id="/game/GetRefreshConfig"></a>

**路径**
- POST `/game/GetRefreshConfig`

**请求**
```ts
interface ReqGetRefreshConfig {
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRefreshConfig {
    list: {
        /** 操作人 */
        operator: string,
        /** 操作时间 */
        operateTime: /*datetime*/ string,
        /**
        * 刷新结果
        * 0: 刷新失败
        * 1: 刷新成功
        */
        result: 0 | 1
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取充值账号密码 <a id="/game/GetResetPassword"></a>

**路径**
- POST `/game/GetResetPassword`

**请求**
```ts
interface ReqGetResetPassword {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    }[],
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetResetPassword {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** 昵称 */
        nickname: string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取重置赠送密码 <a id="/game/GetResetPresentPassword"></a>

其实是充值角色密码

**路径**
- POST `/game/GetResetPresentPassword`

**请求**
```ts
interface ReqGetResetPresentPassword {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    }[],
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetResetPresentPassword {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** 昵称 */
        nickname: string
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取SDK角色 <a id="/game/GetSdkRole"></a>

**路径**
- POST `/game/GetSdkRole`

**请求**
```ts
interface ReqGetSdkRole {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** SDK ID */
        accountId?: string,
        /** SDK账号类型 */
        accountType?: number
    }[],
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetSdkRole {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** SDK ID */
        accountId: number,
        /** SDK账号类型 */
        accountType: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取设置角色类型 <a id="/game/GetSetRole"></a>

**路径**
- POST `/game/GetSetRole`

**请求**
```ts
interface ReqGetSetRole {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string,
        /** 角色类型 */
        playerType?: number
    }[],
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetSetRole {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** SDK ID */
        accountId: number,
        /** 角色类型 */
        playerType: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取屏蔽兑换码 <a id="/game/GetShieldExchange"></a>

**路径**
- POST `/game/GetShieldExchange`

**请求**
```ts
interface ReqGetShieldExchange {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetShieldExchange {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** 状态 */
        status: "shielded" | "unshielded",
        /** 屏蔽时间 */
        shieldTime: /*datetime*/ string
    }[],
    __authToken?: string
}
```

---

### 获取屏蔽兑换道具 <a id="/game/GetShieldExchangeProp"></a>

**路径**
- POST `/game/GetShieldExchangeProp`

**请求**
```ts
interface ReqGetShieldExchangeProp {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetShieldExchangeProp {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** 状态 */
        status: "shielded" | "unshielded",
        /** 屏蔽时间 */
        shieldTime: /*datetime*/ string
    }[],
    __authToken?: string
}
```

---

### 获取屏蔽充值 <a id="/game/GetShieldPay"></a>

**路径**
- POST `/game/GetShieldPay`

**请求**
```ts
interface ReqGetShieldPay {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetShieldPay {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** 状态 */
        status: "shielded" | "unshielded",
        /** 屏蔽时间 */
        shieldTime: /*datetime*/ string
    }[],
    __authToken?: string
}
```

---

### 获取屏蔽赠送 <a id="/game/GetShieldPresent"></a>

**路径**
- POST `/game/GetShieldPresent`

**请求**
```ts
interface ReqGetShieldPresent {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetShieldPresent {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** 状态 */
        status: "shielded" | "unshielded",
        /** 屏蔽时间 */
        shieldTime: /*datetime*/ string
    }[],
    __authToken?: string
}
```

---

### 获取禁言 <a id="/game/GetShieldSpeak"></a>

**路径**
- POST `/game/GetShieldSpeak`

**请求**
```ts
interface ReqGetShieldSpeak {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetShieldSpeak {
    list: {
        /** 渠道id */
        channelId: string,
        /** 子渠道id */
        subChannelId: string,
        /** 玩家id */
        playerId: string,
        /** 玩家账号 */
        playerName: string,
        /** 状态 */
        status: "shielded" | "unshielded",
        /** 屏蔽时间 */
        shieldTime: /*datetime*/ string,
        /** 屏蔽结束时间 */
        shieldEndTime: /*datetime*/ string,
        /** 屏蔽时长 */
        shieldDuration: number
    }[],
    __authToken?: string
}
```

---

### 获取系统入口开关设置 <a id="/game/GetSysEntry"></a>

**路径**
- POST `/game/GetSysEntry`

**请求**
```ts
interface ReqGetSysEntry {
    filter?: {
        /** 渠道id */
        channelId?: string,
        /** 子渠道id */
        subChannelId?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetSysEntry {
    list: {
        /** 子渠道id */
        subChannelId: string,
        /** 小游戏开关 */
        miniGame: boolean,
        /** 渔场抽奖开关 */
        fishingLottery: boolean,
        /** 神秘商店入口开关 */
        mysteryShop: boolean,
        /** 小神秘商店入口开关 */
        miniMysteryShop: boolean
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 修改绑定解绑账号 <a id="/game/SetBindSdkId"></a>

**路径**
- POST `/game/SetBindSdkId`

**请求**
```ts
interface ReqSetBindSdkId {
    /** 玩家账号 */
    playerName: string,
    /**
    * SDK ID
    * 绑定账号时传入SDK ID，解绑账号时传入0
    */
    accountId: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetBindSdkId {
    __authToken?: string
}
```

---

### 操作发送列表 <a id="/game/SetBulletinList"></a>

**路径**
- POST `/game/SetBulletinList`

**请求**
```ts
interface ReqSetBulletinList {
    /** 公告id */
    bulletinIds: string[],
    /**
    * 操作类型
    * send: 直接发送公告，公告状态变为已发送
    */
    action: "send",
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetBulletinList {
    __authToken?: string
}
```

---

### 设置已发送公告状态 <a id="/game/SetBulletins"></a>

**路径**
- POST `/game/SetBulletins`

**请求**
```ts
interface ReqSetBulletins {
    bulletinIds: string[],
    action: "delete" | "restore",
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetBulletins {
    __authToken?: string
}
```

---

### sdkid角色渠道设置 <a id="/game/SetChannel"></a>

**路径**
- POST `/game/SetChannel`

**请求**
```ts
interface ReqSetChannel {
    /** SDK ID */
    accountId: number,
    /** 渠道ID */
    channelId: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetChannel {
    __authToken?: string
}
```

---

### 兑换码生成 <a id="/game/SetDhmsc"></a>

**路径**
- POST `/game/SetDhmsc`

**请求**
```ts
interface ReqSetDhmsc {
    /** 礼包id */
    giftId: number,
    /**
    * 兑换码种类
    * 固定码
    * 随机码1，每个角色限用一次
    * 随机码2，每个角色不限次数
    */
    type: "fixed" | "random1" | "random2",
    /** 固定码，在类型为fixed时必须提供 */
    fixedCode?: string,
    /** 生成数量，type为fixed时不填 */
    quantity?: number,
    /** 渠道id */
    channelId?: string,
    /** 子渠道id */
    subChannelId: string,
    /** 要求注册时间开始 */
    registerTimeStart: string,
    /** 要求注册时间结束 */
    registerTimeEnd: string,
    /** 绑定的角色类型 */
    boundRoleType?: number,
    /** 绑定的sdkid类型 */
    boundAccountType?: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetDhmsc {
    __authToken?: string
}
```

---

### 邮件申请 <a id="/game/SetEmailApply"></a>

**路径**
- POST `/game/SetEmailApply`

**请求**
```ts
interface ReqSetEmailApply {
    /** 邮件id，用于修改驳回的邮件 */
    mailId?: string,
    /**
    * 渠道id
    * 0为全部
    * 1为官方
    */
    channelId: string,
    /**
    * 邮件类型
    * 个人邮件，多人邮件，全服邮件
    */
    emailType: "personal" | "multi" | "global",
    /** 账号id列表 */
    playerIds: number[],
    /** 邮件标题 */
    title: string,
    /** 邮件内容 */
    content: string,
    /** 邮件附件 */
    attachments?: {
        itemId: number,
        count: number
    }[],
    /**
    * 操作类型
    * send: 发送邮件
    * save: 保存草稿
    */
    action: "send" | "save",
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetEmailApply {
    __authToken?: string
}
```

---

### 推广号设置 <a id="/game/SetExtend"></a>

**路径**
- POST `/game/SetExtend`

**请求**
```ts
interface ReqSetExtend {
    /** 玩家id */
    playerId: number,
    /** 玩家等级 */
    level: number,
    /** 炮台等级 */
    cannonLevel: number,
    /** 魔法炮台等级 */
    magicCannonLevel: number,
    /** VIP等级 */
    vipLevel: number,
    /** VIP经验 */
    vipExp: number,
    /**
    * 背包容量
    * 填0的时候，不能进渔场 ，不能打开背包
    */
    backpack: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetExtend {
    __authToken?: string
}
```

---

### 模拟充值 <a id="/game/SetFishRecharge"></a>

**路径**
- POST `/game/SetFishRecharge`

**请求**
```ts
interface ReqSetFishRecharge {
    /** 玩家账号 */
    playerName: string,
    /** 金额：分 */
    amount: number,
    /** 计费点 */
    commodityId: number,
    /** 备注 */
    remark: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetFishRecharge {
    __authToken?: string
}
```

---

### 清理鱼雷 <a id="/game/SetFlushFish"></a>

**路径**
- POST `/game/SetFlushFish`

**请求**
```ts
interface ReqSetFlushFish {
    /** 玩家id */
    playerId: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetFlushFish {
    __authToken?: string
}
```

---

### 封号 <a id="/game/SetFroze"></a>

**路径**
- POST `/game/SetFroze`

**请求**
```ts
interface ReqSetFroze {
    /** 要操作的账号 */
    playerIds: number[],
    /** 是否封号 */
    froze: boolean,
    /** 封号时长（小时） */
    frozeDuration?: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetFroze {
    __authToken?: string
}
```

---

### 踢人 <a id="/game/SetKickOut"></a>

**路径**
- POST `/game/SetKickOut`

**请求**
```ts
interface ReqSetKickOut {
    /** 要操作的账号 */
    playerIds: number[],
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetKickOut {
    __authToken?: string
}
```

---

### 邮件审核 <a id="/game/SetMailAudit"></a>

**路径**
- POST `/game/SetMailAudit`

**请求**
```ts
interface ReqSetMailAudit {
    /** 邮件id */
    mailIds: string[],
    /** 是否通过审核 */
    approved: boolean,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetMailAudit {
    __authToken?: string
}
```

---

### 刷新配置 <a id="/game/SetRefreshConfig"></a>

**路径**
- POST `/game/SetRefreshConfig`

**请求**
```ts
interface ReqSetRefreshConfig {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetRefreshConfig {
    __authToken?: string
}
```

---

### 重置账号密码 <a id="/game/SetResetPassword"></a>

**路径**
- POST `/game/SetResetPassword`

**请求**
```ts
interface ReqSetResetPassword {
    /** 玩家账号 */
    playerName: string,
    /** 密码 */
    password: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetResetPassword {
    __authToken?: string
}
```

---

### 重置账号密码 <a id="/game/SetResetPresentPassword"></a>

**路径**
- POST `/game/SetResetPresentPassword`

**请求**
```ts
interface ReqSetResetPresentPassword {
    /** 玩家账号 */
    playerName: string,
    /** 密码 */
    password: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetResetPresentPassword {
    __authToken?: string
}
```

---

### 重置仓库密码 <a id="/game/SetResetSafePwd"></a>

**路径**
- POST `/game/SetResetSafePwd`

**请求**
```ts
interface ReqSetResetSafePwd {
    /** SDK ID */
    accountId: number,
    /** 新密码 */
    password: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetResetSafePwd {
    __authToken?: string
}
```

---

### 重置SDK密码（账号密码） <a id="/game/SetResetSdkPwd"></a>

**路径**
- POST `/game/SetResetSdkPwd`

**请求**
```ts
interface ReqSetResetSdkPwd {
    /** SDK ID */
    accountId: number,
    /** 新密码 */
    password: string,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetResetSdkPwd {
    __authToken?: string
}
```

---

### 设置SDK类型 <a id="/game/SetSdkRole"></a>

**路径**
- POST `/game/SetSdkRole`

**请求**
```ts
interface ReqSetSdkRole {
    /** SDK ID */
    accountId: number,
    /** SDK账号类型 */
    accountType: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetSdkRole {
    __authToken?: string
}
```

---

### 发布公告 <a id="/game/SetSendBulletin"></a>

**路径**
- POST `/game/SetSendBulletin`

**请求**
```ts
interface ReqSetSendBulletin {
    /** 公告id，修改公告时调用 */
    bulletinId?: string,
    /** 渠道id */
    channelId?: string,
    /** 子渠道id */
    subChannelId?: string,
    /** 公告内容 */
    content: string,
    /** 发送次数 */
    sendTimes: number,
    /** 发送频率 */
    sendFrequency: number,
    /**
    * 操作类型
    * send: 直接发送公告
    * save: 保存公告草稿
    */
    action: "send" | "save",
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetSendBulletin {
    __authToken?: string
}
```

---

### 设置角色类型 <a id="/game/SetSetRole"></a>

**路径**
- POST `/game/SetSetRole`

**请求**
```ts
interface ReqSetSetRole {
    /** 玩家账号 */
    playerName: string,
    /** 角色类型 */
    playerType: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetSetRole {
    __authToken?: string
}
```

---

### 屏蔽兑换码 <a id="/game/SetShieldExchange"></a>

**路径**
- POST `/game/SetShieldExchange`

**请求**
```ts
interface ReqSetShieldExchange {
    /** 玩家id */
    playerIds: number[],
    /**
    * 操作
    * shield: 屏蔽赠送
    * unshield: 取消屏蔽赠送
    */
    action: "shield" | "unshield",
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetShieldExchange {
    __authToken?: string
}
```

---

### 屏蔽兑换道具 <a id="/game/SetShieldExchangeProp"></a>

**路径**
- POST `/game/SetShieldExchangeProp`

**请求**
```ts
interface ReqSetShieldExchangeProp {
    /** 玩家id */
    playerIds: number[],
    /**
    * 操作
    * shield: 屏蔽赠送
    * unshield: 取消屏蔽赠送
    */
    action: "shield" | "unshield",
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetShieldExchangeProp {
    __authToken?: string
}
```

---

### 屏蔽充值 <a id="/game/SetShieldPay"></a>

**路径**
- POST `/game/SetShieldPay`

**请求**
```ts
interface ReqSetShieldPay {
    /** 玩家id */
    playerIds: number[],
    /**
    * 操作
    * shield: 屏蔽赠送
    * unshield: 取消屏蔽赠送
    */
    action: "shield" | "unshield",
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetShieldPay {
    __authToken?: string
}
```

---

### 屏蔽赠送 <a id="/game/SetShieldPresent"></a>

**路径**
- POST `/game/SetShieldPresent`

**请求**
```ts
interface ReqSetShieldPresent {
    /** 玩家id */
    playerIds: number[],
    /**
    * 操作
    * shield: 屏蔽赠送
    * unshield: 取消屏蔽赠送
    */
    action: "shield" | "unshield",
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetShieldPresent {
    __authToken?: string
}
```

---

### 屏蔽发言 <a id="/game/SetShieldSpeak"></a>

**路径**
- POST `/game/SetShieldSpeak`

**请求**
```ts
interface ReqSetShieldSpeak {
    /** 玩家id */
    playerIds: number[],
    /**
    * 操作
    * shield: 屏蔽赠送
    * unshield: 取消屏蔽赠送
    */
    action: "shield" | "unshield",
    /** 屏蔽时长，单位秒 */
    duration: number,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetShieldSpeak {
    __authToken?: string
}
```

---

### 系统入口开关设置 <a id="/game/SetSysEntry"></a>

**路径**
- POST `/game/SetSysEntry`

**请求**
```ts
interface ReqSetSysEntry {
    /** 渠道id */
    channelId: string,
    /** 子渠道id */
    subChannelId: string,
    /** 小游戏开关 */
    miniGame?: boolean,
    /** 渔场抽奖开关 */
    fishingLottery?: boolean,
    /** 神秘商店入口开关 */
    mysteryShop?: boolean,
    /** 小神秘商店入口开关 */
    miniMysteryShop?: boolean,
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResSetSysEntry {
    __authToken?: string
}
```

---

## player

### 获取经验值排行榜 <a id="/player/GetRankExp"></a>

**路径**
- POST `/player/GetRankExp`

**请求**
```ts
interface ReqGetRankExp {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRankExp {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家ID */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** VIP等级 */
        vipLevel: number,
        /** 角色等级 */
        level: number,
        /** 经验 */
        experience: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取金币排行榜 <a id="/player/GetRankGold"></a>

**路径**
- POST `/player/GetRankGold`

**请求**
```ts
interface ReqGetRankGold {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRankGold {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家ID */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** VIP等级 */
        vipLevel: number,
        /** 角色等级 */
        level: number,
        /** 金币 */
        coin: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取魔力排行榜 <a id="/player/GetRankMagic"></a>

**路径**
- POST `/player/GetRankMagic`

**请求**
```ts
interface ReqGetRankMagic {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRankMagic {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家ID */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** VIP等级 */
        vipLevel: number,
        /** 魔力 */
        magic: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取充值排行榜 <a id="/player/GetRankRecharge"></a>

**路径**
- POST `/player/GetRankRecharge`

**请求**
```ts
interface ReqGetRankRecharge {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRankRecharge {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家ID */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** VIP等级 */
        vipLevel: number,
        /** 充值金额 */
        rechargeAmount: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取钻石排行榜 <a id="/player/GetRankRing"></a>

**路径**
- POST `/player/GetRankRing`

**请求**
```ts
interface ReqGetRankRing {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRankRing {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家ID */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** VIP等级 */
        vipLevel: number,
        /** 钻石 */
        ring: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取鱼雷排行榜 <a id="/player/GetRankTorpedo"></a>

**路径**
- POST `/player/GetRankTorpedo`

**请求**
```ts
interface ReqGetRankTorpedo {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRankTorpedo {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家ID */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** VIP等级 */
        vipLevel: number,
        /** 角色等级 */
        level: number,
        /** 经验 */
        experience: number,
        /** 青铜鱼雷 */
        bronzeTorpedo: number,
        /** 白银鱼雷 */
        silverTorpedo: number,
        /** 黄金鱼雷 */
        goldTorpedo: number,
        /** 白金鱼雷 */
        platinumTorpedo: number,
        /** 鱼雷总价值 */
        totalTorpedoValue: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

### 获取vip排行榜 <a id="/player/GetRankVIP"></a>

**路径**
- POST `/player/GetRankVIP`

**请求**
```ts
interface ReqGetRankVIP {
    filter?: {
        /** 主渠道 */
        channelId?: string,
        /** 子渠道 */
        subChannelId?: string,
        /** 账号 */
        playerName?: string
    },
    /** 请求分页 */
    page?: {
        /** 一页的数量，最多100 */
        count: number,
        index: number
    },
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResGetRankVIP {
    list: {
        /** 主渠道 */
        channelId: string,
        /** 子渠道 */
        subChannelId: string,
        /** 玩家ID */
        playerId: number,
        /** 玩家账号 */
        playerName: string,
        /** 玩家昵称 */
        nickname: string,
        /** VIP等级 */
        vipLevel: number
    }[],
    /** 返回分页 */
    page: {
        /** 当前页标 */
        index: number,
        pageCount: number,
        count: number,
        totalCount: number
    },
    __authToken?: string
}
```

---

## 获取总数据 <a id="/TotalData"></a>

**路径**
- POST `/TotalData`

**请求**
```ts
interface ReqTotalData {
    /** 鉴权token，登录后的接口都需要填写 */
    __authToken?: string,
    /** 用户昵称 */
    __nickname?: string,
    /** 时间戳 */
    __timestamp?: number,
    /** 操作者ip */
    __ip?: string
}
```

**响应**
```ts
interface ResTotalData {
    /** 累计用户数 */
    users: number,
    /** 最近7天活跃用户数 */
    active7DayUsers: number,
    /** 最近30天活跃用户数 */
    active30DayUsers: number,
    /** 充值用户数 */
    rechargeUsers: number,
    /** 充值总金额 */
    rechargeAmount: number,
    /** 充值ARPU */
    rechargeARPU: number,
    /** 注册ARPU */
    registerARPU: number,
    __authToken?: string
}
```

