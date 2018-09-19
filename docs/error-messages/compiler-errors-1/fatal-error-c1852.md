---
title: 错误 C1852 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1852
dev_langs:
- C++
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0adfa7eed25f1902300fa2378b8ffc19eb8dfafd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023795"
---
# <a name="fatal-error-c1852"></a>错误 C1852

“filename”不是有效的预编译头文件

文件不是预编译头文件。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 使用 **/Yu** 或 **#pragma hdrstop**指定的无效文件。

1. 如果未另行指定，编译器将假定 .pch 为文件扩展名。