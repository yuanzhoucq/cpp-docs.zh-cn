---
title: BSCMAKE 警告 BK4504 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a2da8903dade37faf3b14175b65f3169efd908
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049758"
---
# <a name="bscmake-warning-bk4504"></a>BSCMAKE 警告 BK4504

文件包含引用太多;正在忽略来自此源的更多参考

.cpp 文件包含 64,000 个以上的符号引用。 当 BSCMAKE 在某个文件中遇到 64,000 个引用之后，它将会忽略所有后续的引用。

若要更正此问题，请将该文件拆分为两个或更多文件（每个文件包含 64,000 个以下的符号引用），或使用 `#pragma component(browser)` 预处理器指令限制为特定引用生成的符号。 有关详细信息，请参阅[组件](../../preprocessor/component.md)。