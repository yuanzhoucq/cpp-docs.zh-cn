---
title: 链接器工具警告 LNK4217
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1ce410312493b353bb68ea7264fce9cd6a394e0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183106"
---
# <a name="linker-tools-warning-lnk4217"></a>链接器工具警告 LNK4217

> "*filename_1*" 中定义的符号 "*symbol*" 由函数 "*function*" 中的 "*filename_2 .obj*" 导入

即使符号是在同一图像的对象文件中定义的，也为符号指定了[__declspec （dllimport）](../../cpp/dllexport-dllimport.md) 。 删除 `__declspec(dllimport)` 修饰符以解决此警告。

## <a name="remarks"></a>备注

*symbol*是在图像中定义的符号名称。 *函数*是导入符号的函数。

使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项编译时不会出现此警告。

如果尝试将两个模块链接在一起，而你应改为在第二个模块上编译第一个模块的导入库，则也会发生 LNK4217。

```cpp
// main.cpp
__declspec(dllimport) void func();

int main()
{
    func();
    return 0;
}

```

然后，

```cpp
// tt.cpp
// compile with: /c
void func() {}
```

尝试按如下所示编译这两个模块会导致 LNK4217：

```cmd
cl.exe /c main.cpp tt.cpp
link.exe main.obj tt.obj
```

若要修复此错误，请在编译两个文件之后，将 tt 传递到 node.js 以创建 .lib 文件，然后将 main .obj 与 tt 连接，如下所示：

```cmd
cl.exe /c main.cpp tt.cpp
lib.exe tt.obj /export:func /def
link.exe main.obj tt.lib
```

## <a name="see-also"></a>另请参阅

[链接器工具警告 LNK4049](linker-tools-warning-lnk4049.md) \
[链接器工具警告 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)
