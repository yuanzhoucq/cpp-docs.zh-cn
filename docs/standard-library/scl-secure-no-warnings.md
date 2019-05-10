---
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: 77c60aed511fc3dbbea2d74e83e36dae735dcb0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348303"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

调用中可能不安全的方法的任何C++标准库会导致[编译器警告 （等级 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 若要禁用此警告，请在代码中定义宏 _SCL_SECURE_NO_WARNINGS:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

如果使用预编译标头，此指令在预编译的头文件中先将包括任何 C 运行时库或标准库标头。 如果你包含预编译的头文件之前将其放入单个源代码文件中，它将忽略编译器。

## <a name="remarks"></a>备注

禁用 C4996 警告的其他方式包括：

- 使用 [/D（预处理器定义）](../build/reference/d-preprocessor-definitions.md)编译器选项：

   > cl /D_SCL_SECURE_NO_WARNINGS [其他编译器选项] myfile.cpp

- 使用 [/w](../build/reference/compiler-option-warning-level.md) 编译器选项：

   > cl /wd4996 [other compiler options] myfile.cpp

- 使用 [#pragma warning](../preprocessor/warning.md) 指令：

   ```cpp
   #pragma warning(disable:4996)
   ```

此外，还可以使用 **/w\<l>\<n>** 编译器选项手动更改警告 C4996 的级别。 例如，可将警告 C4996 设置为级别 4：

> cl /w44996 [other compiler options] myfile.cpp

有关详细信息，请参阅 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX（警告级别）](../build/reference/compiler-option-warning-level.md)。

## <a name="see-also"></a>请参阅

[：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
