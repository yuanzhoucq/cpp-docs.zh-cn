---
title: FtmBase 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
dev_langs:
- C++
helpviewer_keywords:
- FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 38f30c497fc8640b1f88f4ffb3fc6f14bed55a3e
ms.sourcegitcommit: e3b4ef19b534a2ed48bb9091e5197a6e536f16c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814347"
---
# <a name="ftmbase-class"></a>FtmBase 类
表示自由线程封送拆收器对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,   
   Microsoft::WRL::CloakedIid<IMarshal> >;  
```  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[RuntimeClass 类](runtimeclass-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[FtmBase::FtmBase 构造函数](../windows/ftmbase-ftmbase-constructor.md)|初始化 FtmBase 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable 方法](../windows/ftmbase-createglobalinterfacetable-method.md)|可以创建全局接口表 (GIT)。|  
|[FtmBase::DisconnectObject 方法](../windows/ftmbase-disconnectobject-method.md)|强制释放对象的所有外部连接。 对象的服务器调用之前的情况下关闭此方法的对象的实现。|  
|[FtmBase::GetMarshalSizeMax 方法](../windows/ftmbase-getmarshalsizemax-method.md)|获取上的封送指定的接口指针上指定的对象所需的字节数的上限。|  
|[FtmBase::GetUnmarshalClass 方法](../windows/ftmbase-getunmarshalclass-method.md)|获取 COM 用来定位 DLL 包含代码的相应的代理的 CLSID。 COM 加载此 DLL 才能创建代理服务器的未初始化的实例。|  
|[FtmBase::MarshalInterface 方法](../windows/ftmbase-marshalinterface-method.md)|初始化代理对象某些客户端过程中的所需的数据将写入流。|  
|[FtmBase::ReleaseMarshalData 方法](../windows/ftmbase-releasemarshaldata-method.md)|销毁封送的数据包。|  
|[FtmBase::UnmarshalInterface 方法](../windows/ftmbase-unmarshalinterface-method.md)|初始化新创建的代理，并向该代理返回的接口指针。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[FtmBase::marshaller_ 数据成员](../windows/ftmbase-marshaller-data-member.md)|保存到自由线程封送处理程序的引用。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `FtmBase`  
  
## <a name="requirements"></a>要求  
 **标头：** ftm.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)