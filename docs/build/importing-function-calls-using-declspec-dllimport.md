---
title: 使用 __declspec(dllimport) 导入函数调用
ms.date: 11/04/2016
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 1743cbba8c3046ef844f16be8e78d43c61f62606
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442518"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>使用 __declspec(dllimport) 导入函数调用

下面的代码示例演示如何使用 **_declspec （dllimport）** 将函数调用从 DLL 导入到应用程序中。 假定 `func1` 是独立于包含**main**函数的 .exe 文件的 DLL 中的函数。

如果没有 **__declspec （dllimport）** ，则给定以下代码：

```
int main(void)
{
   func1();
}
```

编译器生成的代码如下所示：

```
call func1
```

链接器将调用转换为类似于下面的内容：

```
call 0x4000000         ; The address of 'func1'.
```

如果 `func1` 存在于另一个 DLL 中，链接器将无法直接解决此问题，因为它无法知道 `func1` 的地址。 在16位环境中，链接器会将此代码地址添加到 .exe 文件中的一个列表，加载程序会在运行时使用正确的地址进行修补。 在32位和64位环境中，链接器会生成它知道地址的 thunk。 在32位环境中，thunk 如下所示：

```
0x40000000:    jmp DWORD PTR __imp_func1
```

此处 `imp_func1` 是 .exe 文件导入地址表中 `func1` 槽的地址。 这样，链接器便可以识别所有地址。 加载时，加载程序只需更新 .exe 文件的导入地址表，一切就能正常工作。

因此，使用 **__declspec （dllimport）** 更好，因为链接器在不需要时不生成 thunk。 Thunk 使代码更大（在 RISC 系统上，它可以是几个说明），并且可能会降低缓存性能。 如果告诉编译器函数在 DLL 中，则可以为您生成间接调用。

现在，此代码：

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

生成此指令：

```
call DWORD PTR __imp_func1
```

没有 thunk，无 `jmp` 指令，因此代码更小且速度更快。

另一方面，对于 DLL 内的函数调用，不需要使用间接调用。 您已经知道函数的地址。 由于在间接调用之前加载和存储函数的地址需要时间和空间，因此直接调用始终更快且更小。 仅当从 DLL 本身外部调用 DLL 函数时，才需要使用 **__declspec （dllimport）** 。 生成 DLL 时，不要对 DLL 内的函数使用 **__declspec （dllimport）** 。

## <a name="see-also"></a>另请参阅

[导入到应用程序中](importing-into-an-application.md)
