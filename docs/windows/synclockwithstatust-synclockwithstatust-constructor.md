---
title: 'Synclockwithstatust:: Synclockwithstatust 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f068c618cf7f8a8658cd8409a7ec79a561c307a6
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018382"
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT 构造函数
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
### <a name="parameters"></a>参数  
 *other*  
 对另一个右值引用**SyncLockWithStatusT**对象。  
  
 *sync*  
 对另一个引用**SyncLockWithStatusT**对象。  
  
 *status*  
 值[status_](../windows/synclockwithstatust-status-data-member.md)的数据成员*其他*参数或*同步*参数。  
  
## <a name="remarks"></a>备注  
 初始化的新实例**SyncLockWithStatusT**类。  
  
 第一个构造函数初始化当前**SyncLockWithStatusT**从另一个对象**SyncLockWithStatusT**由参数指定*其他*，，然后使另**SyncLockWithStatusT**对象。 第二个构造函数是**受保护**，并初始化当前**SyncLockWithStatusT**为无效状态的对象。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus 方法](../windows/synclockwithstatust-getstatus-method.md)