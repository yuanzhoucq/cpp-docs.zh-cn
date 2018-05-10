---
title: 如何： 声明和使用内部指针及托管的数组 (C + + /cli CLI) |Microsoft 文档
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
ms.openlocfilehash: 457cec66aaabb01b9c10ccc66a8f9594312195b4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-declare-and-use-interior-pointers-and-managed-arrays-ccli"></a>如何：声明和使用内部指针及托管数组 (C++/CLI)
以下 C + + /cli CLI 示例演示如何声明和使用内部指针到一个数组。  
  
> [!IMPORTANT]
>  通过支持此语言功能 **/clr**编译器选项，但不是 **/ZW**编译器选项。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
```  
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
  
### <a name="output"></a>输出  
  
```  
1st element in arr holds: 1  
ipi points to memory address whose value is: 1  
after incrementing ipi, it points to memory address whose value is: 2  
```  
  
## <a name="see-also"></a>请参阅  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)