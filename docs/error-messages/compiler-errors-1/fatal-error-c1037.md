---
title: 错误 C1037 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1037
dev_langs:
- C++
helpviewer_keywords:
- C1037
ms.assetid: 79103bca-ccfb-42e7-aef9-9b90c15b162f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8091eb7316531c6bdda9bf714ec7a195b5406182
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047676"
---
# <a name="fatal-error-c1037"></a>错误 C1037

无法打开对象文件的文件名

无法打开由 [/Fo](../../build/reference/fo-object-file-name.md) 指定的对象文件。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 文件名无效。

1. 内存不足，无法打开该文件。

1. 另一个进程正在使用该文件。

1. 一个只读文件具有相同的名称。

