---
title: _com_ptr_t 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t
dev_langs:
- C++
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02e3c0833423f2e9eb8eebfe2c15a46466ef3c58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073560"
---
# <a name="comptrt-class"></a>_com_ptr_t 类

**Microsoft 专用**

一个 **_com_ptr_t**对象封装 COM 接口指针，称为"智能"指针。 此模板类管理资源分配和解除分配，通过对函数调用`IUnknown`成员函数： `QueryInterface`， `AddRef`，和`Release`。

智能指针通常由 _COM_SMARTPTR_TYPEDEF 宏所提供的 typedef 定义引用。 此宏采用接口名称和 IID 和声明的专用化 **_com_ptr_t**同名的接口和后缀的`Ptr`。 例如：

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

声明 **_com_ptr_t**专用化`IMyInterfacePtr`。

一套[函数模板](../cpp/relational-function-templates.md)，不隶属于此模板类，支持使用比较运算符右侧的智能指针的比较。

### <a name="construction"></a>构造

|||
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|构造 **_com_ptr_t**对象。|

### <a name="low-level-operations"></a>低级别运算

|||
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|调用`AddRef`成员函数的`IUnknown`上封装的接口指针。|
|[附加](../cpp/com-ptr-t-attach.md)|封装此智能指针的类型的原始接口指针。|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|创建一个对象的新实例`CLSID`或`ProgID`。|
|[分离](../cpp/com-ptr-t-detach.md)|提取并返回封装的接口指针。|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|将附加到给定的对象的现有实例`CLSID`或`ProgID`。|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|返回封装的接口指针。|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|调用`QueryInterface`成员函数的`IUnknown`上封装的接口指针。|
|[发布](../cpp/com-ptr-t-release.md)|调用`Release`成员函数的`IUnknown`上封装的接口指针。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](../cpp/com-ptr-t-operator-equal.md)|将新值分配到现有 **_com_ptr_t**对象。|
|[运算符 = =、 ！ =、 \<，>， \<=、 > =](../cpp/com-ptr-t-relational-operators.md)|比较的智能指针对象与另一个智能指针、 原始接口指针，则为 NULL。|
|[提取器](../cpp/com-ptr-t-extractors.md)|提取封装的 COM 接口指针。|

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头：** \<comip.h 声明 >

**Lib:** comsuppw.lib 或 comsuppwd.lib (请参阅[/zc: wchar_t （wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)有关详细信息)

## <a name="see-also"></a>请参阅

[编译器 COM 支持类](../cpp/compiler-com-support-classes.md)