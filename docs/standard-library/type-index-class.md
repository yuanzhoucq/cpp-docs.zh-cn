---
title: type_index 类
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: 8807a041ab1c6ef47a9c3c12dac2688f121f6cfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278953"
---
# <a name="typeindex-class"></a>type_index 类

`type_index` 类将指针包装到 [type_info 类](../cpp/type-info-class.md)，以便通过这些对象辅助编写索引。

class type_index { public: type_index(const type_info& tinfo); const char *name() const; size_t hash_code() const; bool operator==(const type_info& right) const; bool operator!=(const type_info& right) const; bool operator<(const type_info& right) const; bool operator\<=(const type_info& right) const; bool operator>(const type_info& right) const; bool operator>=(const type_info& right) const; };

构造函数将 `ptr` 初始化为 `&tinfo`。

`name` 返回 `ptr->name()`。

`hash_code` 返回 `ptr->hash_code().`

`operator==` 返回 `*ptr == right.ptr`。

`operator!=` 返回 `!(*this == right)`。

`operator<` 返回 `*ptr->before(*right.ptr)`。

`operator<=` 返回 `!(right < *this).`

`operator>` 返回 `right < *this`。

`operator>=` 返回 `!(*this < right)`。

## <a name="see-also"></a>请参阅

[运行时类型信息](../cpp/run-time-type-information.md)<br/>
[\<typeindex>](../standard-library/typeindex.md)<br/>
