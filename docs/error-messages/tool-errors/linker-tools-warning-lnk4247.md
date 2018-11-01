---
title: 链接器工具警告 LNK4247
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: cd4108f8bd06ec7a0b2d2eb9fab13917174b797b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516020"
---
# <a name="linker-tools-warning-lnk4247"></a>链接器工具警告 LNK4247

入口点 'decorated_function_name 已具有线程特性;attribute 被忽略

使用指定的入口点[/ENTRY （入口点符号）](../../build/reference/entry-entry-point-symbol.md)，有一个线程处理的属性，但[/CLRTHREADATTRIBUTE （设置 CLR 线程特性）](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)也指定了，与不同的线程处理模型。

链接器忽略 /CLRTHREADATTRIBUTE 用指定的值。

若要解决此警告：

- 从你的生成中删除 /CLRTHREADATTRIBUTE。

- 从源代码文件中删除属性。

- 从您的生成，来自源和 /CLRTHREADATTRIBUTE 删除这两个属性，并接受默认 CLR 线程模型。

- 这样一来，它与源中的属性，请更改传递给 /CLRTHREADATTRIBUTE 的值。

- 更改源中的属性，这样一来，它与传递给 /CLRTHREADATTRIBUTE 的值一致。

下面的示例生成 LNK4247

```
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```