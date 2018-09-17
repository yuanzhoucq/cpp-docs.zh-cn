---
title: 修复版本生成的问题 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- release builds, troubleshooting
- debug builds, memory overwrites
- memory, overwrites
- troubleshooting Visual C++, release builds
- troubleshooting release builds
ms.assetid: a0c0818e-4c47-4fe0-a611-50d61a41bd88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b304fa6bcc9b0b248719ea44b28e9dae5c76a6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726526"
---
# <a name="fixing-release-build-problems"></a>修复发行版本问题

如果你的代码从调试版本切换到发行版本后生成编译错误，有几个方面应检查。

在未调试生成期间收到的优化 （发布） 生成期间，可能会收到编译器警告。

- [检查 ASSERT 语句](../../build/reference/using-verify-instead-of-assert.md)

- [使用调试版本检查内存改写](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

- [打开生成的发布版本的调试信息](../../build/reference/how-to-debug-a-release-build.md)

- [检查内存改写](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>请参阅

[发行版本](../../build/reference/release-builds.md)<br/>
[创建发行版本时遇到的常见问题](../../build/reference/common-problems-when-creating-a-release-build.md)<br/>
[优化代码](../../build/reference/optimizing-your-code.md)