---
title: 编译器警告（等级 1）C4122
ms.date: 11/04/2016
f1_keywords:
- C4122
helpviewer_keywords:
- C4122
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
ms.openlocfilehash: bb5016bbf323057822c89a74001c75ab1855542c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380900"
---
# <a name="compiler-warning-level-1-c4122"></a>编译器警告（等级 1）C4122

“function”: alloc_text 仅适用于带 C 链接的函数

**alloc_text** 杂注仅适用于使用 **extern c**声明的函数。 它不能与外部 C++ 函数一起使用。

将忽略杂注。