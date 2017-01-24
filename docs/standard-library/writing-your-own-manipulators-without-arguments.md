---
title: "自行编写无参数的操控器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "操控器"
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 自行编写无参数的操控器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不使用参数编写器不需要类对复杂派生和宏的使用。  假定打印机需要对 \<、\>\[粗体输入模式。  可以插入此对直接到流：  
  
```  
cout << "regular " << '\033' << '[' << "boldface" << endl;  
```  
  
 也可以定义一个 `bold` 移动，插入字符：  
  
```  
ostream& bold( ostream& os ) {  
    return os << '\033' << '[';  
}  
cout << "regular " << bold << "boldface" << endl;  
```  
  
 以全局方式定义的 `bold` 函数采用 `ostream` 引用参数并返回 `ostream` 引用。  因为它不需要对任何私有类的元素，访问不是成员函数或是友元。  `bold` 函数连接流，因为流的 `<<` 运算符重载接受此类函数，使用类似下面的声明：  
  
```  
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))  
{     
   // call ios_base manipulator  
   (*_Pfn)(*(ios_base *)this);  
   return (*this);  
}  
```  
  
 您可以使用该功能扩展其他重载运算符。  在这种情况下，是意外发生的 `bold`、字符到流中。  函数不一定会调用它，而当插入流时，在连续字符打印时。  因此，存在缓冲的流，可以打印延迟。  
  
## 请参阅  
 [输出流](../standard-library/output-streams.md)