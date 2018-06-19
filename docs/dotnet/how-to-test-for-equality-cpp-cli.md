---
title: 如何： 测试相等性 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- equality, testing for
ms.assetid: 9115e298-9f75-452d-bdfb-6eeb0fa0b3c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0c32bd9c73b7251f311593b547d4f3abdd33d7c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127976"
---
# <a name="how-to-test-for-equality-ccli"></a>如何：测试相等性 (C++/CLI)
在下面的示例中，使用 Managed Extensions for c + + 的相等性测试将基于句柄的引用。  
  
## <a name="example"></a>示例  
  
```  
// mcppv2_equality_test.cpp  
// compile with: /clr /LD  
using namespace System;  
  
bool Test1() {  
   String ^ str1 = "test";  
   String ^ str2 = "test";  
   return (str1 == str2);  
}  
```  
  
 此程序 IL 显示返回的值通过使用 op_Equality 调用实现。  
  
```  
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,  
                                                               string)  
```  
  
## <a name="see-also"></a>请参阅  
 [托管类型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)