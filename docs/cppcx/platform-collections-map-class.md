---
title: Platform::Collections::Map 类
ms.date: 10/01/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
ms.openlocfilehash: 30dbc71a03c398c77124738b2477a3563191d50d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214979"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map 类

表示一个 *映射*，它是键值对的集合。 实现[Windows：： Foundation：：集合：： IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2)以帮助 XAML[数据绑定](/windows/uwp/data-binding/data-binding-in-depth)。

## <a name="syntax"></a>语法

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>参数

*温度*<br/>
键值对中键的类型。

*向量*<br/>
键值对中值的类型。

*C*<br/>
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。 默认情况下， [std：： \<K> less](../standard-library/less-struct.md)。

*__is_valid_winrt_type （）* 编译器生成的函数，用于验证*K*和*V*类型，并在此类型无法存储在映射中时提供友好错误消息。

### <a name="remarks"></a>备注

允许的类型是：

- integers

- 接口类 ^

- 公共 ref 类

- value struct

- 公共枚举类

映射基本上是 [std::map](../standard-library/map-class.md)的包装器。 它是[windows：： foundation：：集合：： IMap<windows：： foundation：：集合：： IKeyValuePair \<K,V> > ](/uwp/api/windows.foundation.collections.imap-2)和[IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2)类型的 c + + 具体实现，这些类型通过公共 Windows 运行时接口传递。 如果你尝试在公共返回值或参数中使用 `Platform::Collections::Map` 类型，则将引发编译器错误 C3986。 可以通过将参数或返回值的类型更改为[Windows：： Foundation：：集合：： IMap \<K,V> ](/uwp/api/windows.foundation.collections.imap-2)来修复此错误。

有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[Map：： Map](#ctor)|初始化 Map 类的新实例。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[Map：： Clear](#clear)|从当前 Map 对象中移除所有键值对。|
|[Map：： First](#first)|返回指定映射中第一个元素的迭代器。|
|[Map：： GetView](#getview)|返回当前映射的只读视图，即 [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md)。|
|[Map：： HasKey](#haskey)|确定当前 Map 中是否包含指定键。|
|[Map：： Insert](#insert)|将指定的键值对添加到当前 Map 对象中。|
|[Map：： Lookup](#lookup)|检索当前 Map 对象中指定键处的元素。|
|[Map::Remove](#remove)|从当前 Map 对象中删除指定的键值对。|
|[Map：： Size](#size)|返回当前 Map 对象中的元素数目。|

### <a name="events"></a>事件

|||
|-|-|
|名称|描述|
|[Map：： MapChanged](#mapchanged)事件|当映射更改时发生。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Map`

### <a name="requirements"></a>要求

**标头：** 集合。h

**命名空间：** Platform::Collections

## <a name="mapclear-method"></a><a name="clear"></a>Map：： Clear 方法

从当前 Map 对象中移除所有键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>Map：： First 方法

返回指定映射中第一个元素的迭代器， **`nullptr`** 如果映射为空，则返回。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>返回值

指定映射中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存第一个（）返回的迭代器的一种简便方法是将返回值分配给使用 **`auto`** 类型推导关键字声明的变量。 例如，`auto x = myMap->First();`。

## <a name="mapgetview-method"></a><a name="getview"></a>Map：： GetView 方法

返回当前映射的只读视图;也就是说， [Platform：： IMapView：： MapView 类，该类](../cppcx/platform-collections-mapview-class.md)实现[Windows：： Foundation：：集合：： \<K,V> ](/uwp/api/windows.foundation.collections.imapview-2)接口。

### <a name="syntax"></a>语法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>返回值

`MapView` 对象。

## <a name="maphaskey-method"></a><a name="haskey"></a>Map：： HasKey 方法

确定当前 Map 中是否包含指定键。

### <a name="syntax"></a>语法

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>参数

*key*<br/>
用于定位 Map 元素的键。 *键*类型为 typename *K*。

### <a name="return-value"></a>返回值

**`true`** 如果找到该键，则为;否则为 **`false`** 。

## <a name="mapinsert-method"></a><a name="insert"></a>Map：： Insert 方法

将指定的键值对添加到当前 Map 对象中。

### <a name="syntax"></a>语法

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>参数

*key*<br/>
键值对中的键部分。 *键*类型为 typename *K*。

*value*<br/>
键值对中的值部分。 *值*的类型为 typename *V*。

### <a name="return-value"></a>返回值

**`true`** 如果当前映射中现有元素的键与*键*匹配，并且该元素的值部分设置为*value*。 **`false`** 如果当前映射中没有任何现有元素匹配*键*，并且*键*和*值*参数成为键值对并随后添加到当前映射中，则为。

## <a name="maplookup-method"></a><a name="lookup"></a>Map：： Lookup 方法

检索与类型 K 的指定键关联的类型 V 的值（如果键存在）。

### <a name="syntax"></a>语法

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>参数

*key*<br/>
用于定位映射中的元素的键。 *键*类型为 typename *K*。

### <a name="return-value"></a>返回值

与*键*配对的值。 返回值的类型为 typename *V*。

### <a name="remarks"></a>备注

如果该键不存在，则将引发[Platform：： OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) 。

## <a name="mapmap-constructor"></a><a name="ctor"></a>Map：： Map 构造函数

初始化 Map 类的新实例。

### <a name="syntax"></a>语法

```cpp
explicit Map(const C& comp = C());
explicit Map(const StdMap& m);
explicit Map(StdMap&& m ;
template <typename InIt>
Map(
   InItfirst,
   InItlast,
   const C& comp = C());
```

### <a name="parameters"></a>参数

*InIt*<br/>
当前映射的类型名称。

*comp*<br/>
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。

*m*<br/>
[rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) `map Class` 用于初始化当前映射的的引用或对的右值。

*first*<br/>
用于初始化当前映射的一系列元素中的第一个元素的输入迭代器。

*last*<br/>
用于初始化当前映射的一系列元素之后的第一个元素的输入迭代器。

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>Map：： MapChanged 事件

项目插入到映射中或从映射中移除时引发。

### <a name="syntax"></a>语法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>属性值/返回值

一个[MapChangedEventHandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) ，其中包含有关引发事件的对象的信息，以及发生的更改类型。 另请[参阅 \<K> Imapchangedeventargs<k>](/uwp/api/windows.foundation.collections.imapchangedeventargs-1)和[CollectionChange 枚举](/uwp/api/windows.foundation.collections.collectionchange)。

## <a name="net-framework-equivalent"></a>.NET Framework 等效项

使用 c # 或 Visual Basic 项目 IMap \<K,V> 作为 IDictionary Windows 运行时应用 \<K,V> 。

## <a name="mapremove-method"></a><a name="remove"></a>Map：： Remove 方法

从当前 Map 对象中删除指定的键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>参数

*key*<br/>
键值对中的键部分。 *键*类型为 typename *K*。

## <a name="mapsize-method"></a><a name="size"></a>Map：： Size 方法

返回映射中[Windows：： Foundation：：集合：： IKeyValuePair \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素的数目。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

Map 中的元素数目。

## <a name="see-also"></a>另请参阅

[集合 (C++/CX)](collections-c-cx.md)<br/>
[平台命名空间](platform-namespace-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
