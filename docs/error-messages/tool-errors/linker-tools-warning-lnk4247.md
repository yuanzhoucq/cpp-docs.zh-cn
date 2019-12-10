---
title: 链接器工具警告 LNK4247
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: 344c219fa1f3daa1e5f9c31431e608f5e7036400
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991156"
---
# <a name="linker-tools-warning-lnk4247"></a>链接器工具警告 LNK4247

入口点 "decorated_function_name" 已经有一个 thread 属性;已忽略 "attribute"

使用[/ENTRY （入口点符号）](../../build/reference/entry-entry-point-symbol.md)指定的入口点具有一个线程属性，但也使用不同的线程模型指定了[/CLRTHREADATTRIBUTE （设置 CLR 线程特性）](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) 。

链接器忽略了通过/CLRTHREADATTRIBUTE. 指定的值

若要解决此警告：

- 从生成中删除/CLRTHREADATTRIBUTE。

- 从源代码文件中删除属性。

- 从生成中删除源和/CLRTHREADATTRIBUTE 中的属性，并接受默认 CLR 线程模型。

- 更改传递给/CLRTHREADATTRIBUTE 的值，使其与源中的属性一致。

- 在源中更改属性，使其与传递给/CLRTHREADATTRIBUTE. 的值一致

下面的示例生成 LNK4247

```cpp
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```
