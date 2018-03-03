---
title: "编译器错误 C3380 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3380
dev_langs:
- C++
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8789889ab0d9ebe93941a438c286ed718ac4721
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3380"></a>编译器错误 C3380
“class”: 程序集访问说明符无效 - 只允许“public”或“private”  
  
 应用于托管类或结构时， [public](../../cpp/public-cpp.md) 和 [private](../../cpp/private-cpp.md) 关键字指示是否通过程序集元数据公开此类。 程序中使用 `public` /clr `private` 编译的类只可使用 [或](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 `ref`和`value`关键字，与一起使用时[/clr](../../build/reference/clr-common-language-runtime-compilation.md)，指示该类受托管 (请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md))。  
  
 以下示例生成 C3380：  
  
```  
// C3380_2.cpp  
// compile with: /clr  
protected ref class A {   // C3380  
// try the following line instead  
// ref class A {  
public:  
   static int i = 9;  
};  
  
int main() {  
   A^ myA = gcnew A;  
   System::Console::WriteLine(myA->i);  
}  
```  
