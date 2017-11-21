---
title: "编译器警告 （等级 4） C4559 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4559
dev_langs: C++
helpviewer_keywords: C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 046a3186554603d4a33b2eec78084dd76ec64e40
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4559"></a>编译器警告（等级 4）C4559
function： 重定义;函数提升 __declspec(modifier)  
  
 已重新定义函数或将其重新声明和第二个定义或声明添加 __**declspec**修饰符 (***修饰符***)。 此警告为信息性。 若要解决此警告，请删除其中一个定义。  
  
 下面的示例生成 C4559:  
  
```  
// C4559.cpp  
// compile with: /W4 /LD  
void f();  
__declspec(noalias) void f();   // C4559  
```