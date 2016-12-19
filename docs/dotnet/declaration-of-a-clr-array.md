---
title: "CLR 数组的声明 | Microsoft Docs"
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
  - "array 关键字 [C++]"
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLR 数组的声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，声明、实例化和初始化托管数组的语法发生了更改。  
  
 托管扩展中 CLR 数组对象的声明是标准数组声明的扩展，其中 `__gc` 关键字被放置在数组对象名及其可能用逗号填充的维数之间，如以下两个示例所示：  
  
```  
void PrintValues( Object* myArr __gc[]);  
void PrintValues( int myArr __gc[,,]);  
```  
  
 这在新语法中已简化，在新语法中我们使用与 STL `vector` 声明相似的类似于模板的声明。  第一个参数指示元素类型。  第二个参数指定数组维数（默认值为 1，所以只有多维数组需要第二个变量）。  数组对象本身是一个跟踪句柄，所以必须为其赋予一个插入符号。  如果元素类型也是引用类型，则它还需要一个帽子。  例如，上面的示例在新的语法中的表示如下：  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
 由于引用类型是一个跟踪句柄而不是对象，可以将 CLR 数组指定为函数的返回类型。（相反，不能将本机数组指定为函数的返回类型。）在托管扩展中执行此操作的语法有不太直观。  例如：  
  
```  
Int32 f() [];  
int GetArray() __gc[];  
```  
  
 在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中，该声明简单很多。  例如，  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
 两种版本的语言中都支持局部托管数组的简短初始化。  例如：  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = {   
      __box(26), __box(27), __box(28), __box(29), __box(30)  
   };  
   return a1;  
}  
```  
  
 在新的语法中得到了显著地简化（请注意，由于在新的语法中装箱是隐式的，所以取消了 `__box` 运算符 — 有关讨论，请参见 [值类型及其行为 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)）：  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
   return a1;  
}  
```  
  
 由于数组是 CLR 引用类型，所以每个数组对象的声明都是一个跟踪句柄。  因此，数组对象必须在 CLR 堆上分配。（简短的表示法隐藏托管的堆分配。）以下代码是托管扩展下数组对象初始化的显式形式：  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 在新语法中，`new` 表达式由 `gcnew` 替换。  维数大小作为参数传递给了 `gcnew` 表达式，如下所示：  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 在新的语法中，显式初始化列表可以遵循 `gcnew` 表达式；托管扩展中不支持此功能。  例如：  
  
```  
// explicit initialization list following gcnew   
// was not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## 请参阅  
 [托管类型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [数组](../windows/arrays-cpp-component-extensions.md)