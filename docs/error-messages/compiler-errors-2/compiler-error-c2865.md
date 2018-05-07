---
title: 编译器错误 C2865 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70b2c6c831fde18f9054e139a120d834a75b6950
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2865"></a>编译器错误 C2865
function： 非法 handle_or_pointer 比较  
  
 你可以比较对引用[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)或托管仅对是否相等的引用类型以查看它们是否引用同一对象 （= =） 或不同的对象 (！ =)。  
  
 无法比较它们的排序，因为.NET 运行时可能会将托管的对象移动任何时候，从而更改测试的结果。