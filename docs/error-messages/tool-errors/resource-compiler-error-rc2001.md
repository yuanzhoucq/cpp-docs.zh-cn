---
title: 资源编译器错误 RC2001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d75d0f906ba0d7be75ca5177bc1f58bccd226251
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039967"
---
# <a name="resource-compiler-error-rc2001"></a>资源编译器错误 RC2001

常量中有换行符

一个字符串常量在第二个行继续不带反斜杠 (**\\**) 或关闭并打开两个双引号 (**"**)。

若要中断一个字符串常量，它位于源文件中的两行上，执行以下操作：

- 结束，第一行用行继续符，反斜杠。

- 结束的字符串与双引号匹配的第一行上，打开下一行中的字符串与另一个引号。

不足够结束，第一行用 \n，在一个字符串常量中嵌入换行字符的转义序列。