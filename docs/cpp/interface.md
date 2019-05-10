---
title: __interface
ms.date: 05/07/2019
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 7c95e3700b4124c4793e0214ed3b06ecfeee72f1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222076"
---
# <a name="interface"></a>__interface

**Microsoft 专用**

MicrosoftC++接口可以按如下所示定义：

- 可从零个或多个基接口继承。

- 不能从基类继承。

- 只能包含公共的纯虚方法。

- 不能包含构造函数、析构函数或运算符。

- 不能包含静态方法。

- 不能包含数据成员；允许使用属性。

## <a name="syntax"></a>语法

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>备注

一个C++[类](../cpp/class-cpp.md)或[结构](../cpp/struct-cpp.md)未能实现这些规则，但 **__interface**强制实施它们。

例如，以下是示例接口定义：

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

有关托管接口的信息，请参阅[接口类](../extensions/interface-class-cpp-component-extensions.md)。

请注意，您无需显式指示 `CommitX` 和 `get_X` 函数是纯虚函数。 第一个函数的等效声明为：

```cpp
virtual HRESULT CommitX() = 0;
```

**__interface**意味着[novtable](../cpp/novtable.md) **__declspec**修饰符。

## <a name="example"></a>示例

以下示例演示如何使用接口中声明的属性。

```cpp
// deriv_interface.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <string.h>
#include <comdef.h>
#include <stdio.h>

[module(name="test")];

[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]
__interface IFace {
   [ id(0) ] int int_data;
   [ id(5) ] BSTR bstr_data;
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class MyClass : public IFace {
private:
    int m_i;
    BSTR m_bstr;

public:
    MyClass()
    {
        m_i = 0;
        m_bstr = 0;
    }

    ~MyClass()
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
    }

    int get_int_data()
    {
        return m_i;
    }

    void put_int_data(int _i)
    {
        m_i = _i;
    }

    BSTR get_bstr_data()
    {
        BSTR bstr = ::SysAllocString(m_bstr);
        return bstr;
    }

    void put_bstr_data(BSTR bstr)
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
        m_bstr = ::SysAllocString(bstr);
    }
};

int main()
{
    _bstr_t bstr("Testing");
    CoInitialize(NULL);
    CComObject<MyClass>* p;
    CComObject<MyClass>::CreateInstance(&p);
    p->int_data = 100;
    printf_s("p->int_data = %d\n", p->int_data);
    p->bstr_data = bstr;
    printf_s("bstr_data = %S\n", p->bstr_data);
}
```

```Output
p->int_data = 100
bstr_data = Testing
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[接口特性](../windows/attributes/interface-attributes.md)