---
title: 编译器错误 C3715 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9412592ac177fb49f065975db469c9f77b98e8c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265891"
---
# <a name="compiler-error-c3715"></a>编译器错误 C3715
指针： 必须是指向 class  
  
 指定中的指针[__hook](../../cpp/hook.md)或[__unhook](../../cpp/unhook.md)包含不指向有效的类。 若要解决此错误，请确保你`__hook`和`__unhook`调用对指定指向有效的类的指针。