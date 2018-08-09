---
title: 'Weakref:: Copyto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88a092255655aaea0e06e8f69b520789f441d379
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016283"
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo 方法
如果可用，请为指定的指针变量分配一个指向接口的指针。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
### <a name="parameters"></a>参数  
 *U*  
 指针`IInspectable`接口。 如果错误发出*U*不派生自`IInspectable`。  
  
 *riid*  
 接口 ID。 如果错误发出*riid*不派生自`IWeakReference`。  
  
 *ptr*  
 指向的双向间接指针`IInspectable`或`IWeakReference`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为描述失败的 HRESULT。 有关更多信息，请参见**备注**。  
  
## <a name="remarks"></a>备注  
 返回值 S_OK 表示此操作成功，但并不指示弱引用是否解析为强引用。 如果返回 S_OK，则测试参数*p*是否为强引用; 即，参数*p*不等于**nullptr**。  
  
 从 Windows 10 SDK 开始，此方法不设置**WeakRef**实例向**nullptr**如果无法获得弱引用，因此应避免错误检查，检查的 WeakRef 的代码**nullptr**。 相反，应检查*ptr*有关**nullptr**。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [WeakRef 类](../windows/weakref-class.md)