---
title: 项目生成错误 PRJ0033 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0033
dev_langs:
- C++
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c70bd942123c48866c3353443b478de4953668de
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036067"
---
# <a name="project-build-error-prj0033"></a>项目生成错误 PRJ0033

自定义生成的附加依赖项属性 macro_expansion 到文件 file 包含宏的计算步骤。

对文件的自定义生成步骤中包含错误，其原因可能是宏评估问题的附加依赖项。 此错误还可能意味着路径有格式错误，其中包含的字符或在文件路径中是非法的字符的组合。

若要解决此错误，请修复该宏或修复所指定的路径。 计算出的路径是从项目目录的绝对路径。