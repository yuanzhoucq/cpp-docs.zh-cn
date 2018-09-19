---
title: 链接器工具警告 LNK4006 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4006
dev_langs:
- C++
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c992369d7bb3d9a3571e23c42a64bf936d5ae383
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017607"
---
# <a name="linker-tools-warning-lnk4006"></a>链接器工具警告 LNK4006

中的对象; 已定义的符号忽略第二个定义

以修饰形式显示的给定 `symbol` 被多次定义。 当遇到此警告时，`symbol`会获得两次，但将使用只有其第一个窗体。

如果你尝试将两个导入 libs 合并为一个，可以获取此警告。

如果您正在重新生成的 C 运行时库，可以忽略此消息。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 给定`symbol`可能会使用编译时所创建已包装的函数[/Gy](../../build/reference/gy-enable-function-level-linking.md)。 此符号包含在多个文件，但各编译间已改变。 重新编译包括的所有文件`symbol`。

1. 给定`symbol`可能以不同的方式定义不同的库中的两个成员对象中。

1. 绝对符号可能已定义了两次，每个定义中的不同值。

1. 如果组合库时收到错误消息`symbol`添加到库中已存在。