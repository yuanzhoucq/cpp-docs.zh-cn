---
title: "override | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "重写关键字 [C++]"
  - "重写, 重写关键字 [C++]"
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# override
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`override` 区分上下文的关键字表明类型成员重写基类或基接口成员。  
  
## 备注  
 `override` 关键字在编译本机目标（默认编译器选项）时、Windows 运行时目标（**\/ZW** 编译器选项），或者公共语言运行时目标（**\/clr** 编译器选项）时有效。  
  
 有关重写说明符的更多信息，请参见 [override 说明符](../cpp/override-specifier.md) 和 [重写说明符和本机编译](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
 有关区分上下文的关键字的更多信息，请参见 [上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## 示例  
 **示例**  
  
 以下代码示例表明 `override` 也可用于本机编译。  
  
```cpp#  
// override_keyword_1.cpp  
// compile with: /c  
struct I1 {  
   virtual void f();  
};  
  
struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **示例**  
  
 以下代码示例表明 `override` 可用于 Windows 运行时编译器。  
  
```cpp#  
// override_keyword_2.cpp  
// compile with: /ZW /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **要求**  
  
 编译器选项：**\/ZW**  
  
 **示例**  
  
 以下代码示例表明 `override` 也可用于公共语言运行时编译器。  
  
```cpp#  
// override_keyword_3.cpp  
// compile with: /clr /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **要求**  
  
 编译器选项：**\/clr**  
  
## 请参阅  
 [override 说明符](../cpp/override-specifier.md)   
 [重写说明符](../windows/override-specifiers-cpp-component-extensions.md)