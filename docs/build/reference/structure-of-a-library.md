---
title: 库结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- libraries, structure
ms.assetid: a5fda8e8-4a1b-4499-9095-0df935262ce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03c2c66d45ee415ddc4f3ba27b6a100c5e2ec1dc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702099"
---
# <a name="structure-of-a-library"></a>库结构

库包含 COFF 对象。 库中的对象包含函数和程序中的其他对象可以从外部引用的数据。 有时，库中的对象称为库成员。

可以通过使用 /LINKERMEMBER 选项运行 DUMPBIN 工具来获取内容库的其他信息。 有关此选项的详细信息，请参阅[DUMPBIN 参考](../../build/reference/dumpbin-reference.md)。

## <a name="see-also"></a>请参阅

[LIB 概述](../../build/reference/overview-of-lib.md)