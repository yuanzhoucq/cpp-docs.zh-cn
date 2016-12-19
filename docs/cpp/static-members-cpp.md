---
title: "静态成员 (C++) | Microsoft Docs"
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
  - "类实例 [C++], 共享成员"
  - "类实例 [C++], 静态成员"
  - "类成员 [C++], 共享"
  - "类成员 [C++], static"
  - "数据成员 [C++], 静态数据成员"
  - "实例构造函数, 共享成员"
  - "实例构造函数, 静态成员"
  - "成员 [C++], 静态数据成员"
  - "静态数据成员 [C++]"
  - "静态成员 [C++], 数据成员"
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 静态成员 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类可以包含静态成员数据和成员函数。  当数据成员被声明为**“静态”**时，只会为类的所有对象保留一个数据副本。  （有关详细信息，请参阅[静态成员函数](../misc/static-member-functions.md)。）  
  
 静态数据成员不是给定的类类型的对象的一部分。  因此，静态数据成员的声明不被视为一个定义。  在类范围中声明数据成员，但在文件范围内执行定义。  这些静态类成员具有外部链接。  下面的示例阐释了这一点：  
  
```  
// static_data_members.cpp  
class BufferedOutput  
{  
public:  
   // Return number of bytes written by any object of this class.  
   short BytesWritten()  
   {  
      return bytecount;  
   }  
  
   // Reset the counter.  
   static void ResetCount()  
   {  
      bytecount = 0;  
   }  
  
   // Static member declaration.  
   static long bytecount;  
};  
  
// Define bytecount in file scope.  
long BufferedOutput::bytecount;  
  
int main()  
{  
}  
```  
  
 在前面的代码中，该成员 `bytecount` 在类 `BufferedOutput` 中声明，但它必须在类声明的外部定义。  
  
 在不引用类类型的对象的情况下，可以引用静态数据成员。  可以获取使用 `BufferedOutput` 对象编写的字节数，如下所示：  
  
```  
long nBytes = BufferedOutput::bytecount;  
```  
  
 对于存在的静态成员，类类型的所有对象的存在则没有必要。  还可以使用成员选择（**.** 和 **–\>**）运算符访问静态成员。  例如:  
  
```  
BufferedOutput Console;  
  
long nBytes = Console.bytecount;  
```  
  
 在前面的示例中，不会评估对对象\(`Console`\) 的引用；返回的值是静态对象 `bytecount` 的值。  
  
 静态数据成员遵循类成员访问规则，因此只允许类成员函数和友元拥有对静态数据成员的私有访问权限。  这些规则在[成员访问控制](../cpp/member-access-control-cpp.md)中介绍。  例外情况是，无论静态数据成员的访问限制如何，都必须在文件范围内进行定义。  如果进行显式初始化数据成员，则必须使用定义提供初始值设定项。  
  
 静态成员的类型不是由其类名称限定的。  因此，`BufferedOutput::bytecount` 的类型为 `long`。  
  
## 请参阅  
 [类和结构](../cpp/classes-and-structs-cpp.md)