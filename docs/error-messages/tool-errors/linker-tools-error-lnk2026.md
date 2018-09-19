---
title: 链接器工具错误 LNK2026 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2026
dev_langs:
- C++
helpviewer_keywords:
- LNK2026
ms.assetid: 9955bf7c-59b5-4fa1-8481-147db0d7df45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b76c5533e79c75d06594d42464ca32104eb065ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046220"
---
# <a name="linker-tools-error-lnk2026"></a>链接器工具错误 LNK2026

模块对于 SAFESEH 映像是不安全

[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)已指定，但模块不兼容与安全异常处理功能。 如果你想要使用与此模块 **/SAFESEH**，则您将需要重新编译该模块。