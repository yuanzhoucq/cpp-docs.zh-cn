---
title: 项目生成警告 PRJ0029 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0029
dev_langs:
- C++
helpviewer_keywords:
- PRJ0029
ms.assetid: f02c09c6-09f3-4d44-8cd4-9a25336be1ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 854120bf6021295348ff2e28b36f7b44007017b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025995"
---
# <a name="project-build-warning-prj0029"></a>项目生成警告 PRJ0029

项目级自定义生成步骤的输出属性未设置。 将跳过自定义生成步骤。

未执行的自定义生成步骤，因为未指定输出。

若要解决此错误，请执行下列操作之一：

- 从生成中排除自定义生成步骤。

- 添加输出。

- 删除自定义生成步骤的命令的内容。