---
title: BSCMAKE 错误 BK1517
ms.date: 11/04/2016
f1_keywords:
- BK1517
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
ms.openlocfilehash: 47c99d21828512c063703edf541c017843708da5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197518"
---
# <a name="bscmake-error-bk1517"></a>BSCMAKE 错误 BK1517

同时用/Yc 和/Yu 编译的 sbrfile 源文件

.Sbr 文件引用自身。 在用/Yc. 编译后，很可能已通过/Yu 重新编译 将源文件的编译器选项重置为/Yc，然后选择 "**重新**生成" 以生成新的 .sbr 文件。 不要用/Yu. 重新编译源文件
