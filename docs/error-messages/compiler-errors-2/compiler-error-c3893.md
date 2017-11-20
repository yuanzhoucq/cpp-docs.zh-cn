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
ms.openlocfilehash: 49097d988175e7571c5825b4d54e1dd496fb2ba7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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