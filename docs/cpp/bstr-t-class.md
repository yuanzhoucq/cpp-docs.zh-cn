---
title: "_bstr_t 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object, COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ce63f8243bc46d77116dbacdf82f821333cba785
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="bstrt-class"></a>_bstr_t 类
**Microsoft 专用**  
  
 A`_bstr_t`对象所封装[BSTR 数据类型](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228)。 类管理资源分配和释放函数调用通过**SysAllocString**和**SysFreeString**和其他`BSTR`Api 在适当的时候。 `_bstr_t` 类使用引用计数来避免开销过大。  
  
### <a name="construction"></a>构造  
  
|||  
|-|-|  
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|构造 `_bstr_t` 对象。|  
  
### <a name="operations"></a>操作  
  
|||  
|-|-|  
|[分配](../cpp/bstr-t-assign.md)|将 `BSTR` 复制到 `BSTR` 包装的 `_bstr_t` 中。|  
|[附加](../cpp/bstr-t-attach.md)|将 `_bstr_t` 包装器链接到 `BSTR`。|  
|[copy](../cpp/bstr-t-copy.md)|构造封装的 `BSTR` 的副本。|  
|[分离](../cpp/bstr-t-detach.md)|返回 `BSTR` 包装的 `_bstr_t` 并从 `BSTR` 中分离 `_bstr_t`。|  
|[GetAddress](../cpp/bstr-t-getaddress.md)|指向 `BSTR` 包装的 `_bstr_t`。|  
|[GetBSTR](../cpp/bstr-t-getbstr.md)|指向 `BSTR` 包装的 `_bstr_t` 的开头。|  
|[length](../cpp/bstr-t-length.md)|返回 `_bstr_t` 中的字符数。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](../cpp/bstr-t-operator-equal.md)|将新值赋给现有 `_bstr_t` 对象。|  
|[运算符 + =](../cpp/bstr-t-operator-add-equal-plus.md)|将字符附加到 `_bstr_t` 对象的结尾。|  
|[运算符 +](../cpp/bstr-t-operator-add-equal-plus.md)|串联两个字符串。|  
|[运算符 !](../cpp/bstr-t-operator-logical-not.md)|检查是否封装`BSTR`是**NULL**字符串。|  
|[运算符 = =、 ！ =、 \<，>， \<=、 > =](../cpp/bstr-t-relational-operators.md)|比较两个 `_bstr_t` 对象。|  
|[运算符 wchar_t * &#124;char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|提取指向封装的 Unicode 或多字节 `BSTR` 对象的指针。|  
  
**结束 Microsoft 专用**  
  
## <a name="requirements"></a>要求  
 **标头：** comutil.h  
  
 **Lib:**对 comsuppw.lib 或 comsuppwd.lib (请参阅[/zc: wchar_t （wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)有关详细信息)  
  
## <a name="see-also"></a>另请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)
