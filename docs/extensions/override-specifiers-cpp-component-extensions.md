---
title: 重写说明符（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: 410fe9ecc48b92c68132f7b1b8057c2549c8afcf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181897"
---
# <a name="override-specifiers--ccli-and-ccx"></a>重写说明符（C++/CLI 和 C++/CX）

重写说明符修改继承类型及其成员在派生类型中的行为。

## <a name="all-runtimes"></a>所有运行时

### <a name="remarks"></a>备注

有关重写说明符的详细信息，请参阅：

- [abstract](abstract-cpp-component-extensions.md)

- [新（vtable 中的新槽）](new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- [重写说明符和本机编译](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

abstract 和 sealed 也对类型声明有效，但不用作重写说明符。

若要了解如何显式重写基类函数，请参阅[显式重写](explicit-overrides-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 运行时

(此语言功能没有只适用于 Windows 运行时的备注。）

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

（此语言功能没有只适用于公共运行时的备注。）

### <a name="requirements"></a>要求

编译器选项：`/clr`

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
