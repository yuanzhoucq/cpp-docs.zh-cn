---
title: "上下文相关的关键字（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "internal_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "上下文相关的关键字"
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 上下文相关的关键字（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*区分上下文关键字*是一些语言元素，这些元素只有在特定上下文中才能识别出来。  在特定的上下文以外，区分上下文关键字可以是用户定义的符号。  
  
## 所有运行时  
 **备注**  
  
 下面是区上下文关键字的列表：  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [delegate](../windows/delegate-cpp-component-extensions.md)  
  
-   [event](../windows/event-cpp-component-extensions.md)  
  
-   [finally](../dotnet/finally.md)  
  
-   [for each，in](../dotnet/for-each-in.md)  
  
-   [initonly](../dotnet/initonly-cpp-cli.md)  
  
-   `internal`（请参见[成员可见性](../misc/member-visibility.md)）  
  
-   [literal](../windows/literal-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [property](../windows/property-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   `where`（[泛型](../windows/generics-cpp-component-extensions.md) 的一部分）  
  
 出于可读性的目的，您可能要限制区分上下文关键字作为用户定义符号的使用。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **备注**  
  
 （此功能没有特定于平台的备注。）  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
 （此功能没有特定于平台的备注。）  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的代码示例显示，在合适的上下文中，`property` 区分上下文关键字可用来定义属性和变量。  
  
```  
// context_sensitive_keywords.cpp  
// compile with: /clr  
public ref class C {  
   int MyInt;  
public:  
   C() : MyInt(99) {}  
  
   property int Property_Block {   // context-sensitive keyword  
      int get() { return MyInt; }  
   }  
};  
  
int main() {  
   int property = 0;               // variable name  
   C ^ MyC = gcnew C();  
   property = MyC->Property_Block;  
   System::Console::WriteLine(++property);  
}  
```  
  
 **输出**  
  
  **100**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)