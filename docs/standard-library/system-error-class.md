---
title: "system_error 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "system_error/std::system_error"
  - "std.system_error"
  - "std::system_error"
  - "system_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "system_error 类"
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# system_error 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示引发以报告低级系统错误的所有异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class system_error : public runtime_error {  
public:  
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

 };  
```  
  
## <a name="remarks"></a>备注  
 返回的值 `what` 类中 [异常](../standard-library/exception-class1.md) 从构造 `_Message` 和类型的存储的对象 [error_code](../standard-library/error-code-class.md) (或者 `code` 或 `error_code(_Errval, _Errcat)`)。  
  
 成员函数 `code` 返回存储 [error_code](../standard-library/error-code-class.md) 对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** \< system_error >  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
 [\< system_error >](../standard-library/system-error.md)

