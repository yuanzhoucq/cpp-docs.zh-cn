---
title: _com_ptr_t 类
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: eeaab22ded537cbbb211a79596b8383251af3ab7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189894"
---
# <a name="_com_ptr_t-class"></a>_com_ptr_t 类

**Microsoft 专用**

**_Com_ptr_t**对象封装 com 接口指针，并且称为 "智能" 指针。 此模板类通过对 `IUnknown` 成员函数的函数调用来管理资源分配和释放： `QueryInterface`、`AddRef`和 `Release`。

智能指针通常由 _COM_SMARTPTR_TYPEDEF 宏提供的 typedef 定义引用。 此宏采用接口名称和 IID，并声明使用接口名称加上 `Ptr`后缀的 **_com_ptr_t**的专用化。 例如：

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

声明 **_com_ptr_t**特殊化 `IMyInterfacePtr`。

一组[函数模板](../cpp/relational-function-templates.md)而不是此模板类的成员，它支持与比较运算符右侧的智能指针进行比较。

### <a name="construction"></a>建筑

|||
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|构造一个 **_com_ptr_t**对象。|

### <a name="low-level-operations"></a>低级别运算

|||
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|调用封装的接口指针上 `IUnknown` 的 `AddRef` 成员函数。|
|[附加](../cpp/com-ptr-t-attach.md)|封装此智能指针的类型的原始接口指针。|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|在给定 `CLSID` 或 `ProgID`的情况创建对象的新实例。|
|[分离](../cpp/com-ptr-t-detach.md)|提取并返回封装的接口指针。|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|如果给定 `CLSID` 或 `ProgID`，则附加到对象的现有实例。|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|返回封装的接口指针。|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|调用封装的接口指针上 `IUnknown` 的 `QueryInterface` 成员函数。|
|[版本](../cpp/com-ptr-t-release.md)|调用封装的接口指针上 `IUnknown` 的 `Release` 成员函数。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](../cpp/com-ptr-t-operator-equal.md)|将新值分配给现有的 **_com_ptr_t**对象。|
|[operators = =，！ =，\<，>，\<=，> =](../cpp/com-ptr-t-relational-operators.md)|将智能指针对象与另一个智能指针、原始接口指针或 NULL 进行比较。|
|[提取器](../cpp/com-ptr-t-extractors.md)|提取封装的 COM 接口指针。|

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头：** \<comip.h >

**Lib：** comsuppw.lib 或 comsuppwd.lib （有关详细信息，请参阅[/zc： Wchar_t （Wchar_t 为本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>另请参阅

[编译器 COM 支持类](../cpp/compiler-com-support-classes.md)
