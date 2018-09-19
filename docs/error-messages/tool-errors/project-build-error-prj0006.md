---
title: 项目生成错误 PRJ0006 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 264b2f90a2d778b1545117ce5c3b1272626ebad6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073247"
---
# <a name="project-build-error-prj0006"></a>项目生成错误 PRJ0006

无法打开临时文件 file。 请确保该文件存在并且，目录未被写保护。

Visual c + + 无法在生成过程中创建临时文件。 其中的原因包括：

- 没有临时目录。

- 只读的临时目录。

- 磁盘空间不足。

- $ （intdir） 文件夹是只读的或包含临时文件的都是只读的。

以下错误 PRJ0007 也将出现此错误： 无法创建输出目录 directory。 错误 PRJ0007 意味着无法创建 $ （intdir） 目录，这意味着临时文件的创建也将失败。

在指定时，会创建临时文件：

- 响应文件。

- 一个自定义生成步骤。

- 生成事件。