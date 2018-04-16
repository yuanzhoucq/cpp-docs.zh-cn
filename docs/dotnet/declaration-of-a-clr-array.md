---
title: CLR 数组的声明 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3f263227d437ddafb65ac3da0829414e4af05855
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="declaration-of-a-clr-array"></a>CLR 数组的声明
声明的语法，实例化，并初始化托管的数组已从更改托管扩展的 c + + 为 Visual c + +。  
  
 托管扩展中的 CLR 数组对象的声明是在其中的标准数组声明的扩展，`__gc`关键字被放置数组对象的名称和其可能逗号填充的维数，如下所示以下两个之间示例：  
  
```  
void PrintValues( Object* myArr __gc[]);  
void PrintValues( int myArr __gc[,,]);  
```  
  
 这也已简化在新语法中，我们在其中使用相似的模板的声明类似于 c + + 标准库`vector`声明。 第一个参数指示的元素类型。 第二个参数指定数组维度 （默认值为 1，因此仅多个维度都要求第二个参数）。 Array 对象本身是跟踪句柄，并因此必须指定乘幂号的。 如果元素类型也是一个引用类型，它还要求乘幂号的。 例如，上面的示例中，当在新语法中，表示将如下所示：  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
 由于是引用类型的跟踪句柄，而不是对象，则可以指定为一个函数的返回类型的 CLR 数组。 （与此相反，它不是可以指定本机数组作为函数的返回类型。）执行此操作在托管扩展中的语法已某种程度上的非直观。 例如:  
  
```  
Int32 f() [];  
int GetArray() __gc[];  
```  
  
 Visual c + + 中的声明不要简单得多。 例如，应用于对象的  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
 在这两个版本的语言，本地托管数组的速记初始化受到支持。 例如:  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = {   
      __box(26), __box(27), __box(28), __box(29), __box(30)  
   };  
   return a1;  
}  
```  
  
 显著地简化的新语法中 (请注意，因为装箱是隐式在新语法中，`__box`已消除运算符-请参阅[值类型和他们的行为 (C + + /cli CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)的讨论):  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
   return a1;  
}  
```  
  
 数组是 CLR 引用类型，因为每个数组对象的声明是跟踪句柄。 因此，必须在 CLR 堆上分配数组对象。 （速记表示法隐藏托管的堆分配。）下面是在托管扩展中的数组对象初始化的显式形式：  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 在新语法中，`new`表达式替换`gcnew`。 维度大小作为参数传递`gcnew`表达式，如下所示：  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 在新语法中，可以遵循的显式初始化列表`gcnew`表达式; 这不支持在托管扩展中。 例如:  
  
```  
// explicit initialization list following gcnew   
// was not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="see-also"></a>请参阅  
 [托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)   
 [数组](../windows/arrays-cpp-component-extensions.md)