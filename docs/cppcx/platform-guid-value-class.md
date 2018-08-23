---
title: 'Platform:: guid 值类 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
dev_langs:
- C++
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 102585cf7148923f584591102712278847ee7573
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601249"
---
# <a name="platformguid-value-class"></a>Platform::Guid 值类
代表 Windows 运行时类型系统中的 [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) 类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public value struct Guid  
```  
  
### <a name="members"></a>成员  
 Guid 具有从 [Platform::Object Class](../cppcx/platform-object-class.md)派生的 Equals()、GetHashCode() 和 ToString() 方法，以及从 [Platform::Type Class](../cppcx/platform-type-class.md)。 Guid 还具有下列成员。  
  
|成员|描述|  
|------------|-----------------|  
|[Guid](#ctor)|初始化 Guid 结构的新实例。|  
|[operator==](#operator-equality)|等于运算符。|  
|[operator!=](#operator-not-equal)|不等于运算符。|  
|[operator()](#operator-call)|将 Guid 转换为 GUID。|  
  
### <a name="remarks"></a>备注  
 有关如何生成新的 platform:: guid 使用 Windows 函数的示例[CoCreateGuid](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateguid)，请参阅[WinRT 组件： 如何生成 GUID？](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  

 
## <a name="ctor"></a> Guid:: guid 构造函数
初始化 Guid 结构的新实例。  
  
### <a name="syntax"></a>语法  
  
```cpp  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        unsigned char d,   
        unsigned char e,   
        unsigned char f,   
        unsigned char g,   
        unsigned char h,   
        unsigned char i,   
        unsigned char j,   
        unsigned char k  );  
  
    Guid(GUID m);  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        Array<unsigned char>^ n );  
```  
  
### <a name="parameters"></a>参数  
 `a`  
 GUID 的前 4 个字节。  
  
 `b`  
 GUID 的下两个字节。  
  
 `c`  
 GUID 的下两个字节。  
  
 `d`  
 GUID 的下一个字节。  
  
 `e`  
 GUID 的下一个字节。  
  
 `f`  
 GUID 的下一个字节。  
  
 `g`  
 GUID 的下一个字节。  
  
 `h`  
 GUID 的下一个字节。  
  
 `i`  
 GUID 的下一个字节。  
  
 `j`  
 GUID 的下一个字节。  
  
 `k`  
 GUID 的下一个字节。  
  
 `m`  
 所定义的 GUID。  
  
 `n`  
 GUID 的其余 8 个字节。  
  

## <a name="operator-equality"></a> Guid::operator = = 运算符
比较两个 guid。  
  
### <a name="syntax"></a>语法  
  
```cpp  
Platform::Guid::operator==  
```  
  
### <a name="return-value"></a>返回值  
 如果两个 guid 相等，则为 true。

## <a name="operator-inequality"></a> Guid::operator ！ = 运算符
比较两个 guid。  
  
### <a name="syntax"></a>语法  
  
```cpp  
Platform::Guid::operator!=  
```  
  
### <a name="return-value"></a>返回值  
 如果两个 guid 是否不相等，则为 true。



## <a name="operator-call"></a> Guid::operator() 运算符
将隐式转换[GUID 结构](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx)platform:: guid 的 GUID。  
  
### <a name="syntax"></a>语法  
  
```cpp  
Platform::Guid operator()  
```  
  
### <a name="return-value"></a>返回值  
 一个 Guid 结构。  
  
  
## <a name="see-also"></a>请参阅  
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)