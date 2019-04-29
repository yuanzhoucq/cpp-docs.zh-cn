---
title: 要弃用的类型和成员 (C++/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 7f488dfa522c0b48c75150d40584b0946baae806
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301495"
---
# <a name="deprecating-types-and-members-ccx"></a>要弃用的类型和成员 (C++/CX)

在C++/CX，生成者和使用者通过使用 Windows 运行时类型和成员的弃用[已弃用](/uwp/api/windows.foundation.metadata.deprecatedattribute)支持属性。 如果你使用的 API 已应用此特性，将显示一条编译时警告消息，指示该 API 已弃用并建议使用其他 API。 在你自己的公共类型和方法中，可应用此特性并提供自己的自定义消息。

> [!CAUTION]
> [已弃用](/uwp/api/windows.foundation.metadata.deprecatedattribute)属性是只适用于 Windows 运行时类型。 对于标准 C++ 类和成员，请使用 [__declspec(deprecated)](../cpp/deprecated-cpp.md)。

### <a name="example"></a>示例

下面的示例演示如何弃用你自己的公共 API（例如 Windows 运行时组件中的公共 API）。 类型 [Windows:Foundation::Metadata::DeprecationType](/uwp/api/windows.foundation.metadata.deprecationtype) 的第二个参数知否弃用或移除该 API。 目前仅支持 DeprecationType::Deprecated 值。 该特性中的第三个参数指定要应用该特性的 [Windows::Foundation::Metadata::Platform](/uwp/api/windows.foundation.metadata.platformattribute) 。

```

namespace wfm = Windows::Foundation::Metadata;

public ref class Bicycle sealed
{

public:
    property double Speed;

    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]
    double ComputeAngularVelocity();
};
```

## <a name="supported-targets"></a>支持的目标

下表列出了可应用 Deprecated 特性的构造：

| |
|-|
|XAML 控件|
|委托|
|Event — 事件|
|枚举字段|
|enum|
|struct|
|方法|
|class|
|interface|
|属性|
|结构字段|
|参数化构造函数|

## <a name="see-also"></a>请参阅

[类型系统](../cppcx/type-system-c-cx.md)<br/>
[VisualC++语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)
