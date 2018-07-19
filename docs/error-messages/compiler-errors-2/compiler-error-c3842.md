---
title: 编译器错误 C3842 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3842
dev_langs:
- C++
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c29878f7d64bfe1ed444130c77461dece6d20302
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270757"
---
# <a name="compiler-error-c3842"></a>编译器错误 C3842
“函数”: 不支持在 WinRT 或托管类型的成员函数上使用“const”和“volatile”限定符  
  
 [const](../../cpp/const-cpp.md)和[易失性](../../cpp/volatile-cpp.md)不支持的 Windows 运行时或托管的类型的成员函数上。  
  
 下面的示例生成 C3842：  
  
```  
// C3842a.cpp  
// compile with: /clr /c  
public ref struct A {  
   void f() const {}   // C3842  
   void f() volatile {}   // C3842  
  
   void f() {}  
};  
```