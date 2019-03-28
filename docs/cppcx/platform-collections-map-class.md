---
title: Platform::Collections::Map 类
ms.date: 03/27/2019
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
ms.openlocfilehash: ce50290217c7c06e26f26fc50564d3e37c873157
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565277"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map 类

表示一个 *映射*，它是键值对的集合。

## <a name="syntax"></a>语法

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>参数

*K*<br/>
键值对中键的类型。

*V*<br/>
键值对中值的类型。

*C*<br/>
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。 默认情况下[std:: less\<K >](../standard-library/less-struct.md)。

*__is_valid_winrt_type()* 编译器生成的函数，用于验证的类型*K*并*V*和此类型不能存储在映射中时提供友好错误消息。

### <a name="remarks"></a>备注

允许的类型包括：

- 整数

- 接口类 ^

- 公共 ref 类

- value struct

- 公共枚举类

映射基本上是 [std::map](../standard-library/map-class.md)的包装器。 它是 c + + 具体实现[Windows::Foundation::Collections::IMap < Windows::Foundation::Collections::IKeyValuePair\<K，V >>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)并[IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_)Windows 运行时接口的公共之间传递的类型。 如果你尝试在公共返回值或参数中使用 `Platform::Collections::Map` 类型，则将引发编译器错误 C3986。 可通过更改参数或返回值的类型来修复该错误[Windows::Foundation::Collections::IMap\<K，V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)。

有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[Map::Map](#ctor)|初始化 Map 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Map::Clear](#clear)|从当前 Map 对象中移除所有键值对。|
|[Map::First](#first)|返回指定映射中第一个元素的迭代器。|
|[Map::GetView](#getview)|返回当前映射的只读视图，即 [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md)。|
|[Map::HasKey](#haskey)|确定当前 Map 中是否包含指定键。|
|[Map::Insert](#insert)|将指定的键值对添加到当前 Map 对象中。|
|[Map::Lookup](#lookup)|检索当前 Map 对象中指定键处的元素。|
|[Map::Remove](#remove)|从当前 Map 对象中删除指定的键值对。|
|[Map::Size](#size)|返回当前 Map 对象中的元素数目。|

### <a name="events"></a>事件

|||
|-|-|
|名称|描述|
|[Map:: mapchanged](#mapchanged)事件|当映射更改时发生。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Map`

### <a name="requirements"></a>要求

**标头：** collection.h

**命名空间：** Platform::Collections

## <a name="clear"></a>  Map:: clear 方法

从当前 Map 对象中移除所有键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Clear();
```

## <a name="first"></a>  Map:: first 方法

返回指定映射中第一个元素的迭代器，如果映射为空，则返回 `nullptr`。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>返回值

指定映射中第一个元素的迭代器。

### <a name="remarks"></a>备注

保留 first （） 返回的迭代器的简便方法是将返回值分配为使用声明的变量**自动**类型推导关键字。 例如 `auto x = myMap->First();`。

## <a name="getview"></a>  Map:: getview 方法

返回当前映射的只读视图即[& 类](../cppcx/platform-collections-mapview-class.md)，它可以实现 [Windows::Foundation::Collections::IMapView\<K，V >] / uwp/api/Windows.Foundation.Collections.IMapView_K_V_) 接口。

### <a name="syntax"></a>语法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>返回值

一个 `MapView` 对象。

## <a name="haskey"></a>  Map:: haskey 方法

确定当前 Map 中是否包含指定键。

### <a name="syntax"></a>语法

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>参数

*key*<br/>
用于定位 Map 元素的键。 类型*键*是 typename *K*。

### <a name="return-value"></a>返回值

**true**如果该键; 否则为**false**。

## <a name="insert"></a>  Map:: insert 方法

将指定的键值对添加到当前 Map 对象中。

### <a name="syntax"></a>语法

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>参数

*key*<br/>
键值对中的键部分。 类型*键*是 typename *K*。

*值*<br/>
键值对中的值部分。 类型*值*是 typename *V*。

### <a name="return-value"></a>返回值

**true**如果当前映射中的现有元素的键匹配*密钥*，该元素的值部分设置为*值*。 **false**如果当前映射中的没有任何现有元素匹配*密钥*并且*密钥*并*值*参数构成键值对并随后将添加到当前映射。

## <a name="lookup"></a>  Map:: lookup 方法

检索与类型 K 的指定键关联的类型 V 的值（如果键存在）。

### <a name="syntax"></a>语法

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>参数

*key*<br/>
用于定位映射中的元素的键。 类型*键*是 typename *K*。

### <a name="return-value"></a>返回值

与成对的值*密钥*。 返回值的类型是 typename *V*。

### <a name="remarks"></a>备注

如果不存在该键，则[platform:: outofboundsexception](../cppcx/platform-outofboundsexception-class.md)引发。

## <a name="ctor"></a>  Map:: map 构造函数

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
引用或[rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)到`map Class`用于初始化当前映射。

*first*<br/>
用于初始化当前映射的一系列元素中的第一个元素的输入迭代器。

*last*<br/>
用于初始化当前映射的一系列元素之后的第一个元素的输入迭代器。

## <a name="mapchanged"></a>  Map:: mapchanged 事件

项目插入到映射中或从映射中移除时引发。

### <a name="syntax"></a>语法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>属性值/返回值

一个[MapChangedEventHandler\<K，V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler)包含引发事件，并已发生更改的类型的对象有关的信息。 另请参阅[IMapChangedEventArgs\<K >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_)并[CollectionChange 枚举](/uwp/api/windows.foundation.collections.collectionchange)。

## <a name="net-framework-equivalent"></a>.NET Framework 等效项

项目使用 C# 或 Visual Basic 的 Windows 运行时应用的 IMap\<K，V > 作为 IDictionary\<K，V >。

## <a name="remove"></a>  Map:: remove 方法

从当前 Map 对象中删除指定的键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>参数

*key*<br/>
键值对中的键部分。 类型*键*是 typename *K*。

## <a name="size"></a>  Map:: size 方法

返回的数[Windows::Foundation::Collections::IKeyValuePair\<K，V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_)映射中的元素。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

Map 中的元素数目。

## <a name="see-also"></a>请参阅

[平台 Namespace](platform-namespace-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
