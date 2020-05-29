---
title: 编译器警告（等级3） C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 38b346e0a90729bda431b9cb578a03806be1ea4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198973"
---
# <a name="compiler-warning-level-3-c4192"></a>编译器警告（等级3） C4192

导入类型库 "库" 时自动排除 "name"

`#import` 库包含在 Win32 系统标头中也进行了定义的项 "*名称*"。 由于类型库的限制，通常在类型库中定义**IUnknown**或 GUID 等名称，从系统标头复制定义。 `#import` 将检测这些项，并拒绝将它们合并到 .tlh 和 .tli 标头文件中。

若要重写此行为，请使用 `#import` 特性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)并[包括（）](../../preprocessor/include-parens.md)。
