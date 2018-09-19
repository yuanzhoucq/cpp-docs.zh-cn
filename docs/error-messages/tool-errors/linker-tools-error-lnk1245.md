---
title: 链接器工具错误 LNK1245 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef7bace5cec937399d7a2ed440e21b9b751f4141
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041787"
---
# <a name="linker-tools-error-lnk1245"></a>链接器工具错误 LNK1245

无效的子系统子系统指定任何引用;/SUBSYSTEM 必须是 WINDOWS、 WINDOWSCE 或 CONSOLE

[/clr](../../build/reference/clr-common-language-runtime-compilation.md)用于编译对象和以下条件之一为 true:

- 定义自定义入口点 ([/ENTRY](../../build/reference/entry-entry-point-symbol.md))，以便链接器无法推导出子系统。

- 一个值传递给[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)不能用于 /clr 对象的链接器选项。

对于这两种情况，解决方法是指定于 /SUBSYSTEM 链接器选项的有效值。