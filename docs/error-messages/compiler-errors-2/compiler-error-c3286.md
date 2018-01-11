---
title: "编译器错误 C3286 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3286
dev_langs: C++
helpviewer_keywords: C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 80cda9575b604c9dd8e0000428c2d32a487079dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3286"></a>编译器错误 C3286  
  
> *说明符*： 迭代变量不能包含任何存储类说明符  
  
存储类不能对指定迭代变量。 有关详细信息，请参阅[存储类 （c + +）](../../cpp/storage-classes-cpp.md)和[对于每一个，在](../../dotnet/for-each-in.md)。  
  
## <a name="example"></a>示例  
  
下面的示例生成 C3286，并还显示正确的使用情况。  
  
```cpp  
// C3286.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p = { 1, 2, 3 };  
   for each (static int i in p) {}   // C3286   
   for each (int j in p) {}   // OK  
}  
```