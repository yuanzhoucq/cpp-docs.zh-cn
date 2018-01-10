---
title: "如何： 声明重写说明符 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0f50e500cf25a18e86e107e22d58e6446d03379d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>如何：声明本机编译中的重写说明符 (C++/CLI)
[密封](../windows/sealed-cpp-component-extensions.md)，[抽象](../windows/abstract-cpp-component-extensions.md)，和[重写](../windows/override-cpp-component-extensions.md)可在编译中，不要使用**/ZW**或[/clr](../build/reference/clr-common-language-runtime-compilation.md)。  
  
> [!NOTE]
>  ISO C + + 11 标准语言具有[重写](../cpp/override-specifier.md)标识符和[最终](../cpp/final-specifier.md)标识符，并且两个支持 Visual Studio 使用`final`而不是`sealed`中旨在为代码，编译为仅限本机。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示`sealed`在本机编译中有效。  
  
### <a name="code"></a>代码  
  
```cpp  
// sealed_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
   virtual void g();  
};  
  
class X : public I1 {  
public:  
   virtual void g() sealed {}  
};  
  
class Y : public X {  
public:  
  
   // the following override generates a compiler error  
   virtual void g() {}   // C3248 X::g is sealed!  
};  
```  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示`override`在本机编译中有效。  
  
### <a name="code"></a>代码  
  
```cpp  
// override_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
};  
  
class X : public I1 {  
public:  
   virtual void f() override {}   // OK  
   virtual void g() override {}   // C3668 I1::g does not exist  
};  
```  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 此示例演示`abstract`在本机编译中有效。  
  
### <a name="code"></a>代码  
  
```cpp  
// abstract_native_keyword.cpp  
class X abstract {};  
  
int main() {  
   X * MyX = new X;   // C3622 cannot instantiate abstract class  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [重写说明符](../windows/override-specifiers-cpp-component-extensions.md)