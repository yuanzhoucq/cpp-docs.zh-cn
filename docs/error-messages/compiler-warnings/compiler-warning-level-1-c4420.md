---
title: 编译器警告 （等级 1） C4420 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98336a30e7174b62df48e93a04ba9ee7ddcc919a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279105"
---
# <a name="compiler-warning-level-1-c4420"></a>编译器警告（等级 1）C4420
operator： 运算符不可用，改为; 使用 operator运行时检查可能已泄露  
  
 当你使用时，会生成此警告[/RTCv](../../build/reference/rtc-run-time-error-checks.md) （矢量检查新/删除） 并且在发现没有向量形式。 在这种情况下，使用非向量窗体。  
  
 为了使 /RTCv 正常工作，编译器应始终调用矢量形式的[新](../../cpp/new-operator-cpp.md)/[删除](../../cpp/delete-operator-cpp.md)如果时使用的矢量语法。