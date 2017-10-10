---
title: "编译器错误 C2146 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2146
dev_langs:
- C++
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 92e94ae29c1a7a3fc6adfdc0b3e82f5ce4dfcaf0
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2146"></a>编译器错误 C2146
语法错误： 缺少 token 标识符 identifier 的前面  
  
 编译器预期`token`和找到`identifier`相反。  可能的原因：  
  
1.  拼写或大小写错误。  
  
2.  标识符的声明中缺少类型说明符。  
  
 犯了输入错误可能导致此错误。 错误[C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md)通常在之前发生此错误。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2146。  
  
```  
// C2146.cpp  
class CDeclaredClass {};  
  
class CMyClass {  
   CUndeclared m_myClass;   // C2146  
   CDeclaredClass m_myClass2;   // OK  
};  
  
int main() {  
   int x;  
   int t x;   // C2146 : missing semicolon before 'x'  
}  
```  
  
## <a name="example"></a>示例  
 此错误还可能来自于为 Visual Studio.NET 2003年执行的编译器一致性工作： 缺少`typename`关键字。  
  
 下面的示例在 Visual Studio.NET 2002年中编译，但在 Visual Studio.NET 2003年中将失败：  
  
```  
// C2146b.cpp  
// compile with: /c  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
  
template <typename T>  
X<T>::Y func() { }   // C2146  
  
// OK  
template <typename T>  
typename X<T>::Y func() { }  
```  
  
## <a name="example"></a>示例  
 您还会看到此错误于为 Visual Studio.NET 2003年执行的编译器一致性工作： 显式专用化无法再找到从主模板的模板参数。  
  
 使用`T`显式专用化中不允许从主模板。 对于要在 Visual c + + 的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中有效的代码，替换的显式专用化类型的专用化中的模板参数的所有实例。  
  
 下面的示例在 Visual Studio.NET 中编译，但在 Visual Studio.NET 2003年中将失败：  
  
```  
// C2146_c.cpp  
// compile with: /c  
template <class T>   
struct S;  
  
template <>   
struct S<int> {  
   T m_t;   // C2146  
   int m_t2;   // OK  
};  
```
