---
title: "编译器警告 （等级 1） C4143 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4143
dev_langs:
- C++
helpviewer_keywords:
- same_seg
- C4143
ms.assetid: ef0bd19f-d169-4034-8710-b22971bd642d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 720d3ee7aea412d13b1a842aa9f6c87a50aa0c58
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4143"></a>编译器警告（等级 1）C4143
不支持杂注“same_seg”；使用 __based 分配  
  
 **#Pragma same_seg** 不再受支持。 请改用 [__based](../../cpp/based-pointers-cpp.md) 关键字。