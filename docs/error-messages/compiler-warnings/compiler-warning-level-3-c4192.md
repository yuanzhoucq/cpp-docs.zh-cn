---
title: 编译器警告 （等级 3） C4192 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 671a8c83dcadcaa89372e53b6c3d677c5810b4a5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114405"
---
# <a name="compiler-warning-level-3-c4192"></a>编译器警告 （等级 3） C4192

自动导入类型库库时排除 name

一个`#import`库包含的项，*名称*，即也在 Win32 系统标头中定义。 由于类型库的限制，名称如**IUnknown**或 GUID 通常定义在类型库中，复制系统标头中的定义。 `#import` 将检测这些项，并拒绝将其合并.tlh 和.tli 标头文件中。

若要重写此行为，请使用`#import`特性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)并[include （)](../../preprocessor/include-parens.md)。