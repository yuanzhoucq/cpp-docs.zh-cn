---
title: "要弃用的类型和成员 (C + + /cli CX) |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a1062a507d6281e003d9294de1c1cb39b7c01f9e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="deprecating-types-and-members-ccx"></a>要弃用的类型和成员 (C++/CX)
在 C + + /CX 中，生成者和使用者通过使用 Windows 运行时类型和成员的不推荐使用[已弃用](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c)支持属性。 如果你使用的 API 已应用此特性，将显示一条编译时警告消息，指示该 API 已弃用并建议使用其他 API。 在你自己的公共类型和方法中，可应用此特性并提供自己的自定义消息。  
  
> [!CAUTION]
>  [已弃用](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c)属性是仅用于使用 Windows 运行时类型。 对于标准 C++ 类和成员，请使用 [__declspec(deprecated)](http://msdn.microsoft.com/library/044swk7y.aspx)。  
  
### <a name="example"></a>示例  
 下面的示例演示如何弃用你自己的公共 API（例如 Windows 运行时组件中的公共 API）。 类型 [Windows:Foundation::Metadata::DeprecationType](http://msdn.microsoft.com/en-us/ee01e63d-37d0-4273-accc-fca174f88bfa) 的第二个参数知否弃用或移除该 API。 目前仅支持 DeprecationType::Deprecated 值。 该特性中的第三个参数指定要应用该特性的 [Windows::Foundation::Metadata::Platform](http://msdn.microsoft.com/en-us/1eae292d-1ab7-4d97-a58c-b0beffd51ef5) 。  
  
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
  
||  
|-|  
|XAML 控件|  
|委托|  
|Event — 事件|  
|枚举字段|  
|enum|  
|struct|  
|方法|  
|类|  
|接口|  
|属性|  
|结构字段|  
|参数化构造函数|  
  
## <a name="see-also"></a>请参阅  
 [类型系统](../cppcx/type-system-c-cx.md)   
 [Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)