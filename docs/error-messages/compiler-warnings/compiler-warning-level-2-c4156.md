---
title: 编译器警告 （等级 2） C4156 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4156
dev_langs:
- C++
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 249d90712b4a8b02f10deaa4d87cdbb7a7c17ae3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296444"
---
# <a name="compiler-warning-level-2-c4156"></a>编译器警告 （等级 2） C4156
使用数组表达式，而无需使用删除; 数组形式的删除替换数组形式  
  
 非数组形式的**删除**无法删除数组。 编译器转换**删除**到数组窗体。  
  
 仅在 Microsoft 扩展 (/Ze) 下出现此警告。  
  
## <a name="example"></a>示例  
  
```  
// C4156.cpp  
// compile with: /W2  
int main()  
{  
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];  
   delete array; // C4156, changed by compiler to "delete [] array;"  
}  
```