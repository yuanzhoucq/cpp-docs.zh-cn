---
title: "编译器警告 （等级 4） C4207 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4207
dev_langs: C++
helpviewer_keywords: C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 31211fb7eb8d71bf214d41d5649cc91a92c9b7fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4207"></a>编译器警告（等级 4）C4207
使用的非标准扩展： 扩展初始值设定项窗体  
  
 使用 Microsoft 扩展 (/Ze)，您可以初始化数组未确定大小的`char`使用大括号内的字符串。  
  
## <a name="example"></a>示例  
  
```  
// C4207.c  
// compile with: /W4  
char c[] = { 'a', 'b', "cdefg" }; // C4207  
  
int main()  
{  
}  
```  
  
 此类初始化操作是在 ANSI 兼容性无效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。