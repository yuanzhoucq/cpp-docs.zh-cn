---
title: Platform::Metadata::RuntimeClassName |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 024d9d7dce234b07620a108b1f11c240bd842ac6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592573"
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName
在应用于类定义时，请确保私有类从 GetRuntimeClassName 函数返回有效名称。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[Platform::Metadata::RuntimeClassName] name  
```  
  
#### <a name="parameters"></a>参数  
 name  
  
 Windows 运行时中可见的现有公共类型的名称。  
  
### <a name="remarks"></a>备注  
 在私有 ref 类上使用此特性指定自定义运行时类型名称并且/或者指定现有名称未满足要求。 指定为类实现的公共接口名称。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用此特性。 在此示例中，HellowWorldImpl 的运行时类型名称为 Test::Native::MyComponent::IHelloWorld  
  
```  
  
namespace Test  
{  
    namespace Native  
    {  
        namespace MyComponent  
        {  
            public interface class IHelloWorld  
            {  
                Platform::String^ SayHello();  
            };  
  
            private ref class HelloWorldImpl sealed :[Platform::Metadata::RuntimeClassName] IHelloWorld  
            {  
            public:  
                HelloWorldImpl();  
                virtual Platform::String^ SayHello();  
            };  
  
            Platform::String^ HelloWorldImpl::SayHello()  
            {  
                return L"Hello World!";  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [Platform::Metadata 命名空间](../cppcx/platform-metadata-namespace.md)