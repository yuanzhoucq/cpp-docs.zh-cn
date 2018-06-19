---
title: 编译器错误 C2094 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2094
dev_langs:
- C++
helpviewer_keywords:
- C2094
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4db86a805118cbdbf74f21737b4a331fc59237c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167315"
---
# <a name="compiler-error-c2094"></a>编译器错误 C2094
标签“identifier”未定义  
  
通过 [goto](../../cpp/goto-statement-cpp.md) 语句使用的标签在函数中不存在。  
  
## <a name="example"></a>示例  
以下示例生成 C2094：  
  
```cpp  
// C2094.c  
int main() {  
   goto test;  
}   // C2094  
```  
  
 可能的解决方法：  
  
```cpp  
// C2094b.c  
int main() {  
   goto test;  
   test:   
   {  
   }  
}  
```