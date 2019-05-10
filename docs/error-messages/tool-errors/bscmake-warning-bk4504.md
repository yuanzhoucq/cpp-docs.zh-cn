---
title: BSCMAKE 警告 BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 7ffcb7c2e6ae512006ccd29c87b05c53fdfcaef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279283"
---
# <a name="bscmake-warning-bk4504"></a>BSCMAKE 警告 BK4504

文件包含引用太多;正在忽略来自此源的更多参考

.cpp 文件包含 64,000 个以上的符号引用。 当 BSCMAKE 在某个文件中遇到 64,000 个引用之后，它将会忽略所有后续的引用。

若要更正此问题，请将该文件拆分为两个或更多文件（每个文件包含 64,000 个以下的符号引用），或使用 `#pragma component(browser)` 预处理器指令限制为特定引用生成的符号。 有关详细信息，请参阅[组件](../../preprocessor/component.md)。