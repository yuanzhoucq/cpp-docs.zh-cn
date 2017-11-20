---
title: "编译器错误 C2834 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2834
dev_langs: C++
helpviewer_keywords: C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5b85b01fa832b0d14d01b6b7cbb5ef65107177ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2834"></a>编译器错误 C2834
operator operator 必须是全局限定  
  
 `new`和`delete`运算符被绑定到类驻留的位置。 范围解析不能用于选择的版本`new`或`delete`从另一个类。 若要实现的多个窗体`new`或`delete`运算符，带有额外形参创建运算符的版本。