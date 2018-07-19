---
title: 编译器错误 C2061 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4d4b018dbab16e8e376a3331a85d0f1b1004f5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167374"
---
# <a name="compiler-error-c2061"></a>编译器错误 C2061
语法错误： 标识符 identifier  
  
 编译器发现标识符不应在此。 请确保`identifier`在使用它之前声明。  
  
 初始值设定项可能由括号括起。 若要避免此问题，请将声明符括在括号中，或使其`typedef`。  
  
 当编译器检测到作为类模板参数; 表达式时，也可能导致此错误使用[typename](../../cpp/typename.md)以告知编译器它是类型。  
  
 下面的示例生成 C2061:  
  
```  
// C2061.cpp  
// compile with: /c  
template < A a >   // C2061  
// try the following line instead  
// template < typename b >  
class c{};  
```  
  
 如果传递到实例名称，则会发生 C2061 [typeid](../../windows/typeid-cpp-component-extensions.md):  
  
```  
// C2061b.cpp  
// compile with: /clr  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   System::Type ^ pType = typeid<pG>;   // C2061  
   System::Type ^ pType2 = typeid<G>;   // OK  
}  
```