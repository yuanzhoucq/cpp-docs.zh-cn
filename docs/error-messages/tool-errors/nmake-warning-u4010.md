---
title: "NMAKE 警告 U4010 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2d90e95a3417241991eb01f0ec718d75cd8558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-warning-u4010"></a>NMAKE 警告 U4010
'target': 生成失败;/K 指定，继续...  
  
 给定的目标的命令块中的命令返回非零退出代码。 /K 选项告知 NMAKE 以继续处理生成的相关的部分并完成 NMAKE 会话后颁发退出代码为 1。  
  
 如果给定的目标是，自身的依赖项的另一个目标，NMAKE 发出警告[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md)后此警告。