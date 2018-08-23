---
title: 'Asyncbase:: Checkvalidstateforresultscall 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
dev_langs:
- C++
helpviewer_keywords:
- CheckValidStateForResultsCall method
ms.assetid: 87ca6805-bff1-4063-b855-6dd26132deff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 398f46d5f8eb15d961d80b9a7a20b758fffd09c3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584231"
---
# <a name="asyncbasecheckvalidstateforresultscall-method"></a>AsyncBase::CheckValidStateForResultsCall 方法

测试是否可以在当前的异步状态中收集的异步操作结果。

## <a name="syntax"></a>语法

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

## <a name="return-value"></a>返回值

如果可以收集结果; 则为 S_OK否则为 E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL。

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)