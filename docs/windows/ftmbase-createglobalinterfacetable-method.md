---
title: 'Ftmbase:: Createglobalinterfacetable 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable
dev_langs:
- C++
helpviewer_keywords:
- CreateGlobalInterfaceTable method
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c042b6bd17da3459f499f9eb1c9167343c2e2ab
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578768"
---
# <a name="ftmbasecreateglobalinterfacetable-method"></a>FtmBase::CreateGlobalInterfaceTable 方法

创建全局接口表 (GIT)。

## <a name="syntax"></a>语法

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>参数

*Git*  
此操作完成后，指向全局接口表的指针。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="remarks"></a>备注

有关详细信息，请参阅`IGlobalInterfaceTable`中的主题**COM 接口**的子主题**COM 引用**MSDN Library 中的主题。

## <a name="requirements"></a>要求

**标头：** ftm.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[FtmBase 类](../windows/ftmbase-class.md)