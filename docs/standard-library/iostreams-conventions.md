---
title: "iostreams 约定 | Microsoft Docs"
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
  - "iostream 标头"
  - "标准 C++ 库, iostreams"
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# iostreams 约定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

iostreams 标头支持在文本和编码形式之间和的转换输入和输出。外部文件：  
  
|||  
|-|-|  
|[\<fstream\>](../standard-library/fstream.md)|[\< \> iomanip](../standard-library/iomanip.md)|  
|[\<ios\>](../standard-library/ios.md)|[\<iosfwd\>](../standard-library/iosfwd.md)|  
|[\<iostream\>](../standard-library/iostream.md)|[\< \> istream](../standard-library/istream.md)|  
|[\<ostream\>](../standard-library/ostream.md)|[\<sstream\>](../standard-library/sstream.md)|  
|[\< \> streambuf](../standard-library/streambuf.md)|[\<strstream\>](../standard-library/strstream.md)|  
  
 使用 iostreams 的最为简单的使用还要求只包含标头 [\<iostream\>](../standard-library/iostream.md)。  然后可以从 [cin](../Topic/cin.md)[wcin](../Topic/wcin.md) 读取的值或标准输入。  执行的规则。类 [basic\_istream 类](../standard-library/basic-istream-class.md)的阐释概述。  您还可以插入值为或 [cout](../Topic/cout.md)[wcout](../Topic/wcout.md) 写入标准输出。  执行的规则。类 [basic\_ostream 类](../standard-library/basic-ostream-class.md)的阐释概述。  格式控件共有两提取器和 insertors 由类管理。[basic\_ios 类](../standard-library/basic-ios-class.md) 操作装扮提取并粘贴此对象的格式信息是若干默认操控器。  
  
 您可以对要打开的文件的名称相同 iostreams 操作，使用声明中的 [\<fstream\>](../standard-library/fstream.md)。  若要转换类之间 [basic\_string 类](../standard-library/basic-string-class.md)iostreams 和对象，使用声明中的 [\<sstream\>](../standard-library/sstream.md)。  若要执行与 C\# 字符串，使用声明中的 [\<strstream\>](../standard-library/strstream.md)。  
  
 剩余的标题。iostreams 类的最高级用户只有提供支持服务，功能直接相关。  
  
## 请参阅  
 [STL 概述](../standard-library/cpp-standard-library-overview.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)