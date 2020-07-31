---
title: enable_shared_from_this 类
ms.date: 11/04/2016
f1_keywords:
- memory/std::enable_shared_from_this
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
ms.openlocfilehash: 9b417eabdaf6002724a0fa947dd97dea6f0df0a5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217774"
---
# <a name="enable_shared_from_this-class"></a>enable_shared_from_this 类

帮助生成一个 `shared_ptr`。

## <a name="syntax"></a>语法

```cpp
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
    weak_ptr<T> weak_from_this() noexcept;
    weak_ptr<T const> weak_from_this() const noexcept;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
};
```

### <a name="parameters"></a>参数

*Ty*\
由共享指针控制的类型。

## <a name="remarks"></a>备注

从 `enable_shared_from_this` 派生的对象可以在成员函数中使用 `shared_from_this` 方法来创建实例的 [shared_ptr](../standard-library/shared-ptr-class.md) 所有者，这些所有者与现有 `shared_ptr` 所有者共享所有权。 否则，如果使用创建一个新 `shared_ptr` 的 **`this`** ，它与现有 `shared_ptr` 所有者不同，后者可能导致无效引用或导致对象被删除多次。

保护构造函数、析构函数和赋值运算符，以帮助预防意外的误用。 模板参数类型*Ty*必须是派生类的类型。

有关使用示例，请参阅 [enable_shared_from_this::shared_from_this](#shared_from_this)。

## <a name="shared_from_this"></a><a name="shared_from_this"></a>shared_from_this

生成与现有 `shared_ptr` 所有者共享实例所有权的 `shared_ptr`。

```cpp
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```

### <a name="remarks"></a>备注

从 `enable_shared_from_this` 基类派生对象时，`shared_from_this` 模板成员函数返回与现有 `shared_ptr` 所有者共享此实例所有权的 [shared_ptr 类](../standard-library/shared-ptr-class.md)对象。 否则，如果您从创建一个新 `shared_ptr` 的 **`this`** ，它将不同于现有 `shared_ptr` 所有者，这会导致无效引用或导致对象被删除多次。 如果在尚未由 `shared_ptr` 对象所有的实例上调用 `shared_from_this`，则不会定义行为。

### <a name="example"></a>示例

```cpp
// std_memory_shared_from_this.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

struct base : public std::enable_shared_from_this<base>
{
    int val;
    shared_ptr<base> share_more()
    {
        return shared_from_this();
    }
};

int main()
{
    auto sp1 = make_shared<base>();
    auto sp2 = sp1->share_more();

    sp1->val = 3;
    cout << "sp2->val == " << sp2->val << endl;
    return 0;
}
```

```Output
sp2->val == 3
```

## <a name="weak_from_this"></a><a name="weak_from_this"></a>weak_from_this

```cpp
weak_ptr<T> weak_from_this() noexcept;
weak_ptr<T const> weak_from_this() const noexcept;
```
