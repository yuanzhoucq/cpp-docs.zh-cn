---
title: 链接器工具错误 LNK1561 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1561
dev_langs:
- C++
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac24ed0c4aff4cbd7f0ea95ff71d0b8c4b3be09c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050757"
---
# <a name="linker-tools-error-lnk1561"></a>链接器工具错误 LNK1561

必须定义入口点

找不到链接器*入口点*，要调用的可执行文件中的初始函数。 默认情况下，链接器查找`main`或`wmain`控制台应用程序的函数`WinMain`或`wWinMain`函数对于 Windows 应用，或`DllMain`需要初始化 dll。 可以通过使用指定另一个函数[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项。

此错误可以有几个原因：
- 您可能不包含要链接的文件列表中定义的入口点的文件。 验证包含入口点函数的文件链接到你的应用。
- 您可能定义了使用错误的函数签名中; 的入口点例如，你可能有拼写错误或使用错误的大小写的函数名称，或者未正确指定返回类型或参数类型。
- 你可能不指定[/DLL](../../build/reference/dll-build-a-dll.md)选项时生成 DLL。
- 你可能已指定的入口点函数名称不正确时所用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项。
- 如果使用的[LIB](../../build/reference/lib-reference.md)工具生成 DLL 时，你可能已指定一个.def 文件。 如果是这样，从生成中移除.def 文件。

当生成的应用程序，链接器将查找某个入口点函数，以调用以启动您的代码。 这是应用程序加载并运行时进行初始化之后调用的函数。 必须提供一个应用程序、 某个入口点函数，或您的应用程序无法运行。 入口点是可选的 DLL。 默认情况下，链接器查找有几个特定名称和签名，如某个入口点函数`int main(int, char**)`。 可以指定另一个函数名称作为入口点，通过使用 /ENTRY 链接器选项。

## <a name="example"></a>示例

下面的示例生成 LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```