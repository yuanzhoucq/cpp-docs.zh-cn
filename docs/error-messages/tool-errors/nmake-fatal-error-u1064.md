---
title: NMAKE 错误 U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: bfc42c458c1932287f17f367d09c4b23c2c201a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182820"
---
# <a name="nmake-fatal-error-u1064"></a>NMAKE 错误 U1064

找不到生成文件并且未指定目标

NMAKE 命令行未指定生成文件或目标，并且当前目录不包含名为生成文件的文件。

NMAKE 需要生成文件或命令行目标（或两者）。 若要生成可用于 NMAKE 的生成文件，请指定/F 选项，或在当前目录中放置一个名为 "生成文件" 的文件。 如果未提供生成文件，NMAKE 可以使用推理规则创建命令行目标。
