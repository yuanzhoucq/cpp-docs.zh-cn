---
title: 使用 __declspec(dllimport) 导入函数调用
description: 调用 DLL 数据和函数时，如何以及为什么使用 __declspec （dllimport）。
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765716"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>使用导入函数调用`__declspec(dllimport)`

使用批注调用**`__declspec(dllimport)`** 可以更快地进行调用。 **`__declspec(dllimport)`** 访问导出的 DLL 数据始终需要。

## <a name="import-a-function-from-a-dll"></a>从 DLL 导入函数

下面的代码示例演示如何使用**`__declspec(dllimport)`** 将 DLL 中的函数调用导入到应用程序中。 假设`func1`是独立于包含**main**函数的可执行文件的 DLL 中的函数。

如果**`__declspec(dllimport)`** 没有，则给定以下代码：

```C
int main(void)
{
   func1();
}
```

编译器生成的代码如下所示：

```asm
call func1
```

链接器将调用转换为类似于下面的内容：

```asm
call 0x4000000         ; The address of 'func1'.
```

如果`func1`存在于另一个 DLL 中，链接器将无法直接解析此地址，因为它无法知道的`func1`地址。 在32位和64位环境中，链接器在已知地址生成 thunk。 在32位环境中，thunk 如下所示：

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

下面`__imp_func1`是可执行文件的`func1`导入地址表中的槽地址。 链接器已知所有这些地址。 加载时，加载程序只需更新可执行文件的导入地址表，一切就能正常工作。

这就是为什么**`__declspec(dllimport)`** 使用更好的原因：如果链接器不需要，则不生成 thunk。 Thunk 使代码更大（在 RISC 系统上，它可以是几个说明），并且可能会降低缓存性能。 如果告诉编译器函数在 DLL 中，则可以为您生成间接调用。

现在，此代码：

```C
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

生成此指令：

```asm
call DWORD PTR __imp_func1
```

没有 thunk 和`jmp`说明，因此代码更小且速度更快。 您也可以在不使用全程序**`__declspec(dllimport)`** 优化的情况下获得相同的效果。 有关详细信息，请参阅 [/GL（全程序优化）](reference/gl-whole-program-optimization.md)。

对于 DLL 中的函数调用，不需要使用间接调用。 链接器已经知道函数的地址。 在间接调用之前，需要额外的时间和空间来加载和存储函数的地址。 直接调用始终更快且更小。 只需在从 DLL **`__declspec(dllimport)`** 本身之外调用 dll 函数时使用。 生成 DLL **`__declspec(dllimport)`** 时，不要在 dll 内使用函数。

## <a name="see-also"></a>另请参阅

[导入到应用程序中](importing-into-an-application.md)
