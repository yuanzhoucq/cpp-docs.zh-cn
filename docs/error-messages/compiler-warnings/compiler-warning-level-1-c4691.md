---
title: "编译器警告 （等级 1） C4691 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4691
dev_langs: C++
helpviewer_keywords: C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17673ee3e65d2e0cd0d989c56759b62de38f5fdc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4691"></a>编译器警告（等级 1）C4691
type： 在未引用程序集 file，而是使用了当前翻译单元中定义的类型应引用的类型  
  
 不引用包含原始的类型定义的元数据文件，且编译器使用局部类型定义。  
  
 在这种情况，在重新生成其中*文件*，可以忽略或关闭了杂注 C4691[警告](../../preprocessor/warning.md)。  也就是说，如果要生成的文件同名编译器需要找到的类型定义的文件，你可以忽略 C4691。  
  
 但是，如果编译器使用不是来自同一元数据; 中引用的程序集的定义发生意外的行为可以CLR 类型被类型以及类型的名称，不仅能还由程序集。  即，从程序集 z.dll 类型 Z 是不同的程序集 y.dll 中的类型 Z。  
  
## <a name="example"></a>示例  
 此示例包含原始的类型定义。  
  
```  
// C4691_a.cpp  
// compile with: /clr /LD /W1  
public ref class Original_Type {};  
```  
  
## <a name="example"></a>示例  
 此示例引用 C4691_a.dll 并声明类型 Original_Type 的字段。  
  
```  
// C4691_b.cpp  
// compile with: /clr /LD  
#using "C4691_a.dll"  
public ref class Client {  
public:  
   Original_Type^ ot;  
};  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C4691。  请注意此示例包含一个定义 Original_Type 并不引用 C4691a.dll。  
  
 若要解决，引用包含原始的类型定义的元数据文件并删除本地声明和定义。  
  
```  
// C4691_c.cpp  
// compile with: /clr /LD /W1  
// C4691 expected  
  
// Uncomment the following line to resolve.  
// #using "C4691_a.dll"  
#using "C4691_b.dll"  
  
// Delete the following line to resolve.  
ref class Original_Type;  
  
public ref class MyClass : Client {};  
```