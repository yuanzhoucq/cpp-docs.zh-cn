---
title: "CA2CAEX 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CA2CAEX"
  - "ATL.CA2CAEX<t_nBufferLength>"
  - "ATLCONV/CA2CAEX"
  - "ATL::CA2CAEX<t_nBufferLength>"
  - "ATL::CA2CAEX"
  - "CA2CAEX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CA2CAEX 类"
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CA2CAEX 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字符串翻译宏 `CA2CTEX` 和 `CT2CAEX`和typedef使用此选件类 **CA2CA**。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CA2CAEX  
```  
  
#### 参数  
 `t_nBufferLength`  
 用于的缓冲区的大小将过程。  默认长度为128个字节。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CA2CAEX::CA2CAEX](../Topic/CA2CAEX::CA2CAEX.md)|构造函数。|  
|[CA2CAEX::~CA2CAEX](../Topic/CA2CAEX::~CA2CAEX.md)|该析构函数。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CA2CAEX::operator LPCSTR](../Topic/CA2CAEX::operator%20LPCSTR.md)|转换运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CA2CAEX::m\_psz](../Topic/CA2CAEX::m_psz.md)|存储源字符串的数据成员。|  
  
## 备注  
 除非需要额外功能，使用 `CA2CTEX`，`CT2CAEX`或 **CA2CA** 在代码。  
  
 此选件类是安全使用在循环并不会溢出堆栈。  默认情况下，ATL转换选件类和宏来转换会使用当前线程的ANSI代码页。  
  
 下面的宏基于此选件类:  
  
-   `CA2CTEX`  
  
-   `CT2CAEX`  
  
 下面的typedef基于此选件类:  
  
-   **CA2CA**  
  
 有关这些讨论的文本翻译宏，请参见 [ATL和MFC字符串翻译宏](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 示例  
 为使用基于这些字符串翻译宏参见 [ATL和MFC字符串翻译宏](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 要求  
 **Header:** atlconv.h  
  
## 请参阅  
 [CA2AEX 类](../../atl/reference/ca2aex-class.md)   
 [CA2WEX 类](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 类](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 类](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 类](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)