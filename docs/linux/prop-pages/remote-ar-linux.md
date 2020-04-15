---
title: 远程存档属性 (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: 3b6f71d9cceccf0b0221be46bacb1294d84533cd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364291"
---
# <a name="remote-archive-properties-c-linux"></a>远程存档属性 (C++ Linux)

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

::: moniker range=">=vs-2017"

| Property | 描述 |
|--|--|
| 创建存档索引 | 创建存档索引（通过使用 ranlib 完成操作）。 此选项可以加速链接并减少自身库中的依赖项。 |
| 创建精简的存档 | 创建精简的存档。  精简的存档包含项目的相对路径，而不是嵌入对象。  在“精简”和“常规”之间切换需要删除现有库。 |
| Create 上无警告 | 创建库时，不发出警告。 |
| 截断时间戳 | 为时间戳和 uid/gid 使用零。 |
| 取消显示启动版权标志 | 不显示版本号。 |
| 详细 | 详细 |
| 附加选项 | 其他选项。 |
| 输出文件 | /OUT 选项重写 lib 创建的程序的默认名称和位置。 |
| 存档程序 | 指定链接静态对象期间要调用的程序，或远程系统上存档程序的路径。 |
| 存档程序超时 | 远程存档程序超时（毫秒）。 |
| 复制输出 | 指定是否要将生成输出文件从远程系统复制到本地计算机。 |

::: moniker-end
