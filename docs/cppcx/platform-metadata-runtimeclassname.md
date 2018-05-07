---
title: Platform::Metadata::RuntimeClassName |Microsoft 文档
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 297a5089af7db43d837934e864e0925cd7b34a3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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