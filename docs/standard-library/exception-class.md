---
title: exception 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 713600a72886b713c58c4a449c6f5270a3ccfe9a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="exception-class"></a>exception 类

该类用作某些表达式和 C++ 标准库所引发的所有异常的基类。

## <a name="syntax"></a>语法

```cpp
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };
```

## <a name="remarks"></a>备注

具体来说，此基类是 [\<stdexcept>](../standard-library/stdexcept.md) 中定义的标准异常类的根。 默认构造函数将 `what` 返回的 C 字符串值保留为不指定，但是可以通过某些派生类的构造函数定义为由实现定义的 C 字符串。 无成员函数引发任何异常。

可以通过 `int` 参数指定不应分配任何内存。 将忽略 `int` 的值。

> [!NOTE]
> 构造函数 `exception(const char* const &message)` 和 `exception(const char* const &message, int)` 是 C++ 标准库的 Microsoft 扩展。

## <a name="example"></a>示例

有关从 `exception` 类继承的标准异常类的使用示例，请参阅 [\<stdexcept>](../standard-library/stdexcept.md) 中定义的任意一个类。

## <a name="requirements"></a>要求

**标头：**\<exception>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
