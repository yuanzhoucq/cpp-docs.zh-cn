---
title: BSCMAKE 错误 BK1517 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1517
dev_langs:
- C++
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 941773fbcf65a3b1c1a6041a1e7a067cfc286823
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097050"
---
# <a name="bscmake-error-bk1517"></a>BSCMAKE 错误 BK1517

sbrfile 用 /Yc 和 /Yu 编译的源文件

.Sbr 文件引用自身。 它用 /Yc 编译后用 /Yu 可能重新编译。 为源文件编译器选项重置为 /Yc，然后选择**重新生成**生成新的.sbr 文件。 没有重新编译用 /Yu 源文件。