---
title: 项目生成错误 PRJ0044 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0044
dev_langs:
- C++
helpviewer_keywords:
- PRJ0044
ms.assetid: 5d78c45a-f9e9-4d2b-a3b6-5a5d1421ab84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac5ac11ae8622e2f153effd2cfb5ab0055414331
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028481"
---
# <a name="project-build-error-prj0044"></a>项目生成错误 PRJ0044

自定义生成规则 rule 分配给文件 file 的附加依赖项属性无效。 该属性包含计算结果为“value”的“string”。

**附加依赖项**属性的计算结果为空字符串，或包含无效字符 （任何字符都不能在文件或目录的名称） 的字符串。 自定义生成规则需要生成操作的输出。

有关详细信息，请参阅[指定自定义生成工具](../../ide/specifying-custom-build-tools.md)。

## <a name="see-also"></a>请参阅

[项目生成错误和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)