---
title: 库结构 |Microsoft 文档
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
ms.openlocfilehash: 6eff0000aef01790106b44b49b4855218fcf9332
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373096"
---
# <a name="structure-of-a-library"></a>库结构
库包含 COFF 对象。 库中的对象包含函数和程序中的其他对象可以从外部引用的数据。 有时，库中的对象称为库成员。  
  
 你可以通过使用 /LINKERMEMBER 选项运行 DUMPBIN 工具获取有关内容库的其他信息。 有关此选项的详细信息，请参阅[DUMPBIN 参考](../../build/reference/dumpbin-reference.md)。  
  
## <a name="see-also"></a>请参阅  
 [LIB 概述](../../build/reference/overview-of-lib.md)