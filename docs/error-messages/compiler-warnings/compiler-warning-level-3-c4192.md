---
title: 编译器警告 （等级 3） C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 56b27596296b87edcc6de406e7b6621d5723815d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402224"
---
# <a name="compiler-warning-level-3-c4192"></a>编译器警告 （等级 3） C4192

自动导入类型库库时排除 name

一个`#import`库包含的项，*名称*，即也在 Win32 系统标头中定义。 由于类型库的限制，名称如**IUnknown**或 GUID 通常定义在类型库中，复制系统标头中的定义。 `#import` 将检测这些项，并拒绝将其合并.tlh 和.tli 标头文件中。

若要重写此行为，请使用`#import`特性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)并[include （)](../../preprocessor/include-parens.md)。