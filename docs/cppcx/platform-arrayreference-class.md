---
title: Platform::ArrayReference 类
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: e9dd16ad6c3f53c5562b0419197a582c06fbc642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354793"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference 类

`ArrayReference` 是在你希望用输入数据填充 C 样式数组时可以在输入参数中替换 [Platform::Array^](../cppcx/platform-array-class.md) 的优化类型。

## <a name="syntax"></a>语法

```cpp
class ArrayReference
```

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[数组参考：：数组参考](#ctor)|初始化 `ArrayReference` 类的新实例。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[数组参考：：运算符（） 运算符](#operator-call)|将此 `ArrayReference` 转换为 `Platform::Array<T>^*`。|
|[ArrayReference::operator= 运算符](#operator-assign)|将另一 `ArrayReference` 的内容分配给此实例。|

## <a name="exceptions"></a>例外

### <a name="remarks"></a>备注

通过使用 `ArrayReference` 填充 C 样式数组，可避免在先复制到 `Platform::Array` 变量，然后复制到 C 样式数组时涉及额外的重复操作。 当你使用 `ArrayReference`时，只有一个复制操作。 有关代码示例，请参阅[数组和 WriteOnlyarray](../cppcx/array-and-writeonlyarray-c-cx.md)。

### <a name="requirements"></a>要求

**受支持的最小客户端：** 视窗 8

**受支持的服务器最少：** 视窗服务器 2012

**命名空间：** Platform

**标头：** vccorlib.h

## <a name="arrayreferencearrayreference-constructor"></a><a name="ctor"></a>数组参考：：数组参考构造函数

初始化平台的新实例[：：数组引用](../cppcx/platform-arrayreference-class.md)类。

### <a name="syntax"></a>语法

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>参数

*数据阿格*<br/>
指向数组数据的指针。

*尺寸阿格*<br/>
源数组中的元素数。

*其他阿格*<br/>
其数据将移动以初始化新实例的 `ArrayReference` 对象。

### <a name="remarks"></a>备注

## <a name="arrayreferenceoperator-operator"></a><a name="operator-assign"></a>数组参考：：运算符= 运算符

使用移动语义将指定对象分配给当前[平台：：ArrayReference 对象](../cppcx/platform-arrayreference-class.md)。

### <a name="syntax"></a>语法

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>参数

*其他阿格*<br/>
移动到当前 `ArrayReference` 对象的对象。

### <a name="return-value"></a>返回值

对类型为 `ArrayReference` 的对象的引用。

### <a name="remarks"></a>备注

`Platform::ArrayReference` 是标准 C++ 类模板，而不是 ref 类。

## <a name="arrayreferenceoperator-operator"></a><a name="operator-call"></a>数组参考：：运算符（） 运算符

将当前[平台：：ArrayReference](../cppcx/platform-arrayreference-class.md)对象转换回[平台：：数组](../cppcx/platform-array-class.md)类。

### <a name="syntax"></a>语法

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>返回值

`Array<TArg>^` 类型的句柄到对象

### <a name="remarks"></a>备注

[平台：array参照](../cppcx/platform-arrayreference-class.md)是一个标准的C++类模板，[而平台：：数组](../cppcx/platform-array-class.md)是一个 ref 类。

## <a name="see-also"></a>另请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)
