---
title: 编译器错误 C3286 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3286
dev_langs:
- C++
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc47c103e93fe1e4f20f5007c6688b5b6648bf32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248178"
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