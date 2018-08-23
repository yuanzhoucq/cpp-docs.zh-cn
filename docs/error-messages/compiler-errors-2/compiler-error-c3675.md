---
title: 编译器错误 C3675 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4aaa53ae1d92364fad143f127ee3e7b504acdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273639"
---
# <a name="compiler-error-c3675"></a>编译器错误 C3675
function： 是保留的因为没有定义属性。  
  
 在声明简单属性时，编译器将生成 get 和 set 访问器方法，以及那些名称是你的程序的作用域中存在。  通过预先计算 get_ 和 set_ 到属性名称形成编译器生成的名称。  因此，不能声明具有同名的编译器生成的访问器函数。  
  
 有关更多信息，请参见 [property](../../windows/property-cpp-component-extensions.md) 。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3675。  
  
```  
// C3675.cpp  
// compile with: /clr /c  
ref struct C {  
public:  
   property int Size;  
   int get_Size() { return 0; }   // C3675  
};  
```