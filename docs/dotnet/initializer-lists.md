---
title: 初始值设定项列表 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 981f2737d370dc25ca4e7dc6c20947b3867a0c65
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394603"
---
# <a name="initializer-lists"></a>初始值设定项列表

先于基类构造函数现在称为构造函数中的初始值设定项列表。

## <a name="remarks"></a>备注

在 Visual c + + 2005 中之前, 基类构造函数初始值设定项列表之前时调用编译为 c + + 托管扩展。 现在，使用编译时 **/clr**，首先调用初始值设定项列表。

## <a name="see-also"></a>请参阅

[常规语言更改 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)