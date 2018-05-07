---
title: 编译器错误 C3161 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2d7aff3eb41c03f5be774704922340ac54126fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3161"></a>编译器错误 C3161
interface： 嵌套类、 结构、 联合或接口中的接口是非法的;嵌套接口类、 结构或联合中的是非法  
  
 [__Interface](../../cpp/interface.md)只能出现在全局范围内或在某个命名空间。 类、 结构或联合不能出现在接口中。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3161。  
  
```  
// C3161.cpp  
// compile with: /c  
__interface X {  
   __interface Y {};   // C3161 A nested interface  
};  
```