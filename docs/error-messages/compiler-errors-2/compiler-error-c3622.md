---
title: 编译器错误 C3622 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3622
dev_langs:
- C++
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d8c7ab18bfba899c2df41becb457ed2e7725f81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260087"
---
# <a name="compiler-error-c3622"></a>编译器错误 C3622
class: 类声明为 keyword 不能实例化  
  
尝试实例化类标记为[抽象](../../windows/abstract-cpp-component-extensions.md)。 一个类标记为`abstract`可以是基类，但它不能实例化。  
  
## <a name="example"></a>示例  
下面的示例生成 C3622。  
  
```  
// C3622.cpp  
// compile with: /clr  
ref class a abstract {};  
  
int main() {  
   a aa;   // C3622  
}  
```  
