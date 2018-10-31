---
title: 资源编译器错误 RC1015 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0456845152fb2879d2f58c9c40af2562c7207535
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890239"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>资源编译器错误 RC1015

无法打开包含文件 filename

给定的包含文件不存在、 无法打开或找不到。

确保环境设置有效，并且已为该文件指定了正确的路径。 请确保足够的文件句柄可供资源编译器。 如果文件位于网络驱动器上，请确保您有权打开该文件。

在“配置属性”->“资源”->“常规”属性页中可配置“附加包含目录”，即使包含文件存在于该“附加包含目录”所指定的目录中，也可能发生 RC1015；请指定包含文件的完整路径。
