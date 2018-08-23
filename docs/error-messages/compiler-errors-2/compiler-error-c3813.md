---
title: 编译器错误 C3813 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e947b281c90c4d2ace83971f1de972c29bde72ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273102"
---
# <a name="compiler-error-c3813"></a>编译器错误 C3813
属性声明只能在托管类型或 WinRT 类型的定义内出现  
  
A[属性](../../dotnet/how-to-use-properties-in-cpp-cli.md)仅可以在托管或 Windows 运行时内声明类型。 本机类型不支持 `property` 关键字。  
  
## <a name="example"></a>示例  
下面的示例生成 C3813，并演示如何修复此错误：  
  
```cpp  
// C3813.cpp  
// compile by using: cl /c /clr C3813.cpp  
class A  
{  
   property int Int; // C3813  
};  
  
ref class B  
{  
   property int Int; // OK - declared within managed type  
};  
```