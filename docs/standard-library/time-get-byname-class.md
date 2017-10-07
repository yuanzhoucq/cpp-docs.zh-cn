---
title: "time_get_byname 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xloctime/std::time_get_byname
dev_langs:
- C++
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: b46b1b88b623c1f1bec315ef2bd488ae3675d0b0
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="timegetbyname-class"></a>time_get_byname 类
一种派生模板类，用于描述一个可充当类型 `time_get`\< CharType、InputIterator > 的区域设置 facet 的对象。  
  
## <a name="syntax"></a>语法  
  
```
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```  
  
#### <a name="parameters"></a>参数  
 `_Locname`  
 已命名的区域设置。  
  
 `_Refs`  
 初始引用计数。  
  
## <a name="requirements"></a>要求  
 其行为由已命名的区域设置 `_Locname` 决定。 每个构造函数都使用 [time_get](../standard-library/time-get-class.md#time_get)\<CharType、InputIterator>( `_Refs`) 初始化其基对象。  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




