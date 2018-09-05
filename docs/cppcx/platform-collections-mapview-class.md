---
title: '& 类 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
dev_langs:
- C++
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e1dfbcff7e9e470992b0799aac1c87984b52ed50
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755903"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView 类
将一个只读视图表示为一个 映射，这是键值对的集合。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = ::std::less<K>>  
ref class MapView sealed;  
```  
  
#### <a name="parameters"></a>参数  
 `K`  
 键值对中键的类型。  
  
 `V`  
 键值对中值的类型。  
  
 `C`  
 提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在 MapView 中的相对顺序。 默认情况下[std:: less\<K >](../standard-library/less-struct.md)。  
  
### <a name="remarks"></a>备注  
 MapView 是具体的 c + + 实现[Windows::Foundation::Collections::IMapView \<K，V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)跨应用程序二进制接口 (ABI) 传递的接口。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。  
  
### <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Mapview:: Mapview](#ctor)|初始化 MapView 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Mapview:: First](#first)|返回初始化为映射视图中第一个元素的迭代器。|  
|[Mapview:: Haskey](#haskey)|确定当前 MapView 中是否包含指定键。|  
|[Mapview:: Lookup](#lookup)|检索当前 MapView 对象中指定键处的元素。|  
|[Mapview:: Size](#size)|返回当前 MapView 对象中的元素数目。|  
|[MapView::Split](#split)|将原始 MapView 对象拆分成两个 MapView 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `MapView`  
  
### <a name="requirements"></a>要求  
 **标头：** collection.h  
  
 **命名空间：** Platform::Collections  


## <a name="first"></a> Mapview:: First 方法
返回指定映射视图中第一个元素的迭代器。  
  
### <a name="syntax"></a>语法  
  
```    
virtual Windows::Foundation::Collections::IIterator<  
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
### <a name="return-value"></a>返回值  
 指定映射视图中第一个元素的迭代器。  
  
### <a name="remarks"></a>备注  
 保留 first （） 返回的迭代器的简便方法是将返回值分配为使用声明的变量**自动**类型推导关键字。 例如 `auto x = myMapView->First();`。  
  


## <a name="haskey"></a>  Mapview:: Haskey 方法
确定当前 MapView 中是否包含指定键。  
  
### <a name="syntax"></a>语法  
  
```  
  
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>参数  
 `key`  
 用于定位 MapView 元素的键。 类型`key`是 typename *K*。  
  
### <a name="return-value"></a>返回值  
 如果找到该键，则为 `true`；否则为 `false`。  
  


##  <a name="lookup"></a> Mapview:: Lookup 方法
检索与类型 K 的指定键关联的类型 V 的值。  
  
### <a name="syntax"></a>语法  
  
```  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>参数  
 `key`  
 用于定位 MapView 中的元素的键。 类型`key`是 typename *K*。  
  
### <a name="return-value"></a>返回值  
 与 `key` 配对的值。 返回值的类型是 typename *V*。  
  


##  <a name="ctor"></a> Mapview:: Mapview 构造函数
初始化 MapView 类的新实例。  
  
### <a name="syntax"></a>语法  
  
```cpp  
explicit MapView(const C& comp = C());  
  
explicit MapView(const ::std::map<K, V, C>& m);  
  
explicit MapView(std::map<K, V, C>&& m);  
  
template <typename InIt> MapView(  
    InIt first,  
    InIt last,  
    const C& comp = C());  
  
MapView(
    ::std::initializer_list<std::pair<const K, V>> il,  
    const C& comp = C());  
```  
  
### <a name="parameters"></a>参数  
 `InIt`  
 当前 MapView 的类型名称。  
  
 `comp`  
 可以将两个元素值作为排序键加以比较，以决定它们在 MapView 中的相对顺序的函数对象。  
  
 `m`  
 引用或[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)到`map Class`用于初始化当前 MapView。  
  
 `first`  
 用于初始化当前 MapView 的一系列元素中的第一个元素的输入迭代器。  
  
 `last`  
 用于初始化当前 MapView 的一系列元素之后的第一个元素的输入迭代器。  
  
 il  
 一个[std:: initializer_list < std:: pair\<K，V >>](../standard-library/initializer-list-class.md)其元素将插入 MapView。  



##  <a name="size"></a> Mapview:: Size 方法
返回当前 MapView 对象中的元素数目。  
  
### <a name="syntax"></a>语法  
  
```cpp  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>返回值  
 当前 MapView 中的元素数目。  
  


##  <a name="split"></a> Mapview:: Split 方法
将当前 MapView 对象分成两个 MapView 对象。 此方法为非操作性的。  
  
### <a name="syntax"></a>语法  
  
```  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * secondPartition);  
```  
  
### <a name="parameters"></a>参数  
 `firstPartition`  
 原始 MapView 对象的第一部分。  
  
 `secondPartition`  
 原始 MapView 对象的第二部分。  
  
### <a name="remarks"></a>备注  
 此方法为非操作性的，它不执行任何操作。  
    
## <a name="see-also"></a>请参阅  
 [平台 Namespace](platform-namespace-c-cx.md)