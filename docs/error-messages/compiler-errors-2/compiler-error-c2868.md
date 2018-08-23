---
title: 编译器错误 C2868 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84465453ca7a1d76a9dd6b199232384c2ef9124b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244360"
---
# <a name="compiler-error-c2868"></a>编译器错误 C2868  
  
> *标识符*： 非法使用声明语法; 预期的限定名称  
  
A [using 声明](../../cpp/using-declaration.md)需要*限定的名称*，范围运算符 (`::`) 分隔的命名空间、 类或枚举的名称标识符名称结尾的序列。 单个作用域解析运算符可能用于与全局命名空间中引入一个名称。  
  
## <a name="example"></a>示例  
  
下面的示例生成 C2868，并还显示正确用法：  
  
```cpp  
// C2868.cpp  
class X {  
public:  
   int i;  
};  
  
class Y : X {  
public:  
   using X::i;   // OK  
};  
  
int main() {  
   using X;   // C2868  
}  
```