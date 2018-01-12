---
title: "编译器警告 （等级 4） C4214 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4214
dev_langs: C++
helpviewer_keywords: C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 46df65f9e920eae788088d9e4ec219b6bf93e96f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4214"></a>编译器警告（等级 4）C4214
使用的非标准扩展： 位 int 以外的字段类型  
  
 具有默认的 Microsoft 扩展 (/Ze) 中，位域结构成员可以是任何整数类型。  
  
## <a name="example"></a>示例  
  
```  
// C4214.c  
// compile with: /W4  
struct bitfields  
{  
   unsigned short j:4;  // C4214  
};  
  
int main()  
{  
}  
```  
  
 此类位域是在 ANSI 兼容性无效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。