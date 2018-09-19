---
title: NMAKE 警告 U4010 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a640245db460f4cd8cd658c097955a69a59d1fb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117487"
---
# <a name="nmake-warning-u4010"></a>NMAKE 警告 U4010

'target': 生成失败;/K 指定，再继续...

为给定目标的命令块中的命令返回非零退出代码。 /K 选项告诉 NMAKE 以继续处理生成的不相关的部分以及当 NMAKE 会话完成时发出的退出代码 1。

如果给定的目标是，本身，另一个目标的从属 NMAKE 发出警告[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md)后此警告。