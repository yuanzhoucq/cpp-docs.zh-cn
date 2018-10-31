---
title: 输入 / 输出替换选项
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
ms.openlocfilehash: bc595b64c991ada8e958e71e13f8cb9d134adb8a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439684"
---
# <a name="inputoutput-alternatives"></a>输入/输出替换选项

Visual C++ 为 I/O 编程提供了多种替代方法：

- C 运行时库直接无缓冲 I/O。

- ANSI C 运行时库流 I/O。

- 控制台和端口直接 I/O。

- Microsoft 基础类库。

- Microsoft C++ 标准库。

iostream 类适用于缓冲的格式化文本 I/O。 如果需要 C++ 编程接口且决定不使用 Microsoft 基础类 (MFC) 库，此类也适用于无缓冲或二进制 I/O。 iostream 类是 C 运行时函数的一种面向对象的 I/O 替代方法。

可将 iostream 类用于 Microsoft Windows 操作系统。 字符串和文件流无使用限制条件，但字符模型流对象 `cin`、`cout`、`cerr` 和 `clog` 与 Windows 图形用户界面不一致。 也可派生与 Windows 环境直接交互的自定义流类。

## <a name="see-also"></a>请参阅

[流的定义](../standard-library/what-a-stream-is.md)<br/>
