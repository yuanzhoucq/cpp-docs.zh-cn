---
title: "区域设置名称、语言和国家-地区字符串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.strings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "国家/地区字符串"
  - "本地化, 区域设置"
  - "区域设置"
  - "setlocale 函数"
  - "语言字符串"
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 区域设置名称、语言和国家/地区字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`locale` 和 `setlocale` 函数的 `_create_locale` 参数可使用 Windows NLS API 支持的区域设置名称、语言、国家\/地区代码和代码页设置。`locale` 参数采取以下格式：  
  
```  
  
locale :: "locale_name"  
        | "language[_country_region[.code_page]]"  
        | ".code_page"  
        | "C"  
        | ""  
        | NULL  
```  
  
 首选区域设置名称格式，例如英语（美国）对应的 `en-US`，或波斯尼亚语（西里尔文，波斯尼亚和黑塞哥维那）对应的 `bs-Cyrl-BA`。[Locale Names（区域设置名称）](http://msdn.microsoft.com/library/windows/desktop/dd373814.aspx)中介绍了这一系列区域设置名称。 有关 Windows 操作系统版本支持的区域设置名称的列表，请参阅 [National Language Support \(NLS\) API Reference（区域语言支持 \(NLS\) API 参考）](http://msdn.microsoft.com/goglobal/bb896001.aspx)的“区域性名称”列。 该资源列出了支持的语言、脚本和区域设置名称的地区部分。 有关采用非默认排序顺序的受支持的区域设置名称的信息，请参阅 [Sort Order Identifiers（排序顺序标识符）](http://msdn.microsoft.com/library/windows/desktop/dd374060.aspx)中的“区域性名称”列。  
  
 使用语言字符串或语言字符串和国家\/地区字符串创建区域设置时，*language*\[\_*country\_region*\[.*code\_page*\]\] 格式将存储在类别的区域设置中。[语言字符串](../c-runtime-library/language-strings.md)中介绍了一系列受支持的语言字符串，[国家\/地区字符串](../c-runtime-library/country-region-strings.md)中则列出了受支持的国家\/地区字符串。 如果指定的语言与指定的国家\/地区无关联，则将指定国家\/地区的默认语言存储在区域设置中。 我们不建议将区域设置字符串的该格式嵌入到代码中或序列化到存储中，因为操作系统的更新更改这些字符串的可能性要高于区域设置名称格式。  
  
 代码页是与区域设置关联的 ANSI\/OEM 代码页。 通过语言或通过语言和国家\/地区单独指定区域设置时，代码页已为你确定。 特殊值 `.ACP` 将指定国家\/地区的 ANSI 代码页。 特殊值 `.OCP` 将指定国家\/地区的 OEM 代码页。 例如，如果指定 `"Greek_Greece.ACP"` 作为区域设置，区域设置则存储为 `Greek_Greece.1253`（希腊语的 ANSI 代码页）；如果指定 `"Greek_Greece.OCP"` 作为区域设置，它则存储为 `Greek_Greece.737`（希腊语的 OEM 代码页）。 有关代码页的详细信息，请参见[代码页](../c-runtime-library/code-pages.md)。 有关 Windows 支持的代码页列表，请参阅 [Code Page Identifiers（代码页标识符）](http://msdn.microsoft.com/library/windows/desktop/dd317756.aspx)。  
  
 如果你仅使用代码页指定区域设置，则将使用系统默认语言和国家\/地区。 例如，如果指定 `".1254"`（ANSI 土耳其语）作为系统上为英语（美国）配置的区域设置，则存储的区域设置是 `English_United States.1254`。 我们不建议使用该格式，因为它可能导致不一致的行为。  
  
 `locale` 的 `C` 值为 C 转换指定最小的符合 ANSI 标准的环境。`C` 区域设置假定每个 `char` 数据类型为 1 字节，并且其值始终小于 256。 如果 `locale` 指向一个空字符串，则区域设置是实现定义的本机环境。  
  
 使用 `setlocale` 类别，可以为 `_wsetlocale` 和 `LC_ALL` 函数同时指定所有区域设置类别。 这些类别可以全部设置为同一区域设置，你也可以使用具有该格式的区域设置参数分别设置每个类别：  
  
```  
LC_ALL_specifier :: locale  
        | [LC_COLLATE=locale][;LC_CTYPE=locale][;LC_MONETARY=locale][;LC_NUMERIC=locale][;LC_TIME=locale]  
  
```  
  
 你可以指定多个类别类型，由分号分隔。 未指定的类别类型使用当前的区域设置。 例如，该代码将所有类别的当前区域设置设为 `de-DE`，然后将类别 `LC_MONETARY` 设为 `en-GB`，将 `LC_TIME` 设为 `es-ES`：  
  
 `_wsetlocale(LC_ALL, L"de-DE");`  
  
 `_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");`  
  
## 请参阅  
 [C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)   
 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [语言字符串](../c-runtime-library/language-strings.md)   
 [国家\/地区字符串](../c-runtime-library/country-region-strings.md)