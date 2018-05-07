---
title: 链接器工具警告 LNK4092 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edd9e75dbc781355396e38f767a64c1ded3aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4092"></a>链接器工具警告 LNK4092
共享的可写节节包含重定位;图像可能无法正确运行  
  
 只要您有共享的部分来警告你潜在的严重问题，链接器将发出此警告。  
  
 多个进程之间共享数据的一种方法是将标记为"共享。"部分 但是，将标记为共享部分，这种情况可能会导致问题。 例如，你有一个 DLL，它包含共享的数据部分中声明如下：  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 链接器无法解析`pvar`因为其值取决于在内存中加载 DLL 的位置，因此它放入一个重定位记录 DLL 中。 当 DLL 加载到内存中的地址`var`可以解析和`pvar`分配。 如果另一个进程加载同一个 DLL，但无法加载它位于同一个地址，则重定位的地址`var`为第二个进程和第一个进程的地址空间将指向错误的地址将更新。