---
title: ATL 运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f5027fa4b84d84bf07766c7ac4e75f140706f0c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103694"
---
# <a name="atl-operators"></a>ATL 运算符

本部分包含的 ATL 全局运算符的参考主题。

|运算符|描述|
|--------------|-----------------|
|[operator ==](#operator_eq_eq)|比较两个`CSid`对象或`SID`结构是否相等。|
|[运算符 ！ =](#operator_neq)|比较两个`CSid`对象或`SID`结构是否不相等。|
|[运算符 <](#operator_lt)|如果测试`CSid`对象或`SID`运算符左侧的结构是不会早于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|
|[运算符 >](#operator_gt)|如果测试`CSid`对象或`SID`运算符左侧的结构是否大于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|
|[运算符 < =](#operator_lt__eq)|如果测试`CSid`对象或`SID`运算符左侧的结构是否小于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|
|[运算符 > =](#operator_gt__eq)|如果测试`CSid`对象或`SID`运算符左侧的结构是大于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。|

## <a name="requirements"></a>要求

**标头：** atlsecurity.h。

##  <a name="operator_eq_eq"></a>  运算符 = =

比较`CSid`对象或`SID`（安全标识符） 结构是否相等。

```   
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*  
第一个`CSid`对象或`SID`结构进行比较。

*rhs*  
第二个`CSid`对象或`SID`结构进行比较。

### <a name="return-value"></a>返回值

如果对象相等，则返回 FALSE 如果它们不相等，则返回 TRUE。

##  <a name="operator_neq"></a>  运算符 ！ =

比较`CSid`对象或`SID`（安全标识符） 结构是否不相等。

```   
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*  
第一个`CSid`对象或`SID`结构进行比较。

*rhs*  
第二个`CSid`对象或`SID`结构进行比较。

### <a name="return-value"></a>返回值

如果对象不相等，如果它们相等则为 FALSE，则返回 TRUE。

##  <a name="operator_lt"></a>  运算符 <

如果测试`CSid`对象或`SID`运算符左侧的结构是不会早于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*  
第一个`CSid`对象或`SID`结构进行比较。

*rhs*  
第二个`CSid`对象或`SID`结构进行比较。

### <a name="return-value"></a>返回值

如果返回 TRUE 的地址*lhs*对象是否小于的地址*rhs*对象，则返回 FALSE 否则。

### <a name="remarks"></a>备注

此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供与 c + + 标准库集合类的兼容性。

##  <a name="operator_gt"></a>  运算符 >

如果测试`CSid`对象或`SID`运算符左侧的结构是否大于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*  
第一个`CSid`对象或`SID`结构进行比较。

*rhs*  
第二个`CSid`对象或`SID`结构进行比较。

### <a name="return-value"></a>返回值

如果，则返回 TRUE 的地址*lhs*大于的地址*rhs*FALSE，否则为。

### <a name="remarks"></a>备注

此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供与 c + + 标准库集合类的兼容性。

##  <a name="operator_lt__eq"></a>  运算符 < =

如果测试`CSid`对象或`SID`运算符左侧的结构是否小于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*  
第一个`CSid`对象或`SID`结构进行比较。

*rhs*  
第二个`CSid`对象或`SID`结构进行比较。

### <a name="return-value"></a>返回值

如果返回 TRUE 的地址*lhs*小于或等于的地址*rhs*，则返回 FALSE 否则为。

### <a name="remarks"></a>备注

此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供与 c + + 标准库集合类的兼容性。

##  <a name="operator_gt__eq"></a>  运算符 > =

如果测试`CSid`对象或`SID`运算符左侧的结构是大于或等于`CSid`对象或`SID`（适用于 c + + 标准库兼容性） 右侧的结构。

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*  
第一个`CSid`对象或`SID`结构进行比较。

*rhs*  
第二个`CSid`对象或`SID`结构进行比较。

### <a name="return-value"></a>返回值

如果，则返回 TRUE 的地址*lhs*大于或等于的地址*rhs*FALSE，否则为。

### <a name="remarks"></a>备注

此运算符作用于的地址`CSid`对象或`SID`结构，并实现以提供与 c + + 标准库集合类的兼容性。

