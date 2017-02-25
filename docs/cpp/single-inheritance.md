---
title: "单个继承 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "single inheritance_cpp"
  - "single inheritance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基类, 间接"
  - "派生类, 单个基类"
  - "继承, 单个"
  - "运算符 [C++], 范围解析"
  - "范围解析运算符"
  - "范围, 范围解析运算符"
  - "单个继承"
ms.assetid: 1cb946ed-8b1b-4cf1-bde0-d9cecbfdc622
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 单个继承
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在“单继承”（继承的常见形式）中，类仅具有一个基类。  考虑下图中阐释的关系。  
  
 ![基本单一继承图](../cpp/media/vc38xj1.png "vc38XJ1")  
简单单继承关系图  
  
 注意该图中从常规到特定的进度。  在大多数类层次结构的设计中发现的另一个常见特性是，派生类与基类具有“某种”关系。  在该图中，`Book` 是一种 `PrintedDocument`，而 `PaperbackBook` 是一种 `book`。  
  
 该图中的另一个要注意的是：`Book` 既是派生类（来自 `PrintedDocument`），又是基类（`PaperbackBook` 派生自 `Book`）。  此类类层次结构的框架声明如下面的示例所示：  
  
```  
// deriv_SingleInheritance.cpp  
// compile with: /LD  
class PrintedDocument {};  
  
// Book is derived from PrintedDocument.  
class Book : public PrintedDocument {};  
  
// PaperbackBook is derived from Book.  
class PaperbackBook : public Book {};  
```  
  
 `PrintedDocument` 被视为 `Book` 的“直接基”类；它是 `PaperbackBook` 的“间接基”类。  差异在于，直接基类出现在类声明的基础列表中，而间接基类不是这样的。  
  
 在声明派生的类之前声明从中派生每个类的基类。  为基类提供前向引用声明是不够的；它必须是一个完整声明。  
  
 在前面的示例中，使用访问说明符 **public**。  [成员访问控制](../cpp/member-access-control-cpp.md)中介绍了公共的、受保护的和私有的继承的含义。  
  
 类可用作多个特定类的基类，如下图所示。  
  
 ![定向非循环图](../Image/vc38XJ2.gif "vc38XJ2")  
有向非循环图示例  
  
 在上面显示的名为“有向非循环图”（或“DAG”）的关系图中，一些类是多个派生类的基类。  但反过来却行不通；任何给定的派生类只有一个直接基类。  该图中的关系图描述“单继承”结构。  
  
> [!NOTE]
>  有向非循环图对于单继承不是唯一的。  它们还用于表示多重继承关系图。  [多重继承](http://msdn.microsoft.com/zh-cn/3b74185e-2beb-4e29-8684-441e51d2a2ca)中对本主题进行了说明。  
  
 在继承中，派生类包含基类的成员以及您添加的所有新成员。  因此，派生类可以引用基类的成员（除非在派生类中重新定义这些成员）。  当在派生类中重新定义了直接或间接基类的成员时，范围解析运算符 \(`::`\) 可用于引用这些成员。  请看以下示例：  
  
```  
// deriv_SingleInheritance2.cpp  
// compile with: /EHsc /c  
#include <iostream>  
using namespace std;  
class Document {  
public:  
   char *Name;   // Document name.  
   void PrintNameOf();   // Print name.  
};  
  
// Implementation of PrintNameOf function from class Document.  
void Document::PrintNameOf() {  
   cout << Name << endl;  
}  
  
class Book : public Document {  
public:  
   Book( char *name, long pagecount );  
private:  
   long  PageCount;  
};  
  
// Constructor from class Book.  
Book::Book( char *name, long pagecount ) {  
   Name = new char[ strlen( name ) + 1 ];  
   strcpy_s( Name, strlen(Name), name );  
   PageCount = pagecount;  
};  
```  
  
 请注意，`Book` 的构造函数 \(`Book::Book`\) 具有对数据成员 `Name` 的访问权。  在程序中，可以创建和使用类型为 `Book` 的对象，如下所示：  
  
```  
//  Create a new object of type Book. This invokes the  
//   constructor Book::Book.  
Book LibraryBook( "Programming Windows, 2nd Ed", 944 );  
  
...  
  
//  Use PrintNameOf function inherited from class Document.  
LibraryBook.PrintNameOf();  
```  
  
 如前面的示例所示，以相同的方式使用类成员和继承的数据和函数。  如果类 `Book` 的实现调用 `PrintNameOf` 函数的重新实现，则只能通过使用范围解析 \(`Document`\) 运算符来调用属于 `::` 类的函数：  
  
```  
// deriv_SingleInheritance3.cpp  
// compile with: /EHsc /LD  
#include <iostream>  
using namespace std;  
  
class Document {  
public:  
   char *Name;          // Document name.  
   void  PrintNameOf() {}  // Print name.  
};  
  
class Book : public Document {  
   Book( char *name, long pagecount );  
   void PrintNameOf();  
   long  PageCount;  
};  
  
void Book::PrintNameOf() {  
   cout << "Name of book: ";  
   Document::PrintNameOf();  
}  
```  
  
 如果存在可访问的明确基类，则可以隐式将派生类的指针和引用转换为其基类的指针和引用。  下面的代码使用指针演示了此概念（相同的原则适用于引用）：  
  
```  
// deriv_SingleInheritance4.cpp  
// compile with: /W3  
struct Document {  
   char *Name;  
   void PrintNameOf() {}  
};  
  
class PaperbackBook : public Document {};  
  
int main() {  
   Document * DocLib[10];   // Library of ten documents.  
   for (int i = 0 ; i < 10 ; i++)  
      DocLib[i] = new Document;  
}  
```  
  
 在前面的示例中，创建了不同的类型。  但是，由于这些类型都派生自 `Document` 类，因此存在对 `Document *` 的隐式转换。  因此，`DocLib` 是“异类列表”（其中包含的所有对象并非属于同一类型），该列表包含不同类型的对象。  
  
 由于 `Document` 类具有一个 `PrintNameOf` 函数，因此它可以打印库中每本书的名称，但它可能会忽略某些特定于文档类型的信息（`Book` 的页计数、`HelpFile` 的字节数等）。  
  
> [!NOTE]
>  强制使用基类来实现函数（如 `PrintNameOf`）通常不是最佳设计。  [虚函数](../cpp/virtual-functions.md)提供其他设计替代方法。  
  
## 请参阅  
 [派生类概述](../misc/overview-of-derived-classes.md)   
 [\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/zh-cn/3b74185e-2beb-4e29-8684-441e51d2a2ca)