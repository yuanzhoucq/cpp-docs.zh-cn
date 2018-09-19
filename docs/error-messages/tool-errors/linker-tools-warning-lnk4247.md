---
title: 链接器工具警告 LNK4247 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d84a5964cb8df5d2973b6031da55d48dade584e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078005"
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