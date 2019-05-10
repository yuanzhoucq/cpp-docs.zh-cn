---
title: 资源编译器错误 RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: f4755e04a744d94636b4b37aaf727e0d733008ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346681"
---
# <a name="resource-compiler-error-rc2001"></a>资源编译器错误 RC2001

常量中有换行符

一个字符串常量在第二个行继续不带反斜杠 (**\\**) 或关闭并打开两个双引号 (**"**)。

若要中断一个字符串常量，它位于源文件中的两行上，执行以下操作：

- 结束，第一行用行继续符，反斜杠。

- 结束的字符串与双引号匹配的第一行上，打开下一行中的字符串与另一个引号。

不足够结束，第一行用 \n，在一个字符串常量中嵌入换行字符的转义序列。