---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5dec19d4c7d6f1def451f7f11588f303961cc5c0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

调用 c + + 标准库中的任何潜在的不安全的方法会导致[编译器警告 （等级 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 若要禁用此警告，可在代码中将宏定义为 **_SCL_SECURE_NO_WARNINGS**：

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

如果你使用预编译标头，预编译标头文件中放置此指令之前包括任何 C 运行库或标准库头文件。 如果你之前包含预编译的头文件将其放入单独的源代码文件，它会忽略编译器。

## <a name="remarks"></a>备注

禁用 C4996 警告的其他方式包括：

- 使用 [/D（预处理器定义）](../build/reference/d-preprocessor-definitions.md)编译器选项：

   > cl /D_SCL_SECURE_NO_WARNINGS [其他编译器选项] myfile.cpp

- 使用 [/w](../build/reference/compiler-option-warning-level.md) 编译器选项：

   > cl /wd4996 [其他编译器选项] myfile.cpp

- 使用 [#pragma warning](../preprocessor/warning.md) 指令：

   ```cpp
   #pragma warning(disable:4996)
   ```

此外，还可以使用 **/w\<l>\<n>** 编译器选项手动更改警告 C4996 的级别。 例如，可将警告 C4996 设置为级别 4：

> cl /w44996 [其他编译器选项] myfile.cpp

有关详细信息，请参阅 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX（警告级别）](../build/reference/compiler-option-warning-level.md)。

## <a name="see-also"></a>请参阅

[安全库：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
