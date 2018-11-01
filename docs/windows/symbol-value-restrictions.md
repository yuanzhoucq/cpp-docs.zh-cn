---
title: 符号值限制
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.restrictions.value
helpviewer_keywords:
- symbols [C++], value restrictions
- restrictions, symbol values
ms.assetid: 32467ec3-690b-4cd0-a4d0-7d189a3296cb
ms.openlocfilehash: 0f0a02c7eb2bbb205f41aaeec209c45d629f0b20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677664"
---
# <a name="symbol-value-restrictions"></a>符号值限制

符号值可以是用于 #define 预处理器指令的以正常方式表示的任何整数。 下面是符号值的一些示例：

```
18
4001
0x0012
-3456
```

资源（加速器、位图、光标、对话框、图标、菜单、字符串表和版本信息）的符号值必须是处于 0 到 32,767 的范围中的十进制数字（但不能为十六进制）。 资源的部件（如对话框控件或字符串表中的各个字符串）的符号值可以从 0 到 65,534 或从 -32,768 到 32,767。

资源符号是 16 位数字。 可以有符号或无符号形式输入它们，但是，它们在内部用作无符号整数。 因此负数会强制转换为对应的正数值。

下面是符号值的一些限制：

- Visual Studio 开发环境和 MFC 将一些数字范围用于特殊用途。 设置了最高有效位的所有数字（-32,768 到 -1，或 32,768 到 65,534，具体取决于符号）由 MFC 保留。

- 不能使用其他符号字符串定义符号值。 例如，不支持以下符号定义：

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- 不能将具有参数的预处理器宏用作值定义。 例如：

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   不是有效的表达式（无论 `ID` 在编译时的计算结果如何）。

- 应用程序可能具有包含使用表达式定义的符号的现有文件。 有关如何包含符号作为只读符号的详细信息，请参阅[使用共享 （只读） 或计算符号](../windows/including-shared-read-only-or-calculated-symbols.md)。

有关数字范围的详细信息，请参阅[TN023： 标准 MFC 资源](../mfc/tn023-standard-mfc-resources.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[更改符号的数字值](../windows/changing-a-symbol-s-numeric-value.md)<br/>
[符号名限制](../windows/symbol-name-restrictions.md)<br/>
[预定义的符号 ID](../windows/predefined-symbol-ids.md)