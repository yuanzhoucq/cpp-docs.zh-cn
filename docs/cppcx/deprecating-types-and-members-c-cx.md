---
title: 要弃用的类型和成员 (C++/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 6cd880af7e206b4c7338e53615594ec2c65c59fc
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740504"
---
# <a name="deprecating-types-and-members-ccx"></a>要弃用的类型和成员 (C++/CX)

在C++/cx 中，支持使用不[推荐](/uwp/api/windows.foundation.metadata.deprecatedattribute)使用的属性来弃用制造商和使用者的 Windows 运行时类型和成员。 如果你使用的 API 已应用此特性，将显示一条编译时警告消息，指示该 API 已弃用并建议使用其他 API。 在你自己的公共类型和方法中，可应用此特性并提供自己的自定义消息。

> [!CAUTION]
> 不[推荐](/uwp/api/windows.foundation.metadata.deprecatedattribute)使用的属性仅用于 Windows 运行时类型。 对于标准 C++ 类和成员，请使用 [__declspec(deprecated)](../cpp/deprecated-cpp.md)。

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
[C++/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)
