---
title: "编译器错误 C2846 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2846
dev_langs: C++
helpviewer_keywords: C2846
ms.assetid: bc090ec2-5410-4112-9ec6-261325374375
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a22a56547352076b10010f93a9d4c9a72f9ca78a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2846"></a>编译器错误 C2846
constructor： 接口不能有一个构造函数  
  
 Visual c + +[接口](../../cpp/interface.md)不能有一个构造函数。  
  
 下面的示例生成 C2846:  
  
```  
// C2846.cpp  
// compile with: /c  
__interface C {  
   C();   // C2846 constructor not allowed in an interface  
};  
```