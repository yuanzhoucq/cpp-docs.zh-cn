---
title: 项目生成错误 PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: d62c774411fda80a3e94044b3272567177328ff5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451554"
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