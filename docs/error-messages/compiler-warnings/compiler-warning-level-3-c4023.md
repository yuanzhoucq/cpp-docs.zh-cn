---
title: "编译器警告 （等级 3） C4023 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4023
dev_langs:
- C++
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e22ba0ed3d91f75ba73e68817611302d15fa2039
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4023"></a>编译器警告（等级 3）C4023
“symbol”：基指针传递到非原型函数：参数数目  
  
 将基指针传递给非原型函数会导致该指针被正常化，并产生不可预知的结果。  
  
 如果你使用传递基指针的原型函数，则可能会修复此警告。