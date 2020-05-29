---
title: NMAKE 警告 U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: d59b5656d76025fa56bfc76bad800659f25acf53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193194"
---
# <a name="nmake-warning-u4004"></a>NMAKE 警告 U4004

目标 "targetname" 的规则太多

为给定目标指定了多个描述块，并使用了单个冒号（ **：** ）作为分隔符。 NMAKE 在第一个 description 块中执行了命令，并忽略了以后的块。

若要在多个依赖项中指定同一目标，请在每个依赖项行中使用双冒号（`::`）作为分隔符。
