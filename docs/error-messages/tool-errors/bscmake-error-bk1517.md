---
title: BSCMAKE 错误 BK1517
ms.date: 11/04/2016
f1_keywords:
- BK1517
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
ms.openlocfilehash: 455e028a72cce132c49e0d0d778628ee21bf3a0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380521"
---
# <a name="bscmake-error-bk1517"></a>BSCMAKE 错误 BK1517

sbrfile 用 /Yc 和 /Yu 编译的源文件

.Sbr 文件引用自身。 它用 /Yc 编译后用 /Yu 可能重新编译。 为源文件编译器选项重置为 /Yc，然后选择**重新生成**生成新的.sbr 文件。 没有重新编译用 /Yu 源文件。