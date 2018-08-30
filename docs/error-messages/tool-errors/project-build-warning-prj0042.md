---
title: 项目生成警告 PRJ0042 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0042
dev_langs:
- C++
helpviewer_keywords:
- PRJ0042
ms.assetid: 682c9999-6f85-409f-b102-00c93243f74f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 260da8ac336c640ea875610b2c62e6c42c7d335e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211345"
---
# <a name="project-build-warning-prj0042"></a>项目生成警告 PRJ0042

> 文件的自定义生成步骤的输出属性*文件*未设置。 将跳过自定义生成步骤。

未执行的自定义生成步骤，因为未指定输出。

若要解决此错误，请执行下列操作之一：

- 从生成中排除自定义生成步骤。

- 添加输出。

- 删除自定义生成步骤的命令的内容。