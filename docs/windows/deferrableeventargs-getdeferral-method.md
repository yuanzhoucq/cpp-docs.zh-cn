---
title: 'Deferrableeventargs:: Getdeferral 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 47376a055da1625f718b7b2a8b6dbf4fe703e533
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601800"
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral 方法

获取对[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)表示延迟的事件的对象。

## <a name="syntax"></a>语法

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```

### <a name="parameters"></a>参数

*结果*  
将引用的指针[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)对象在调用完成时。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="remarks"></a>备注

有关代码示例，请参阅[DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)。

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)