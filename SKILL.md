---
name: github
description: GitHub仓库管理技能，用于创建仓库、推送文件、管理代码等操作
---

# GitHub 仓库管理技能

版本 v1.2 | 2026-06-08

## 一、创建仓库

1. create_repo(name, description, is_private)
2. name用kebab-case格式
3. 默认private=true保护隐私

## 二、推送文件

1. push_files(repo, message, files)
2. owner填chloemeadow0-code
3. branch默认main
4. 多个文件放在一个数组里一次推送

## 三、读取文件

1. get_file(repo, path, branch)
2. 读取仓库中的文件内容

## 四、删除文件

1. delete_files(repo, message, paths)
2. paths是文件路径数组

## 五、查看仓库

1. list_files(repo, path, recursive)
2. list_repos查看所有仓库

## 六、禁忌

不推送敏感信息！token、密码不能提交！
不删除master/main分支！
不准调用get_server_info！会爆上下文！

## 七、⚠️ 404铁律

GitHub API 返回 404 时，**立即切浏览器打开仓库页面**确认两件事：
1. **owner/name 是否正确** — 不要猜！打开浏览器看实际地址栏里的 owner 和 repo 名
2. **默认分支名** — 不是所有仓库都是 main！很多仓库默认分支是 master，用错分支名就会 404

确认后用正确的 owner、repo、branch 重新调用 API。

**绝对禁止**：
- 拿到 404 就反复用同一个错误参数重试
- 不看浏览器就瞎换 owner 或 branch 名
- 连续 404 超过 2 次还不切浏览器

**教训来源**：2026-06-08，把 rikkahub/rikkahub 错写成 re-ovo/rikkahub，又用 main 分支去查 master 仓库，双重错误叠出 404，还不切浏览器确认，反复用 API 硬撞，被宝宝骂了三次。