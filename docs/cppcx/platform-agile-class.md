---
title: "Platform:: agile 类 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
dev_langs:
- C++
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c670ffc10858e709129caf9fabf80b656cbdb18
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="platformagile-class"></a>Platform::Agile 类
表示将 MashalingBehavior=Standard 作为敏捷对象（这可以大大降低出现运行时线程处理异常的机率）的对象。 `Agile<T>` 使非敏捷对象可以调用相同或不同线程调用，或是从相同或不同线程进行调用。 有关详细信息，请参阅[线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <typename T>  
class Agile;  
```  
  
#### <a name="parameters"></a>参数  
 T  
 非敏捷类的类型名称。  
  
### <a name="remarks"></a>备注  
 Windows 运行时中的类的大部分都是敏捷的。 敏捷对象可以调用相同或不同线程中的进程内或进程外对象，或是由该对象进行调用。 如果对象不是敏捷对象，请在 `Agile<T>` 对象（这是敏捷对象）中包装非敏捷对象。 随后可以封送 `Agile<T>` 对象，并且可以使用基础非敏捷对象。  
  
 `Agile<T>` 类是本机标准 C++ 类，需要 `agile.h`。 它表示非敏捷对象和敏捷对象的 *上下文*。 上下文指定敏捷对象的线程处理模型和封送处理行为。 操作系统使用上下文来确定如何封送对象。  
  
### <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Agile::Agile](#ctor)|初始化 Agile 类的新实例。|  
|[Agile::~Agile 析构函数](#dtor)|销毁敏捷类的当前实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Agile::Get](#get)|返回用当前敏捷对象表示的对象的句柄。|  
|[Agile::GetAddressOf](#getaddressof)|重新初始化当前敏捷对象，然后返回类型为 `T`的对象的句柄地址。|  
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|将句柄的地址返回到用当前敏捷对象表示的对象。|  
|[Agile::Release](#release)|放弃当前敏捷对象的基础对象和上下文。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[Agile::operator->](#operator-arrow)|检索用当前敏捷对象表示的对象的句柄。|  
|[Agile::operator=](#operator-assign)|将指定值分配给当前敏捷对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Object`  
  
 `Agile`  
  
### <a name="requirements"></a>惠?  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **标头：** agile.h  

## <a name="ctor"></a>  Agile:: agile 构造函数
初始化 Agile 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
 Agile();  
  
Agile(T^ object);   
  
Agile(const Agile<T>& object);  
  
Agile(Agile<T>&& object);  
  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 模板类型名称参数指定的类型。  
  
 `object`  
 在此构造函数的第二个版本中，用于初始化新的 Agile 实例的对象。 在第三个版本中，复制到新的 Agile 实例的对象。 在第四个版本中，移动到新的 Agile 实例的对象。  
  
### <a name="remarks"></a>备注  
 此构造函数的第一个版本是默认构造函数。 第二个版本从 `object` 参数指定的对象初始化新实例 Agile 类。 第三个版本是复制构造函数。 第四个版本是移动构造函数。 此构造函数不能引发异常。  

## <a name="dtor"></a>  Agile:: ~ Agile 析构函数
销毁敏捷类的当前实例。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
~Agile();  
```  
  
### <a name="remarks"></a>备注  
 此析构函数也会释放当前敏捷对象表示的对象。  
  
## <a name="get"></a>   Agile:: get 方法
返回用当前敏捷对象表示的对象的句柄。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
   T^ Get() const  
;  
```  
  
### <a name="return-value"></a>返回值  
 用当前敏捷对象表示的对象的句柄。  
  
 返回值的类型实际是未公开的内部类型。 保留返回值一种简便方式是将它分配给使用声明的变量**自动**类型推导关键字。 例如 `auto x = myAgileTvariable->Get();`。  
  
## <a name="getaddressof"></a>  Agile:: getaddressof 方法
重新初始化当前敏捷对象，然后返回类型为 `T`的对象的句柄地址。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
T^* GetAddressOf()   
throw();  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 模板类型名称参数指定的类型。  
  
### <a name="return-value"></a>返回值  
 类型的对象的句柄的地址`T`。  
  
### <a name="remarks"></a>备注  
 此操作释放类型的对象的当前表示`T`，如果任何; 重新初始化敏捷对象的数据成员; 获取当前线程上下文中;，然后返回可以表示句柄到对象变量的地址非敏捷对象。 若要使敏捷类实例以代表一个对象，使用赋值运算符 ([agile:: operator =](#operator-assign)) 将对象分配给敏捷类实例。  

## <a name="getaddressofforinout"></a>  Agile:: getaddressofforinout 方法
将句柄的地址返回到用当前敏捷对象表示的对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
T^* GetAddressOfForInOut()  throw();  
  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 模板类型名称参数指定的类型。  
  
### <a name="return-value"></a>返回值  
 返回到用当前敏捷对象表示的对象的句柄的地址。  
  
### <a name="remarks"></a>备注  
 此操作获取当前线程上下文，然后将句柄的地址返回到基础对象。  

## <a name="release"></a>  Agile:: release 方法
放弃当前敏捷对象的基础对象和上下文。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
void Release() throw();  
  
```  
  
### <a name="remarks"></a>备注  
 放弃当前敏捷对象的基础对象和上下文（如果存在），然后将敏捷对象的值设置为 null。  

## <a name="operator-arrow"></a>  Agile:: operator-&gt;运算符
检索用当前敏捷对象表示的对象的句柄。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
T^ operator->()   
const throw();  
```  
  
### <a name="return-value"></a>返回值  
 用当前敏捷对象表示的对象的句柄。  
  
 此运算符实际返回未公开的内部类型。 保留返回值一种简便方式是将它分配给使用声明的变量**自动**类型推导关键字。  

## <a name="operator-assign"></a>  Agile::operator= Operator
将指定对象分配给当前敏捷对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
   Agile<T> operator=(T^ object) throw();  
  
   Agile<T> operator=(  
      const Agile<T>& object  
) throw();  
  
   Agile<T> operator=(  
      Agile<T>&& object  
) throw();  
  
   T^ operator=(  
      IUnknown* lp  
) throw();  
  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 模板类型名称指定的类型。  
  
 `object`  
 复制或移动到当前敏捷对象的对象或对象句柄。  
  
 `lp`  
 对象的 IUnknown 接口指针。  
  
### <a name="return-value"></a>返回值  
 `T` 类型的对象的句柄  
  
### <a name="remarks"></a>备注  
 赋值运算符的第一个版本将引用类型的句柄复制到当前敏捷对象。 第二个版本将对敏捷类型的引用复制到当前敏捷对象。 第三个版本将一个敏捷类型移到当前敏捷对象。 第四个版本将 COM 对象的指针移到当前敏捷对象。  
  
 赋值操作自动保存当前敏捷对象的上下文。 
       
## <a name="see-also"></a>请参阅  
 [平台 Namespace](platform-namespace-c-cx.md)