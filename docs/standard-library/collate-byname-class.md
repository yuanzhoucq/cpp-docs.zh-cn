---
title: "collate_byname 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::collate_byname"
  - "locale/std::collate_byname"
  - "std.collate_byname"
  - "collate_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collate_byname 类"
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# collate_byname 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种派生模板类，用于描述一个对象来充当给定区域设置的排序规则 facet，从而检索与字符串排序约定有关的文化区域特定信息。  
  
## <a name="syntax"></a>语法  
  
```
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```  
  
#### <a name="parameters"></a>参数  
 `_Locname`  
 命名的区域设置。  
  
 `_Refs`  
 初始引用计数。  
  
## <a name="remarks"></a>备注  
 此模板类描述一个对象来充当 [区域设置 facet](../standard-library/locale-class.md#facet_class) 类型的 [collate](../standard-library/collate-class.md#collate__collate)\< CharType>。 其行为由 [名为](../standard-library/locale-class.md#locale__name) 区域设置 `_Locname`。 每个构造函数初始化与与其基对象 [collate](../standard-library/collate-class.md#collate__collate)\< CharType>( `_Refs`)。  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 区域设置>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



