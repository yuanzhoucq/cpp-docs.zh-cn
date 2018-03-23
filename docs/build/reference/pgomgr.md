---
title: pgomgr |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 743665bbe0ee9c3df08d197d203e95d08542f613
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="pgomgr"></a>pgomgr

将配置文件数据从一个或多个对应的.pgc 文件添加到该.pgd 文件。

## <a name="syntax"></a>语法

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>参数

*options*<br/>
以下选项可指定到**pgomgr**:

-  或   显示可用**pgomgr**选项。

- **/ 清除**导致要清除的所有配置文件信息的.pgd 文件。 不能指定.pgc 文件时**/清除**指定。

- **详细介绍/**显示详细统计信息，包括流 graph 覆盖率信息。

- **/ 摘要**显示每个函数统计信息。

- **/ 唯一**一起使用时**/摘要**，原因修饰函数名以显示。 默认值，当**/ 唯一**不使用，为要显示的未修饰的函数名称。

- **/merge**[**: * * * n*] 导致中或多个对应的.pgc 文件添加到该.pgd 文件的数据。 可选参数， *n*，允许你指定数据应添加*n*时间。 例如，如果一个方案通常是完成的六倍反映频率由客户，你可以在测试运行中一次执行并将其添加到六倍使用.pgd 文件**pgomgr /merge:6**。

*pgcfiles*<br/>
一个或多个.pgc 文件，你想要合并到.pgd 文件的配置文件数据。 你可以指定单个对应的.pgc 文件或多个对应的.pgc 文件。 如果不指定任何对应的.pgc 文件， **pgomgr**合并其文件名是同名的.pgd 文件的所有对应的.pgc 文件。

*pgdfile*到正在合并来自的.pgc 文件或文件的数据的.pgd 文件。

## <a name="remarks"></a>备注

> [!NOTE]
> 只能从 Visual Studio 开发人员命令提示，可以启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。

## <a name="example"></a>示例

此示例命令将清除配置文件数据的 myapp.pgd 文件：

`pgomgr /clear myapp.pgd`

此示例命令将添加配置文件数据 myapp1.pgc 到.pgd 文件三次：

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

在此示例中，从所有 myapp #.pgc 文件的配置文件数据添加到 myapp.pgd 文件。

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>请参阅

[按配置文件优化](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
