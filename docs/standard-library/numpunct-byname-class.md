---
title: "numpunct_byname 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xlocnum/std::numpunct_byname
dev_langs: C++
helpviewer_keywords: numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 84f71302d43a983772890611e55c56af9b21e922
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="numpunctbyname-class"></a>numpunct_byname 类
一种派生模板类，用于描述一个对象来充当给定区域设置的 `numpunct` facet，从而对数字和布尔表达式进行格式化和标点设置。  
  
## <a name="syntax"></a>语法  
  
```
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

 };
```  
  
## <a name="remarks"></a>备注  
 其行为由[已命名的](../standard-library/locale-class.md#name)区域设置 `_Locname` 决定。 构造函数通过 [numpunct](../standard-library/numpunct-class.md#numpunct)\<CharType>( `_Refs`) 初始化其基对象。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



