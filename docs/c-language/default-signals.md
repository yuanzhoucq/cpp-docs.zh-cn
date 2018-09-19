---
title: 默认信号 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- default signals
- defaults, signals
ms.assetid: db9fc17b-75c0-4d33-86be-c536584bbede
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ff2612538cd6953672d9f91dcb603b4676be100
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098916"
---
# <a name="default-signals"></a>默认信号

ANSI 4.7.1.1 调用信号处理程序前未执行 `signal(sig, SIG_DFL)` 的等效项时，对所执行信号的阻止

程序开始运行时，信号将设置为其默认状态。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)