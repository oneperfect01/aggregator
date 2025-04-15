# 自己记录的用法

```
git clone https://github.com/oneperfect01/aggregator.git
docker compose pull && docker compose up
```
## 说明
会生成一个data文件夹，里面就是生成的文件，可以通过自定义映射到一个web服务器   
比如映射到宝塔的nginx，创建一个html站点，域名为a.com
- ```- /www/wwwroot/a.com/data:/aggregator/data```   
那么访问的路径就是  a.com/data/clash.yaml   
 a.com/data/...
## 更多用法
默认每天一点会自动执行collect.py，也就是会自动更新订阅   
可以通过变量修改执行时间  EXECUTION_TIME_COLLECT

自定义入口，或者说自定义每天自动执行的文件
```  - ./start.sh:/aggregator/start.sh```
保留这个，也就是把这个重新映射到容器
```
TIME_PROCESS=${EXECUTION_TIME_PROCESS:-"0 2 */3 * *"}  # 默认每3天2点执行
COMMAND_PROCESS="/usr/local/bin/python -u /aggregator/subscribe/process.py --all --overwrite --skip"
echo "$TIME_PROCESS $COMMAND_PROCESS >> $LOG_FILE_PROCESS 2>&1" >> /etc/cron.d/aggregator-cron
```
把上述恢复注释，或者参考这个，自定义入口，尤其是第二条，代表入口


# 原作者信息
<details>
<summary>原始内容</summary>


<!--
 * @Author: wzdnzd
 * @Date: 2022-03-06 14:51:29
 * @Description: 
 * Copyright (c) 2022 by wzdnzd, All Rights Reserved.
-->

## 功能
打造免费代理池，爬一切可爬节点
> 拥有灵活的插件系统，如果目标网站特殊，现有功能未能覆盖，可针对性地通过插件实现

> 欢迎 Star 及 PR。对于质量较高且普适的爬取目标，亦可在 Issues 中列出，将在评估后选择性添加

## 使用方法
> 可前往 [Issue #91](https://github.com/wzdnzd/aggregator/issues/91) 食用**共享订阅**，量大质优。**请勿浪费**
 
略，自行探索。我才不会告诉你入口是 `collect.py` 和 `process.py`。**强烈建议使用后者，前者只是个小玩具**，配置参考 `subscribe/config/config.default.json`


## 免责申明
+ 本项目仅用作学习爬虫技术，请勿滥用，不要通过此工具做任何违法乱纪或有损国家利益之事
+ 禁止使用该项目进行任何盈利活动，对一切非法使用所产生的后果，本人概不负责


</details>
