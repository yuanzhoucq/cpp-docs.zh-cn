---
title: "编译器错误 C3893 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3893
dev_langs: C++
helpviewer_keywords: C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4fee017305c90d9da69f5432815c0005eb84352c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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