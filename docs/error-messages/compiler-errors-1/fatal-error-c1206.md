---
title: 错误 C1206 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1206
dev_langs:
- C++
helpviewer_keywords:
- C1206
ms.assetid: 2211428f-ad86-4f7b-82eb-f1ba89b0510e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79aa3f33f076b6576363b0bdda63e55c5d9f13fd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046454"
---
# <a name="fatal-error-c1206"></a>错误 C1206

安装的运行时版本不支持 per-appdomain 数据

某些功能（如每个应用程序域数据）只由支持该功能的公共语言运行库支持。

C1206 指出计算机上未安装运行库的最新版本。 请安装适用于你的编译器的公共语言运行时版本。

有关更多信息，请参见 [appdomain](../../cpp/appdomain.md) 。