---
title: WeakRef 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef class
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f56b35ffb53da8947982359174784a0dbb3cef85
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012581"
---
# <a name="weakref-class"></a>WeakRef 类
表示只能由 Windows 运行时而不是经典 COM 使用的 *弱引用* 。 弱引用表示可能可访问或可能不可访问的对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
class WeakRef : public ComPtr<IWeakReference>  
```  
  
## <a name="remarks"></a>备注  
 一个**WeakRef**对象维护*强引用*，这是与对象相关联，可以是有效或无效。 调用`As()`或`AsIID()`方法来获取强引用。 如果强引用有效，就可以访问关联的对象。 当强引用无效 (**nullptr**)，关联的对象是不可访问。  
  
 一个**WeakRef**对象通常用于表示由外部线程或应用程序控制其存在性的对象。 例如，构造**WeakRef**中对文件对象的引用的对象。 文件打开时，强引用有效。 但文件关闭时，强引用无效。  
  
 请注意，Windows 10 SDK 中的 [As](../windows/weakref-as-method.md)、 [AsIID](../windows/weakref-asiid-method.md) 和 [CopyTo](../windows/weakref-copyto-method.md) 方法中没有发生行为更改。 以前，在调用任何一种方法后，可以检查的 WeakRef 的**nullptr**以确定是否强引用已成功获得，如以下代码所示：  
  
```cpp  
WeakRef wr;  
strongComptrRef.AsWeak(&wr);  
  
// Now suppose that the object strongComPtrRef points to no longer exists  
// and the following code tries to get a strong ref from the weak ref:  
ComPtr<ISomeInterface> strongRef;  
HRESULT hr = wr.As(&strongRef);  
  
// This check won't work with the Windows 10 SDK version of the library.  
// Check the input pointer instead.  
if(wr == nullptr)  
{  
    wprintf(L"Couldn’t get strong ref!");  
}  
```  
  
 使用 Windows 10 SDK（或更高版本）时以上代码无效。 相反，应检查传入的指针**nullptr**。  
  
```cpp  
if (strongRef == nullptr)  
{  
    wprintf(L"Couldn't get strong ref!");  
}  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[WeakRef::WeakRef 构造函数](../windows/weakref-weakref-constructor.md)|初始化的新实例**WeakRef**类。|  
|[WeakRef::~WeakRef 析构函数](../windows/weakref-tilde-weakref-destructor.md)|取消初始化的当前实例**WeakRef**类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[WeakRef::As 方法](../windows/weakref-as-method.md)|设置指定`ComPtr`指针参数以表示指定的接口。|  
|[WeakRef::AsIID 方法](../windows/weakref-asiid-method.md)|设置指定`ComPtr`指针参数以表示指定的接口 id。|  
|[WeakRef::CopyTo 方法](../windows/weakref-copyto-method.md)|如果可用，请为指定的指针变量分配一个指向接口的指针。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[WeakRef::operator& 运算符](../windows/weakref-operator-ampersand-operator.md)|返回`ComPtrRef`对象，表示当前**WeakRef**对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ComPtr`  
  
 `WeakRef`  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)