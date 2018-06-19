---
title: 编译器错误 C2592 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2592
dev_langs:
- C++
helpviewer_keywords:
- C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d999056d718d9c7aad93d08a99895caebbef539
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229808"
---
# <a name="compiler-error-c2592"></a>编译器错误 C2592
“class”：“base_class_2” 继承自“base_class_1”，无法重新指定  
  
 你仅可指定不是继承自其他基类的基类。 在此情况下，`class` 的规范中仅需要 `base_class_1`，因为 `base_class_1` 已继承 `base_class_2`。