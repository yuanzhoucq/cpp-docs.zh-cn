---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: c121ad99dfbe0021a263f324ccdb9a95441bba33
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740467"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft 专用**

编译器将 GUID 附加到使用**uuid**特性声明或定义的类或结构（仅限完整的 COM 对象定义）。

## <a name="syntax"></a>语法

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>备注

**Uuid**特性采用字符串作为其参数。 此字符串以带有或不带 **{}** 分隔符的普通注册表格式命名 GUID。 例如:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

此特性可应用于重新声明。 这允许系统标头提供接口`IUnknown`（如）的定义，并允许在其他标头（ \<如 comdef.h >）中重新声明来提供 GUID。

关键字[__uuidof](../cpp/uuidof-operator.md)可用于检索附加到用户定义类型的常量 GUID。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)