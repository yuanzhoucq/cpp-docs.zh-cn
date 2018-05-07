---
title: 编译器错误 C3628 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5210a9bb91b86c63f0cebabce8901c9af50ae896
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3628"></a>编译器错误 C3628
base class： 托管或 WinRTclasses 仅支持公共继承  
  
尝试使用托管或 WinRT 类用作[私有](../../cpp/private-cpp.md)或[保护](../../cpp/protected-cpp.md)基类。 托管数组或 WinRT 类只能用作基类与[公共](../../cpp/public-cpp.md)访问。  
  
下面的示例生成 C3628，并演示如何修复此错误：  
  
```  
// C3628a.cpp  
// compile with: /clr  
ref class B {  
};  
  
ref class D : private B {   // C3628  
  
// The following line resolves the error.  
// ref class D : public B {  
};  
  
int main() {  
}  
```  
