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
ms.openlocfilehash: d19d47fe7120301740e1431765fc6edbeaa48c60
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448196"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

在C++标准库中调用任何可能不安全的方法都会导致[编译器警告 (等级 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 若要禁用此警告, 请在代码中定义宏 _SCL_SECURE_NO_WARNINGS:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

如果使用预编译头, 请将此指令置于预编译头文件中, 然后再添加任何 C 运行库或标准库标头。 如果将其放在单独的源代码文件中, 然后再包含预编译头文件, 编译器将忽略该文件。

## <a name="remarks"></a>备注

禁用 C4996 警告的其他方式包括：

- 使用 [/D（预处理器定义）](../build/reference/d-preprocessor-definitions.md)编译器选项：

   > cl/D_SCL_SECURE_NO_WARNINGS [其他编译器选项] myfile.txt

- 使用 [/w](../build/reference/compiler-option-warning-level.md) 编译器选项：

   > cl/wd4996 [其他编译器选项] myfile.txt

- 使用 [#pragma warning](../preprocessor/warning.md) 指令：

   ```cpp
   #pragma warning(disable:4996)
   ```

此外，还可以使用 **/w\<l>\<n>** 编译器选项手动更改警告 C4996 的级别。 例如，可将警告 C4996 设置为级别 4：

> cl/w44996 [其他编译器选项] myfile.txt

有关详细信息，请参阅 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX（警告级别）](../build/reference/compiler-option-warning-level.md)。

## <a name="see-also"></a>请参阅

[：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)
