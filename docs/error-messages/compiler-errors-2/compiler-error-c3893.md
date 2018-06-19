---
title: 编译器错误 C3893 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3893
dev_langs:
- C++
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c95d44a90b9325a492a0f179c941d46ff24030c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273418"
---
# <a name="compiler-error-c3893"></a>编译器错误 C3893
var： 左值使用 initonly 数据成员仅允许用在类类型 _ 名称的实例构造函数  
  
 静态[initonly](../../dotnet/initonly-cpp-cli.md)数据成员只能在静态构造函数采用其地址。  
  
 实例 （非静态） initonly 数据成员只能在实例 （非静态） 构造函数采用其地址。  
  
 下面的示例生成 C3893:  
  
```  
// C3893.cpp  
// compile with: /clr  
ref struct Y1 {  
   Y1() : data_var(0) {  
      int% i = data_var;   // OK  
   }  
   initonly int data_var;  
};  
  
int main(){  
   Y1^ y= gcnew Y1;  
   int% i = y->data_var;   // C3893  
}  
```