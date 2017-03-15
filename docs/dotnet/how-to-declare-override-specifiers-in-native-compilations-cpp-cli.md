---
title: "如何：声明本机编译中的重写说明符 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "本机编译中的重写说明符，重写"
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：声明本机编译中的重写说明符 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[封装](../windows/sealed-cpp-component-extensions.md)、[抽象](../windows/abstract-cpp-component-extensions.md)和 [override](../windows/override-cpp-component-extensions.md) 可在不使用 **\/ZW** 或 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)的编译。  
  
> [!NOTE]
>  具有标准 C\+\+11 ISO 语言标识符和 [override](../cpp/override-specifier.md)[最终](../cpp/final-specifier.md) 标识符，因此，两种 Visual Studio 中使用 `final` 支持而不是 `sealed`。视为编译为本机的代码。  
  
## 示例  
  
### 说明  
 下面的示例演示，`sealed` 有效。本机编译。  
  
### 代码  
  
```  
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
  
## 示例  
  
### 说明  
 下一个示例演示，`override` 有效。本机编译。  
  
### 代码  
  
```  
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
  
## 示例  
  
### 说明  
 此示例演示，`abstract` 有效。本机编译。  
  
### 代码  
  
```  
// abstract_native_keyword.cpp  
class X abstract {};  
  
int main() {  
   X * MyX = new X;   // C3622 cannot instantiate abstract class  
}  
```  
  
## 请参阅  
 [重写说明符](../windows/override-specifiers-cpp-component-extensions.md)