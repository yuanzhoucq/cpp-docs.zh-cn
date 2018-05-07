---
title: NMAKE 警告 U4010 |Microsoft 文档
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
ms.openlocfilehash: fc8c99bb4a9b5daf7f630771d0f240479aaf5f3a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-warning-u4010"></a>NMAKE 警告 U4010
'target': 生成失败;/K 指定，继续...  
  
 给定的目标的命令块中的命令返回非零退出代码。 /K 选项告知 NMAKE 以继续处理生成的相关的部分并完成 NMAKE 会话后颁发退出代码为 1。  
  
 如果给定的目标是，自身的依赖项的另一个目标，NMAKE 发出警告[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md)后此警告。