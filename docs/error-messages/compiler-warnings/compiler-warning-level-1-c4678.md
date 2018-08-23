---
title: 编译器警告 （等级 1） C4678 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73871d69198752e12a629d441982c2da47146517
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284233"
---
# <a name="compiler-warning-level-1-c4678"></a>编译器警告（等级 1）C4678
基类“base_type”的可访问性比“derived_type”低  
  
某个公共类型是从私有类型派生的。 如果在引用的程序集中实例化该公共类型，将无法访问私有基类型的成员。  
  
C4678 才可访问使用过时的编译器选项 **/clr:oldSyntax**。 使用时，则会出错 **/clr**来获得可访问性的基类，其派生的类。  
