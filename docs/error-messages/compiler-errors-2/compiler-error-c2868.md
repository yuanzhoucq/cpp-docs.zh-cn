---
title: "编译器错误 C2868 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7255aa3e73e23109535ae0e83d6e9bd907cdbcd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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