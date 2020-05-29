---
title: 资源编译器错误 RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: 35042687b798b53857becdedba57861bd4f41a05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191713"
---
# <a name="resource-compiler-error-rc2001"></a>资源编译器错误 RC2001

常量中有换行符

字符串常量在第二行继续，无反斜杠（ **\\** ）或右引号和左双引号（ **"** ）。

若要中断源文件中两行的字符串常数，请执行下列操作之一：

- 使用行继续符（反斜杠）结束第一行。

- 用双引号结束第一行的字符串，并在下一行中用另一个引号打开字符串。

在字符串常量中嵌入换行符的转义序列不能用 \n 结束第一行。
