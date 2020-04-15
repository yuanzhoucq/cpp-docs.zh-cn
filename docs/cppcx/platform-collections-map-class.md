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
ms.openlocfilehash: 7f41a924811be95160b06a2097db6103cde8fc11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354450"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map 类

表示一个 *映射*，它是键值对的集合。 实现[Windows：基础：集合：：I 可观察映射](/uwp/api/windows.foundation.collections.iobservablemap_k_v_)以帮助进行 XAML[数据绑定](/windows/uwp/data-binding/data-binding-in-depth)。

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

*五*<br/>
键值对中值的类型。

*C*<br/>
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。 默认情况下[，std：：减去\<K>](../standard-library/less-struct.md)。

*__is_valid_winrt_type（）* 编译器生成的函数，用于验证*K*和*V*的类型，并在类型无法存储在 Map 中时提供友好的错误消息。

### <a name="remarks"></a>备注

允许的类型是：

- 整数

- 接口类*

- 公共 ref 类

- value struct

- 公共枚举类

映射基本上是 [std::map](../standard-library/map-class.md)的包装器。 C++ 它是[Windows：：基础：集合：：iMap<Windows：基础：集合：：iKeyValuePair\<K，V>>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)和 I[可观察映射](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_)类型，这些类型通过公共 Windows 运行时接口传递。 如果你尝试在公共返回值或参数中使用 `Platform::Collections::Map` 类型，则将引发编译器错误 C3986。 您可以通过更改参数的类型或将值返回到[Windows：：基础：集合：：IMap\<K，V>来](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)修复错误。

有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[地图：地图](#ctor)|初始化 Map 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[地图：清除](#clear)|从当前 Map 对象中移除所有键值对。|
|[地图：第一](#first)|返回指定映射中第一个元素的迭代器。|
|[地图：：获取视图](#getview)|返回当前映射的只读视图，即 [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md)。|
|[地图：：哈斯键](#haskey)|确定当前 Map 中是否包含指定键。|
|[地图：：插入](#insert)|将指定的键值对添加到当前 Map 对象中。|
|[地图：：查找](#lookup)|检索当前 Map 对象中指定键处的元素。|
|[Map::Remove](#remove)|从当前 Map 对象中删除指定的键值对。|
|[地图：：大小](#size)|返回当前 Map 对象中的元素数目。|

### <a name="events"></a>事件

|||
|-|-|
|名称|说明|
|[映射：：映射已更改](#mapchanged)事件|当映射更改时发生。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Map`

### <a name="requirements"></a>要求

**标题：** 集合.h

**命名空间：** Platform::Collections

## <a name="mapclear-method"></a><a name="clear"></a>映射：清除方法

从当前 Map 对象中移除所有键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>映射：第一种方法

返回指定映射中第一个元素的迭代器，如果映射为空，则返回 `nullptr`。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>返回值

指定映射中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存 First（） 返回的迭代器的一个方便方法是将返回值分配给使用**自动**类型扣减关键字声明的变量。 例如，`auto x = myMap->First();` 。

## <a name="mapgetview-method"></a><a name="getview"></a>映射：：获取视图方法

返回当前地图的只读视图;即[，平台：集合：：mapView 类](../cppcx/platform-collections-mapview-class.md)，实现 [Windows：：基础：集合：集合：：IMapView\<K，V>]/uwp/api/Windows.Foundation.集合.IMapView_K_V_）接口。

### <a name="syntax"></a>语法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>返回值

`MapView` 对象。

## <a name="maphaskey-method"></a><a name="haskey"></a>映射：：有键方法

确定当前 Map 中是否包含指定键。

### <a name="syntax"></a>语法

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>参数

*关键*<br/>
用于定位 Map 元素的键。 *键*的类型是类型名称*K*。

### <a name="return-value"></a>返回值

如果找到密钥，**则为 true;** 否则，**假**。

## <a name="mapinsert-method"></a><a name="insert"></a>映射：：插入方法

将指定的键值对添加到当前 Map 对象中。

### <a name="syntax"></a>语法

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>参数

*关键*<br/>
键值对中的键部分。 *键*的类型是类型名称*K*。

*value*<br/>
键值对中的值部分。 *值*的类型是类型名称*V*。

### <a name="return-value"></a>返回值

如果当前 Map 中现有元素的键与*键*匹配，并且该元素的值部分设置为*值*，**则为 true。** 如果当前 Map 中不存在现有元素与*键*匹配，并且*键*和*值*参数被制成键值对，然后添加到当前 Map，**则为 false。**

## <a name="maplookup-method"></a><a name="lookup"></a>映射：：查找方法

检索与类型 K 的指定键关联的类型 V 的值（如果键存在）。

### <a name="syntax"></a>语法

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>参数

*关键*<br/>
用于定位映射中的元素的键。 *键*的类型是类型名称*K*。

### <a name="return-value"></a>返回值

与*键*配对的值。 返回值的类型为类型名称*V*。

### <a name="remarks"></a>备注

如果密钥不存在，则引发[一个平台：：OutOfsexception。](../cppcx/platform-outofboundsexception-class.md)

## <a name="mapmap-constructor"></a><a name="ctor"></a>映射：：地图构造函数

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

*Init*<br/>
当前映射的类型名称。

*Comp*<br/>
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。

*米*<br/>
对 用于初始化当前映射`map Class`的 引用或[rvalue。](../cpp/lvalues-and-rvalues-visual-cpp.md)

*第一*<br/>
用于初始化当前映射的一系列元素中的第一个元素的输入迭代器。

*最后*<br/>
用于初始化当前映射的一系列元素之后的第一个元素的输入迭代器。

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>映射：：映射已更改事件

项目插入到映射中或从映射中移除时引发。

### <a name="syntax"></a>语法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>属性值/返回值

[MapChangeEventHandler\<K，V>，](/uwp/api/windows.foundation.collections.mapchangedeventhandler)其中包含有关引发事件的对象以及发生的更改类型的信息。 另请参阅[IMapChangeEventArgs\<K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_)和[集合更改枚举](/uwp/api/windows.foundation.collections.collectionchange)。

## <a name="net-framework-equivalent"></a>.NET Framework 等效项

使用 C# 或可视化基本项目 IMap\<K 的 Windows 运行时应用\<，V>为 I字典 K，V>。

## <a name="mapremove-method"></a><a name="remove"></a>映射：：删除方法

从当前 Map 对象中删除指定的键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>参数

*关键*<br/>
键值对中的键部分。 *键*的类型是类型名称*K*。

## <a name="mapsize-method"></a><a name="size"></a>映射：大小方法

返回地图中的[Windows：：基础：集合：：IKeyValuePair\<K，V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_)元素。

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
