---
title: 错误 C1099 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1099
dev_langs:
- C++
helpviewer_keywords:
- C1099
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5c975960310136729620ae8304364667f6e8e60
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045037"
---
# <a name="fatal-error-c1099"></a>错误 C1099

“编辑并继续”引擎正在终止编译

“编辑并继续”在准备进行编译代码更改的过程中加载了一个预编译头文件，但后续操作（例如预编译头 `#include` 语句前的代码更改或停止调试器）阻止“编辑并继续”使用该进程完成编译。 不需要执行任何操作来修复此错误。