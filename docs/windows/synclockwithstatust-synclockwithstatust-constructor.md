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
ms.openlocfilehash: 020632ff17ade10e7fcb9cd46d245849189b6860
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416781"
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

*other*<br/>
对另一个右值引用**SyncLockWithStatusT**对象。

*sync*<br/>
对另一个引用**SyncLockWithStatusT**对象。

*status*<br/>
值[status_](../windows/synclockwithstatust-status-data-member.md)的数据成员*其他*参数或*同步*参数。

## <a name="remarks"></a>备注

初始化的新实例**SyncLockWithStatusT**类。

第一个构造函数初始化当前**SyncLockWithStatusT**从另一个对象**SyncLockWithStatusT**由参数指定*其他*，，然后使另**SyncLockWithStatusT**对象。 第二个构造函数是**受保护**，并初始化当前**SyncLockWithStatusT**为无效状态的对象。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>请参阅

[SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)<br/>
[SyncLockWithStatusT::GetStatus 方法](../windows/synclockwithstatust-getstatus-method.md)