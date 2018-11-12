---
title: 默认信号
ms.date: 11/04/2016
helpviewer_keywords:
- default signals
- defaults, signals
ms.assetid: db9fc17b-75c0-4d33-86be-c536584bbede
ms.openlocfilehash: 91d054f32a072f9ad9ebc15a8932bf2d52a43597
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647737"
---
# <a name="default-signals"></a>默认信号

ANSI 4.7.1.1 调用信号处理程序前未执行 `signal(sig, SIG_DFL)` 的等效项时，对所执行信号的阻止

程序开始运行时，信号将设置为其默认状态。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)