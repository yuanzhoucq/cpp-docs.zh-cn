---
title: "_com_ptr_t 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t
dev_langs: C++
helpviewer_keywords: _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9a17309ab08d50be1366b8db71798766b52baa9
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="comptrt-class"></a>_com_ptr_t 类
**Microsoft 专用**  
  
 `_com_ptr_t` 对象封装 COM 接口指针，被称为“智能”指针。 此模板类管理资源分配和释放函数调用通过**IUnknown**成员函数： `QueryInterface`， `AddRef`，和**版本**。  
  
 智能指针通常由提供的 typedef 定义引用**_COM_SMARTPTR_TYPEDEF**宏。 此宏采用接口名称和 IID，并利用接口名称与后缀 `_com_ptr_t` 声明 `Ptr` 的专用化。 例如:  
  
```  
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 声明`_com_ptr_t`专用化**IMyInterfacePtr**。  
  
 一套[函数模板](../cpp/relational-function-templates.md)，不属于此模板类，具有智能指针的比较运算符右侧的支持比较。  
  
### <a name="construction"></a>构造  
  
|||  
|-|-|  
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|构造 `_com_ptr_t` 对象。|  
  
### <a name="low-level-operations"></a>低级别运算  
  
|||  
|-|-|  
|[AddRef](../cpp/com-ptr-t-addref.md)|调用`AddRef`成员函数**IUnknown**封装的接口指针上。|  
|[附加](../cpp/com-ptr-t-attach.md)|封装此智能指针的类型的原始接口指针。|  
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|创建给定的对象的新实例**CLSID**或**ProgID**。|  
|[分离](../cpp/com-ptr-t-detach.md)|提取并返回封装的接口指针。|  
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|将附加到给定的对象的现有实例**CLSID**或**ProgID**。|  
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|返回封装的接口指针。|  
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|调用`QueryInterface`成员函数**IUnknown**封装的接口指针上。|  
|[发布](../cpp/com-ptr-t-release.md)|调用**版本**成员函数**IUnknown**封装的接口指针上。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator =](../cpp/com-ptr-t-operator-equal.md)|将新值赋给现有 `_com_ptr_t` 对象。|  
|[运算符 = =、 ！ =、 \<，>， \<=、 > =](../cpp/com-ptr-t-relational-operators.md)|比较智能指针对象与另一个智能指针、 原始接口指针或**NULL**。|  
|[提取器](../cpp/com-ptr-t-extractors.md)|提取封装的 COM 接口指针。|  
  
**结束 Microsoft 专用**  
  
## <a name="requirements"></a>惠?  
 **标头：** \<comip.h 声明 >  
  
 **Lib:**对 comsuppw.lib 或 comsuppwd.lib (请参阅[/zc: wchar_t （wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)有关详细信息)  
  
## <a name="see-also"></a>请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)