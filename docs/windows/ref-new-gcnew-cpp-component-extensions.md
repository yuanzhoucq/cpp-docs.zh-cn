---
title: "gcnew | Microsoft Docs"
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
  - "gcnew"
  - "ref new"
  - "gcnew_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gcnew 关键字 [C++]"
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
caps.latest.revision: 24
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# gcnew
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`ref new` 聚合关键字分配在对象无法访问时进行垃圾回收以及返回已分配对象的句柄 \([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)\) 的类型的实例。  
  
## 所有运行时  
 `ref new` 分配的类型的实例的内存会自动释放。  
  
 如果无法分配内存，则 `ref new` 操作会引发 `OutOfMemoryException`。  
  
 有关如何分配和释放本机 C\+\+ 类型的内存的详细信息，请参阅 [new 和 delete 运算符](../cpp/new-and-delete-operators.md)。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 使用 `ref new` 可为要自动管理其生存期的 Windows 运行时对象分配内存。  对象会在其引用计数变为零（这会在引用的最后一个副本超出范围之后发生）时自动释放。  有关详细信息，请参阅 [Ref 类和结构](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 托管类型（引用或值类型）的内存由 `gcnew` 分配，使用垃圾回收进行释放。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的示例使用 `gcnew` 分配 Message 对象。  
  
```  
// mcppv2_gcnew_1.cpp  
// compile with: /clr  
ref struct Message {  
   System::String^ sender;  
   System::String^ receiver;  
   System::String^ data;  
};  
  
int main() {  
   Message^ h_Message  = gcnew Message;  
  //...  
}  
```  
  
 **示例**  
  
 下面的示例使用 `gcnew` 创建装箱值类型以供使用（如引用类型）。  
  
```  
// example2.cpp : main project file.  
// compile with /clr  
using namespace System;  
value class Boxed {  
    public:  
        int i;  
};  
int main()  
{  
    Boxed^ y = gcnew Boxed;  
    y->i = 32;  
    Console::WriteLine(y->i);  
    return 0;  
}  
```  
  
 **输出**  
  
  **32**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)