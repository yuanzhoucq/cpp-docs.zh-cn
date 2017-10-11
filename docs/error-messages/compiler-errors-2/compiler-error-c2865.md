---
title: "编译器错误 C2865 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5cbe54ebcae8753c0c5b6701ca839202ba7da533
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2865"></a>编译器错误 C2865
function： 非法 handle_or_pointer 比较  
  
 你可以比较对引用[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)或托管仅对是否相等的引用类型以查看它们是否引用同一对象 （= =） 或不同的对象 (！ =)。  
  
 无法比较它们的排序，因为.NET 运行时可能会将托管的对象移动任何时候，从而更改测试的结果。
