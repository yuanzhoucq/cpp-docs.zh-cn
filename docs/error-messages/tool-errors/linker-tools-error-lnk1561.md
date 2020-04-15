---
title: 链接器工具错误 LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: b397ef8e551f8cd6179392541e35183a5850454f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357753"
---
# <a name="linker-tools-error-lnk1561"></a>链接器工具错误 LNK1561

必须定义入口点

链接器没有找到*入口点*，这是调用您的可执行文件的初始函数。 默认情况下，链接程序查找控制台应用、Windows `main` `wmain`应用`WinMain`或`wWinMain`功能或`DllMain`需要初始化的 DLL 的 或函数。 您可以使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项指定其他函数。

此错误可能有多种原因：

- 您可能没有在要链接的文件列表中包括定义入口点的文件。 验证包含入口点功能的文件是否链接到你的应用。
- 您可能使用错误的函数签名定义了入口点;但是，使用签名定义了入口点。例如，您可能拼错了或使用了函数名称的错误大小写，或者错误地指定了返回类型或参数类型。
- 生成 DLL 时，您可能没有指定[/DLL](../../build/reference/dll-build-a-dll.md)选项。
- 使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项时，可能错误地指定了入口点函数的名称。
- 如果使用[LIB](../../build/reference/lib-reference.md)工具生成 DLL，则可能已指定 .def 文件。 如果是这样，请从生成中删除 .def 文件。

构建应用时，链接器将查找要调用的入口点函数以启动代码。 这是加载应用并初始化运行时后调用的函数。 您必须为应用提供入口点功能，否则你的应用无法运行。 对于 DLL，入口点是可选的。 默认情况下，链接器查找具有多个特定名称和签名之一的入口点函数，例如`int main(int, char**)`。 您可以使用 /ENTRY 链接器选项指定其他函数名称作为入口点。

## <a name="example"></a>示例

以下示例生成 LNK1561：

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
