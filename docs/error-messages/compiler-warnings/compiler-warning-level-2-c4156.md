---
title: "编译器警告（等级 2）C4156 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4156"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4156"
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 2）C4156
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未使用数组形式的“delete”删除数组表达式；数组形式被替代  
  
 非数组形式的 **delete** 不能删除数组。  编译器将 **delete** 转换为数组形式。  
  
 该警告只在 Microsoft 扩展 \(\/Ze\) 下出现。  
  
## 示例  
  
```  
// C4156.cpp  
// compile with: /W2  
int main()  
{  
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];  
   delete array; // C4156, changed by compiler to "delete [] array;"  
}  
```