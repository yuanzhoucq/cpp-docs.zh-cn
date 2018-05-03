---
title: Windows 运行时不支持的 CRT 函数 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- unsupported CRT functions, Windows Runtime
- Windows Runtime, unsupported CRT functions
ms.assetid: bb8386d6-0ef8-460c-88d8-addff009b6f1
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 50a04dc63dfc5fbadce7721f5985e3190cdab506
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="windows-runtime-unsupported-crt-functions"></a>Windows 运行时不支持的 CRT 函数

许多 C 运行时 (CRT) API 都不能用于在 Windows 运行时中执行的通用 Windows 平台应用。 这些应用是使用 /ZW 编译器标志生成的。 有关不支持的 CRT 函数的列表，请参阅[通用 Windows 平台应用不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

文档的[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)部分介绍了所有 CRT API。

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
