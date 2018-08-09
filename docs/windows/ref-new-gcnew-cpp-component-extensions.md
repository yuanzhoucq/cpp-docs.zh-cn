---
title: ref new、 gcnew （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
dev_langs:
- C++
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed742d3762232846b2cac189978ea07c140b65f2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012652"
---
# <a name="ref-new-gcnew--c-component-extensions"></a>ref new、gcnew（C++ 组件扩展）
**新的 ref**聚合关键字分配进行垃圾回收时，对象将变为不可访问，并返回一个句柄类型的实例 ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) 已分配对象。  
  
## <a name="all-runtimes"></a>所有运行时  
 分配的类型的实例的内存**ref 新**会自动释放。  
  
 一个**新的 ref**操作，则会引发`OutOfMemoryException`如果无法分配内存。  
  
 有关如何分配和释放本机 c + + 类型的内存的详细信息，请参阅[新和 delete 运算符](../cpp/new-and-delete-operators.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 使用**ref 新**分配内存来存放 Windows 运行时对象想要自动管理其生存期。 对象会在其引用计数变为零（这会在引用的最后一个副本超出范围之后发生）时自动释放。 有关详细信息，请参阅[Ref 类和结构](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)。  
  
### <a name="requirements"></a>要求  
 编译器选项：`/ZW`  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 分配的托管类型 （引用或值类型） 的内存**gcnew**，并且通过使用垃圾回收已解除分配。  
  
### <a name="requirements"></a>要求  
 编译器选项：`/clr`  
  
### <a name="examples"></a>示例  
  
 下面的示例使用**gcnew**分配消息对象。  
  
```cpp  
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
  
 下面的示例使用**gcnew**创建使用类似于引用类型的装箱的值类型。  
  
```cpp  
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
  
```Output  
32  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)