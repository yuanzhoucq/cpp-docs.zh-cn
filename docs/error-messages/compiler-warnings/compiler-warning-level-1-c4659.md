---
title: "编译器警告 （等级 1） C4659 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4659
dev_langs: C++
helpviewer_keywords: C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd974c730a67489d9197b448f02a5042f77159f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4659"></a>编译器警告（等级 1）C4659
\#杂注杂注： 使用保留的段领域具有未定义的行为，请使用 #pragma 注释 （链接器，...）  
  
 .Drectve 选项已用于传递到链接器选项。 改为使用杂注[注释](../../preprocessor/comment-c-cpp.md)传递链接器选项。  
  
```  
// C4659.cpp  
// compile with: /W1 /LD  
#pragma code_seg(".drectve")   // C4659  
```