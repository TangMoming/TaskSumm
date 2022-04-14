## CN-Fin中文金融新闻文本摘要数据集：
该数据集为论文[TaskSum](https://www.dasfaa2022.org//camera_ready/395.pdf) 使用的中文金融新闻数据集
CN-FIN中的新闻，收集整理自东方财富、新浪财经、搜狐财经等网站。该数据集分为：有监督训练数据集，强化训练数据集和数据集。
## 数据获取
[百度网盘] (https://pan.baidu.com/s/1o4ahe7rLLmVPkVeVe68eKQ?pwd=59zm)提取码：59zm
#### 有监督训练数据集：
有监督数据集共有48410篇中文新闻文本，每一篇文档都是一个单独的json格式文件，包含：新闻标题（title），新闻正文（article），和新闻摘要（summary）。
新闻中的摘要是网站提供的人工筛选或人工撰写摘要。工业场景中的摘要质量不高，仅能为计算摘要标签提供参考。

    "title": "李克强 会见 2019 年度 中国 政府 友谊 奖 获奖 外国 专家",
    "article": [
        "股市 还是 未能 逃脱 节前 杀跌 的 规律 ， 那么 节后 会 怎么样 呢",
        "去年 国庆节 之后 大盘 急剧 杀跌 ， 可能 给 投资者 留下 了 巨大 的 心里 阴影 ， 今年 节前 的 大盘 走势 明显 要 弱 于 市场 预期",
        "截至 节前 最后 一个 交易日 收盘 ， 上证 指数 报 2905.19 点 ， 跌 0.92% ； 深 成 指 报 9446.24 点 ， 跌 1.08% ； 创指 报 1627.55 点 ， 跌 1.21%",
        "两 市 成交额 3525 亿 元 ， 较 上 一 交易日 再度 缩量",
        "北 向 资金 尾 盘 再现 集体 涌入 ， 全 天 小 幅 净 流出 6.34 亿 元",
        "至此 ， 上证 指数 、 深成指 和 创业 板 指 周线 皆 出现 三 连 阴 走势 ， 显示 节 前 套现 的 情绪 主导 了 市场",
        ......
        
    ],
    "summary": [
        "【 易 纲 重磅 文章 定调 金融 风险",
        "四 季度 将 迎 三 大 风口 产业 资本 是 最大 空头 】 股市 还是 未能 逃脱 节前 杀跌 的 规律",
        "那么 节后 会 怎么样 呢",
        "2019年 的 十月 是否 会 重现 去年 一幕 呢",
        "这 种 可能性 应该 不大",
        "中国 人民 银行 行长 易 纲 9月 30日 发文 称",
        "金融 风险 整体 收敛 、 总体 可控",
        "市场 预期 发生 积极 变化",
        "而 金融 风险 是 去年 股市 杀跌 的 主因",
    ]

#### 强化训练数据集：
强化训练数据集共有29617篇中文新闻文本, 每一篇文档都是一个单独的json格式文件。由于工业应用场景的数据集中摘要的质量一般。因此我么使用启发式方法计算摘要句抽取标签。我们使用腾讯翻译API将新闻正文翻译为英文，然后使用预训练的sota生成式摘要模型pegasus和BART生成摘要并根据这些模型生成的摘要计算摘要句抽取标签。每一个json文件包含：新闻标题（title），新闻正文（article），腾讯翻译API翻译的部分中文文档（zh_article），腾讯翻译API的翻译结果（en_article），pegasus生成的摘要（pegasus_generate_summary），BART生成的摘要（bart_generate_summary），根据pegasus生成摘要计算得到的抽取标签（pegasus_labels），根据bart生成摘要计算得到的抽取标签（bart_labels），以及综合生成摘要得到的抽取标签（bart_labels），文档的分类类别标签id和标签名（classification_label_id，classification_label_name），由于分类标签数据源自瞰点科技有限公司和本实验室的合作数据，经协商，仅提供分类标签id,请谅解。关于分类标签和分类数据请参考本实验室的论文[F-HMTC](https://www.ijcai.org/proceedings/2020/619)和代码仓库[finint/F-HMTC](https://github.com/finint/F-HMTC)

    "title": "【 中报 点评 31 】 禹洲 地产 ： 全国 化 布局 加速 ， 总 土 储 较 年初 增长 46%",
    "article": [
        "导读 下半年 可 售货 值 705 亿 元 , 占 全年 目标 65% , 加快 完成 全年 目标 . ◎ 作者 / 朱 一鸣 、 齐瑞琳 “ 禹洲 地产 2018 上半年 实现 合约 销售 金额 为 214.94 亿 元 ， 占 全年 600 亿 销售 目标 的 35.82%",
        "项目 布局 集中 合肥 、 苏州 、 杭州 等 一二 线 城市 ， 受到 政策 影响 较 大 ， 下半年 销售 表现 仍 有待 观察",
        "新增 16 幅 地块 ， 权益 土地 储备 地价 约 合 55.24 亿 元 ， 总 建筑 面积 为 223.44 万 平方米 ， 平均 楼面 价格 为 人民币 5297 元 / 平方米",
        "净 负债率 相比 去年 年末 有所 上升 ， 现金 短债 比 虽 有所 上升 ， 但 短期 内 偿债 压力 不大 ， 平均 融资 成本 为 6.52% ， 较 2017年 上升 0.5 个 百分点",
        "” 01 销售 ： 上半年 完成 全年 销售 目标 的 35.8% 禹洲 地产 2018 上半年 实现 合约 销售 金额 为 214.94 亿 元 ， 与 去年 同期 基本 持平 ， 占 全年 600 亿 销售 目标 的 35.82%",
        "合约 销售 面积 为 157.8 万 平方米 ， 较 去年 同期 上升 23%",
        "均价 为 13623 元 / 平方米 ， 低于 去年 的 均价 16744 元 / 平方米",
        "禹洲 地产 计划 在 2020年 实现 千亿 规模 ， 未来 年 复合 增长率 目标 为 40%",
        "2018年 推出 产品 货 值 目标 为 940 亿 元 ， 下半年 的 可 售货 值 为 705 亿 元 ， 今年 的 合约 销售 目标 为 600 亿 元 不变",
       ......
    ],
    "en_article": [
        "The sales value in the second half of the year is 70.5 billion yuan, accounting for 65% of the annual target, speeding up the completion of the annual target. Author / Zhu Yiming, Qi Ruilin \"Yuzhou Real Estate realized contract sales of 21.494 billion yuan in the first half of 2018, accounting for 35.82% of the 60 billion sales target for the whole year.",
        "The layout of the project focuses on the first and second tier cities such as Hefei, Suzhou and Hangzhou, which is greatly affected by the policy, and the sales performance in the second half of the year remains to be seen.",
        "16 new plots, the reserve land price of equity land is about 5.524 billion yuan, the total construction area is 2.2344 million square meters, and the average floor price is 5297 yuan per square meter.",
        "The net debt ratio has increased compared with the end of last year, although the cash-to-short debt ratio has increased, but there is little pressure to repay debt in the short term, with an average financing cost of 6.52%, an increase of 0.5 percentage points over 2017.",
        "\"01 sales: 35.8% of Yuzhou Real Estate achieved its annual sales target in the first half of the year. The contract sales in the first half of 2018 was 21.494 billion yuan, which was basically the same as that in the same period last year, accounting for 35.82% of the 60 billion sales target for the whole year.",
        "The contract sales area was 1.578 million square meters, an increase of 23% over the same period last year.",
               ......
    ],
    "zh_article": [
        "导读 下半年 可 售货 值 705 亿 元 , 占 全年 目标 65% , 加快 完成 全年 目标 . ◎ 作者 / 朱 一鸣 、 齐瑞琳 “ 禹洲 地产 2018 上半年 实现 合约 销售 金额 为 214.94 亿 元 ， 占 全年 600 亿 销售 目标 的 35.82%",
        "项目 布局 集中 合肥 、 苏州 、 杭州 等 一二 线 城市 ， 受到 政策 影响 较 大 ， 下半年 销售 表现 仍 有待 观察",
        "新增 16 幅 地块 ， 权益 土地 储备 地价 约 合 55.24 亿 元 ， 总 建筑 面积 为 223.44 万 平方米 ， 平均 楼面 价格 为 人民币 5297 元 / 平方米",
        "净 负债率 相比 去年 年末 有所 上升 ， 现金 短债 比 虽 有所 上升 ， 但 短期 内 偿债 压力 不大 ， 平均 融资 成本 为 6.52% ， 较 2017年 上升 0.5 个 百分点",
        "” 01 销售 ： 上半年 完成 全年 销售 目标 的 35.8% 禹洲 地产 2018 上半年 实现 合约 销售 金额 为 214.94 亿 元 ， 与 去年 同期 基本 持平 ， 占 全年 600 亿 销售 目标 的 35.82%",
        "合约 销售 面积 为 157.8 万 平方米 ， 较 去年 同期 上升 23%",
        ......
    ],
    "classification_label_id": [
        183
    ],
    "classification_label_name": [
        "房地产"
    ],
    "pegasus_generate_summary": [
        "The sales value in the second half of the year is 70.5 billion yuan, accounting for 65% of the annual target, speeding up the completion of the annual target.",
        "The contract sales area was 1.578 million square meters, an increase of 23% over the same period last year..",
        "The average price is 13,623 yuan per square meter, which is lower than the average price of 16744 yuan per square meter last year..",
        "The product value target for launch in 2018 is 94 billion yuan, the available value for the second half of the year is 70.5 billion yuan, and this year's contract sales target will"
    ],
    "bart_generate_summary": [
        "Yuzhou Real Estate realized contract sales of 21",
        "494 billion yuan in the first half of 2018",
        "The sales value in the second half of the year is 70",
        "5 billion yuan, accounting for 65% of the annual target",
        "The Yangtze River Delta is still the region with the highest contribution to Yuzhou real estate contract sales"
    ],
    "pegasus_labels": [
        0,
        5,
        6,
        8
    ],
    "bart_labels": [
        0,
        9
    ],
    "extracted": [
        0,
        5,
        6,
        8,
        9
    ]
}

#### 测试数据集：
测试数据集共有4834篇中文新闻文本, 每一篇文档都是一个单独的json格式文件。每一个json文件包含：新闻标题（title），新闻正文（article），新闻摘要（summary），文档的分类类别标签id和标签名（classification_label_id，classification_label_name），由于分类标签数据源自瞰点科技有限公司和本实验室的合作数据，经协商，仅提供分类标签id,请谅解。关于分类标签和分类数据请参考本实验室的论文[F-HMTC](https://www.ijcai.org/proceedings/2020/619)和代码仓库[finint/F-HMTC](https://github.com/finint/F-HMTC)

    "title": "养老 保险 覆盖 9.19 亿 人 新业 态 人员 为 全民 参保 重点",
    "summary": [
        "人 社部 新闻 发言人 卢爱红 27日 上午 表示 ， 截至 3月 底 ， 全国 基本 养老 、 失业 、 工伤 保险 参保 人数 分别 为 9.19 亿 人 、 1.88 亿 人 、 2.26 亿 人 ； 一季度 ， 三 项 社会保险 基金 总收入 1.37 万亿 元 ， 同比 增长 22% ， 总 支出 1.06 万 亿 元 ， 同比 增长 18%",
        "对比 2017年 末 的 数据 ， 今年 一季度 参加 养老 保险 的 人数 从 9.15 亿 增加 到了 9.19 亿 ， 距离 养老 保险 应 保 尽保 的 目标 ——10 亿 人 又 进 了 一 步",
        "除去 青少年 和 在校 学生 ， 养老 保险 的 法定 参保人 约 为 10 亿 人",
        "9.19 亿 的 最新 参保 数据 表明 我国 还有 8100 万 人 还 需 纳入 到 养老 保险 的 保障 中 来",
        "针对 新 业态 从业者 流动性 比较 强 的 特点 ， 人 社部 正在 加快 网上 社保 的 建设 ， 增加 社保 制度 的 可 流动性"
    ],
    "article": [
        "虽然 国家 医保局 还 没有 正式 挂牌 ， 但 人 社部 举行 的 第一 季度 新闻 发布会 已经 不再 象 往常 一样 通报 医疗 和 生育 的 数据 了 ， 相关 数据 预计 将 有待 国家 医保局 成立 之后 才 会 发布",
        "人 社部 新闻 发言人 卢爱红 27日 上午 表示 ， 截至 3月 底 ， 全国 基本 养老 、 失业 、 工伤 保险 参保 人数 分别 为 9.19 亿 人 、 1.88 亿 人 、 2.26 亿 人 ； 一季度 ， 三 项 社会保险 基金 总收入 1.37 万亿 元 ， 同比 增长 22% ， 总 支出 1.06 万 亿 元 ， 同比 增长 18%",
        "对比 2017年 末 的 数据 ， 今年 一季度 参加 养老 保险 的 人数 从 9.15 亿 增加 到了 9.19 亿 ， 距离 养老 保险 应 保 尽保 的 目标 ——10 亿 人 又 进 了 一 步",
        ......
    ],
    "classification_label_name": [
        "社会保障",
        "金融市场",
        "社会保障政策"
    ],
    "classification_label_id": [
        234,
        162,
        208
    ]
