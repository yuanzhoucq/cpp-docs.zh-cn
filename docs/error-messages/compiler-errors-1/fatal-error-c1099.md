---
title: 错误 C1099
ms.date: 11/04/2016
f1_keywords:
- C1099
helpviewer_keywords:
- C1099
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
ms.openlocfilehash: 673a54f705a8ff46ad94167a4458ab538df69c88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611024"
---
# <a name="fatal-error-c1099"></a>错误 C1099

“编辑并继续”引擎正在终止编译

“编辑并继续”在准备进行编译代码更改的过程中加载了一个预编译头文件，但后续操作（例如预编译头 `#include` 语句前的代码更改或停止调试器）阻止“编辑并继续”使用该进程完成编译。 不需要执行任何操作来修复此错误。