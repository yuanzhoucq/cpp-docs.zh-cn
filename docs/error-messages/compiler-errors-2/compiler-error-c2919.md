---
title: 编译器错误 C2919 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2919
dev_langs:
- C++
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5e2eb2a32f1a906814f5b347ba1ebf13eba71ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245797"
---
# <a name="compiler-error-c2919"></a>编译器错误 C2919
“type”：不能在 WinRT 类型的发布接口上使用运算符  
  
 Windows 运行时类型系统不支持某类型的发布接口中的运算符成员函数。 这是因为并非所有语言都能使用运算符成员函数。 你可以创建可从相同类或编译单元中的 C++ 代码调用的私有或内部运算符成员函数。  
  
 要修复此问题，请将运算符成员函数从公共接口中删除，或将其更改为命名成员函数。 例如，将成员函数命名为 `Equals`，而不是使用 `operator==`。