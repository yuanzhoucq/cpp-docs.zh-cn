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
ms.openlocfilehash: 7a72cba53ebe9a286ac2e7cbbf2c41b78f4e4e08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100749"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>资源编译器错误 RC1015

无法打开包含文件 filename

给定的包含文件不存在、 无法打开或找不到。

确保环境设置有效，并且已为该文件指定了正确的路径。 请确保足够的文件句柄可供资源编译器。 如果文件位于网络驱动器上，请确保您有权打开该文件。

在“配置属性”->“资源”->“常规”属性页中可配置“附加包含目录”，即使包含文件存在于该“附加包含目录”所指定的目录中，也可能发生 RC1015；请指定包含文件的完整路径。

有关详细信息，请参阅知识库文章 Q326987: RC1015 错误时使用资源视图包含路径是否太长。