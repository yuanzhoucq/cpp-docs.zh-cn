---
title: FtmBase 类 |Microsoft Docs
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
ms.openlocfilehash: 662e40dd7e111b976be105129861b8ea26e5d0d9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646171"
---
# <a name="ftmbase-class"></a>FtmBase 类
表示自由线程封送拆收器对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
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
|[FtmBase::FtmBase 构造函数](../windows/ftmbase-ftmbase-constructor.md)|初始化的新实例**FtmBase**类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable 方法](../windows/ftmbase-createglobalinterfacetable-method.md)|创建全局接口表 (GIT)。|  
|[FtmBase::DisconnectObject 方法](../windows/ftmbase-disconnectobject-method.md)|强制释放对象的所有外部连接。 对象的服务器将调用此方法在关机前对象的实现。|  
|[FtmBase::GetMarshalSizeMax 方法](../windows/ftmbase-getmarshalsizemax-method.md)|获取有关封送指定的接口指针上指定的对象所需的字节数的上限。|  
|[FtmBase::GetUnmarshalClass 方法](../windows/ftmbase-getunmarshalclass-method.md)|获取 COM 用来定位相应代理包含代码的 DLL 的 CLSID。 COM 加载此 DLL 才能创建代理的未初始化的实例。|  
|[FtmBase::MarshalInterface 方法](../windows/ftmbase-marshalinterface-method.md)|初始化一些客户端进程中的代理对象所需的数据写入到流。|  
|[FtmBase::ReleaseMarshalData 方法](../windows/ftmbase-releasemarshaldata-method.md)|销毁封送的数据包。|  
|[FtmBase::UnmarshalInterface 方法](../windows/ftmbase-unmarshalinterface-method.md)|初始化新创建的代理，并对该代理返回的接口指针。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[FtmBase::marshaller_ 数据成员](../windows/ftmbase-marshaller-data-member.md)|保存对自由线程封送处理程序的引用。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `FtmBase`  
  
## <a name="requirements"></a>要求  
 **标头：** ftm.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)