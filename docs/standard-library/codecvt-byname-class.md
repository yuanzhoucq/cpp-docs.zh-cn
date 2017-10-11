---
title: "codecvt_byname 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocale/std::codecvt_byname
dev_langs:
- C++
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 0015721962278a9b4105fb3106ccc244f833becd
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="codecvtbyname-class"></a>codecvt_byname 类
一种派生模板类，用于描述一个对象来充当给定区域设置的排序规则 facet，从而检索与转换有关的文化区域特定信息。  
  
## <a name="syntax"></a>语法  
  
```
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```  
  
```
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```  
  
```
protected:
    virtual ~codecvt_byname();

};
```  
  
#### <a name="parameters"></a>参数  
 `_Locname`  
 已命名的区域设置。  
  
 `_Refs`  
 初始引用计数。  
  
## <a name="remarks"></a>备注  
 构造已命名的区域设置时，将自动创建 Byname facet。  
  
 其行为由命名的区域设置 `_Locname` 决定。 每个构造函数使用 [codecvt](../standard-library/codecvt-class.md)\<CharType, Byte, StateType>( `_Refs`) 初始化其基对象。  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




