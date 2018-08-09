---
title: 如何： 声明和使用内部指针及托管的数组 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, interior
- arrays [C++], managed
ms.assetid: e61a2c09-a7d0-4867-91ea-6b8788a01079
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45cfc4374b9779a61e3ea97c829317b9d4fe75ba
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016156"
---
# <a name="how-to-declare-and-use-interior-pointers-and-managed-arrays-ccli"></a>如何：声明和使用内部指针及托管数组 (C++/CLI)
以下 C + + /cli CLI 示例演示如何声明和使用内部指针到一个数组。  
  
> [!IMPORTANT]
>  `/clr` 编译器选项支持此语言功能，但是 `/ZW` 编译器选项不支持此语言功能。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
```cpp  
// interior_ptr_arrays.cpp  
// compile with: /clr  
#define SIZE 10  
  
int main() {  
   // declare the array  
   array<int>^ arr = gcnew array<int>(SIZE);  
  
   // initialize the array  
   for (int i = 0 ; i < SIZE ; i++)  
      arr[i] = i + 1;  
  
   // create an interior pointer into the array  
   interior_ptr<int> ipi = &arr[0];  
  
   System::Console::WriteLine("1st element in arr holds: {0}", arr[0]);  
   System::Console::WriteLine("ipi points to memory address whose value is: {0}", *ipi);  
  
   ipi++;  
   System::Console::WriteLine("after incrementing ipi, it points to memory address whose value is: {0}", *ipi);  
}  
```  
  
```Output  
1st element in arr holds: 1  
ipi points to memory address whose value is: 1  
after incrementing ipi, it points to memory address whose value is: 2  
```  
  
## <a name="see-also"></a>请参阅  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)