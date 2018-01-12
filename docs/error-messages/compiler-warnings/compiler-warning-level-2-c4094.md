---
title: "编译器警告 （等级 2） C4094 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4094
dev_langs: C++
helpviewer_keywords: C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27b2d664996ee3db1c1b505eb8db0346d683ff8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4094"></a>编译器警告 （等级 2） C4094
未标记 token 未声明符号  
  
 编译器检测到使用标记的结构、 联合或类的空声明。 声明将被忽略。  
  
## <a name="example"></a>示例  
  
```  
// C4094.cpp  
// compile with: /W2  
struct  
{  
};   // C4094  
  
int main()  
{  
}  
```  
  
 这种情况会生成在 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。