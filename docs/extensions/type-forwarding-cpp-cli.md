---
title: 类型转发 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
ms.openlocfilehash: 0803ecc2ffb2da2748b1ef063481aa2571f27f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171926"
---
# <a name="type-forwarding-ccli"></a>类型转发 (C++/CLI)

使用类型转发，可以将类型从一个程序集（程序集 A）移到另一个程序集（程序集 B）中，这样就无需重新编译使用程序集 A 的客户端了。

## <a name="windows-runtime"></a>Windows 运行时

Windows 运行时不支持此功能。

## <a name="common-language-runtime"></a>公共语言运行时

下面的代码示例展示了如何使用类型转发。

### <a name="syntax"></a>语法

```cpp
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>parameters

*全新*<br/>
要将类型定义移到其中的程序集。

type<br/>
要将其定义移到另一个程序集的类型。

### <a name="remarks"></a>备注

在某组件（程序集）交付并被客户端应用程序使用之后，你可以使用类型转发来将类型从此组件（程序集）移到另一个程序集中，并交付更新后的组件（以及所需的其他任何程序集），这样无需你重新编译，客户端应用程序也仍能正常运行。

类型转发只适用于现有应用程序引用的组件。 重新生成应用程序后，必须有应用程序使用的任何类型的相应程序集引用。

如果从程序集中转发类型（类型 A），必须为此类型添加 `TypeForwardedTo` 特性和程序集引用。 引用的程序集必须包含以下内容之一：

- 类型 A 的定义。

- 类型 A 的 `TypeForwardedTo` 特性和程序集引用。

可以转发的类型示例包括：

- ref class

- value class

- 枚举

- 接口

无法转发以下类型：

- 泛型类型

- 本机类型

- 嵌套类型（若要转发嵌套类型，应转发封闭类型）

可以将类型转发到以任何定目标到公共语言运行时的语言编写的程序集。

因此，如果用于生成程序集 A.dll 的源代码文件包含类型定义 (`ref class MyClass`)，且你希望将此类型定义移到程序集 B.dll 中，你会执行以下操作：

1. 将 `MyClass` 类型定义移到用于生成 B.dll 的源代码文件中。

2. 生成程序集 B.dll

3. 从用于生成 A.dll 的源代码中删除 `MyClass` 类型定义，并将它替换为以下代码：

    ```cpp
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. 生成程序集 A.dll。

5. 无需重新编译客户端应用程序，即可使用 A.dll。

### <a name="requirements"></a>要求

编译器选项：`/clr`
