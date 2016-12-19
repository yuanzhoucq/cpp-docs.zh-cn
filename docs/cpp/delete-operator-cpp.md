---
title: "delete 运算符 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "delete_cpp"
  - "delete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delete 关键字 [C++]"
  - "delete 关键字 [C++], 取消分配对象"
  - "delete 关键字 [C++], 语法"
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# delete 运算符 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

释放内存块。  
  
## 语法  
  
```  
[::] delete cast-expression  
[::] delete [ ] cast-expression  
```  
  
## 备注  
 *cast\-expression* 参数必须是指向以前分配给使用 [new 运算符](../cpp/new-operator-cpp.md)创建的对象的内存块的指针。  **delete** 运算符的结果类型为 `void`，因此它不返回值。  例如:  
  
```  
CDialog* MyDialog = new CDialog;  
// use MyDialog  
delete MyDialog;  
```  
  
 对指向不使用 **new** 分配的指针使用 **delete** 将产生不可预知的结果。  但是，可以对值为 0 的指针使用 **delete**。  此设置意味着，当 **new** 失败并返回 0 时，删除已失败 **new** 操作的结果不会造成损害。  有关详细信息，请参阅 [new 和 delete 运算符](../cpp/new-and-delete-operators.md)。  
  
 **new** 和 **delete** 运算符还可用于内置类型（包括数组）。  如果 `pointer` 指的是某一数组，请在 `pointer` 前放置空括号：  
  
```  
int* set = new int[100];  
//use set[]  
delete [] set;  
```  
  
 对对象使用 **delete** 运算符将释放其内存。  在删除对象后取消引用指针的程序可能会产生不可预知的结果或崩溃。  
  
 将 **delete** 用于释放 C\+\+ 类对象的内存时，将在释放该对象的内存之前调用该对象的析构函数（如果该对象具有析构函数）。  
  
 如果 **delete** 运算符的操作数是可修改的左值，则在删除该对象后未定义其值。  
  
## 使用 delete  
 [delete 运算符](../cpp/delete-operator-cpp.md)有两个语法变体：一个针对单一对象，另一个针对对象数组。  以下代码片段演示了它们之间的差异：  
  
```  
// expre_Using_delete.cpp  
struct UDType   
{  
};  
  
int main()  
{  
   // Allocate a user-defined object, UDObject, and an object  
   //  of type double on the free store using the  
   //  new operator.  
   UDType *UDObject = new UDType;  
   double *dObject = new double;  
   // Delete the two objects.  
   delete UDObject;  
   delete dObject;   
   // Allocate an array of user-defined objects on the  
   // free store using the new operator.  
   UDType (*UDArr)[7] = new UDType[5][7];  
   // Use the array syntax to delete the array of objects.  
   delete [] UDArr;  
}  
```  
  
 以下两种情况会生成未定义的结果：在对象中使用 delete 的数组形式 \(delete \[ \]\)，并在数组中使用 delete 的非数组形式。  
  
## 示例  
 有关使用 **delete** 的示例，请参阅 [new 运算符](../cpp/new-operator-cpp.md)。  
  
## delete 的工作方式  
 [delete 运算符](../cpp/delete-operator-cpp.md)将调用函数[运算符 delete](../misc/operator-delete-function.md)。  
  
 对于不是类类型（[class](../cpp/class-cpp.md)、[struct](../cpp/struct-cpp.md) 或 [union](../cpp/unions.md)）的对象，将调用全局 delete 运算符。  对于类类型的对象，如果删除表达式以一元范围解析运算符 \(::\) 开始，则会在全局范围中解析释放函数的名称。  否则，delete 运算符将在释放内存之前为对象调用析构函数（如果指针不为 null）。  可为每个类定义 delete 运算符；如果给定类不存在这种定义，则会调用全局 delete 运算符。  如果删除表达式用于释放其静态对象具有虚拟析构函数的类对象，则将通过对象的动态类型的虚拟析构函数解析释放函数。  
  
## 请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [new 和 delete 运算符](../cpp/new-and-delete-operators.md)   
 [operator delete 函数](../misc/operator-delete-function.md)