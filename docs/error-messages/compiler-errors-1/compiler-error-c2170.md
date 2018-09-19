---
title: 编译器错误 C2170 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2170
dev_langs:
- C++
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b75d4c54bc6ec24cb182f3b6fb37ff4b8cd1ddfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055723"
---
# <a name="compiler-error-c2170"></a>编译器错误 C2170

identifier： 没有声明为一个函数，不能为内部函数

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 杂注`intrinsic`用于与函数之外的项。

1. 杂注`intrinsic`用于没有内部形式的函数。