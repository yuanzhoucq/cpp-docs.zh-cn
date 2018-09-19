---
title: BSCMAKE 错误 BK1503 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16bf228804cb24f4fe7a2428dc581116d4cec91d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064656"
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE 错误 BK1503

无法写入文件 filename [: 原因]

BSCMAKE 将合并到一个数据库中浏览器在编译期间生成的.sbr 文件。 如果生成的浏览器数据库超过 64 MB，或输入 (.sbr) 文件数超过 4092，将发出此错误。

如果问题由多个 4092.sbr 文件引起的您必须减小输入文件的数目。 从 Visual Studio 中，这可以通过实现[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)整个项目，然后重新检查上文件来完成。

如果问题由.bsc 文件大于 64 MB，减少的.sbr 文件作为输入将减少生成的.bsc 文件的大小。 此外，通过使用/e m （排除宏扩展符号）、 /El （排除本地变量） 和 /Es （排除系统文件） 可能会降低的浏览信息的量。

## <a name="see-also"></a>请参阅

[BSCMAKE 选项](../../build/reference/bscmake-options.md)