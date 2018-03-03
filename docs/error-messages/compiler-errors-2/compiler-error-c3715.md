---
title: "编译器错误 C3715 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca60dcff0279982b01c70ee3c7603baf421bd434
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3715"></a>编译器错误 C3715
指针： 必须是指向 class  
  
 指定中的指针[__hook](../../cpp/hook.md)或[__unhook](../../cpp/unhook.md)包含不指向有效的类。 若要解决此错误，请确保你`__hook`和`__unhook`调用对指定指向有效的类的指针。