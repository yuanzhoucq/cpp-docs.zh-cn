---
title: type_index 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- typeindex/std::type_index
dev_langs:
- C++
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86058cd8deb0ddd9458c8882bb31029d365cb110
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
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
