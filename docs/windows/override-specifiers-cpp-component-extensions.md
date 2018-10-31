---
title: 重写说明符 (C + + /cli 和 C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0620bc7045dcb312667cfdfe670e1f19b0545cf2
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327459"
---
# <a name="override-specifiers--ccli-and-ccx"></a>重写说明符 (C + + /cli 和 C + + /cli CX)

*重写说明符*修改如何继承的类型和继承类型成员在派生类型中的行为。

## <a name="all-runtimes"></a>所有运行时

### <a name="remarks"></a>备注

有关重写说明符的详细信息，请参阅：

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [新 (新 vtable 中的槽）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- [重写说明符和本机编译](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**抽象**并**密封**也是有效的在类型声明，它们不用作重写说明符。

有关显式重写基类函数的信息，请参阅[显式重写](../windows/explicit-overrides-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 运行时

(此语言功能没有只适用于 Windows 运行时的备注。）

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

（此语言功能没有只适用于公共运行时的备注。）

### <a name="requirements"></a>要求

编译器选项：`/clr`

## <a name="see-also"></a>请参阅

[适用于.NET 和 UWP 组件扩展](../windows/component-extensions-for-runtime-platforms.md)