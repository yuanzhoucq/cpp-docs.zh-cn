---
title: "类工厂和许可 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories, and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3d045736f9a54d344c67e3f7408198e65a0bc95f
ms.openlocfilehash: 17a99edadeb7a5bd923126bce7fbef50313e1867
ms.lasthandoff: 03/29/2017

---
# <a name="class-factories-and-licensing"></a>类工厂和许可
为了创建 OLE 控件的实例，容器应用程序调用了控件的类工厂的成员函数。 由于控件是实际 OLE 对象，类工厂将负责创建控件的实例。 每个 OLE 控件类必须有一个类工厂。  
  
 OLE 控件的另一个重要功能是强制使用许可证。 ControlWizard 可让您在控件项目的创建过程中包含授权。 有关控件授权的详细信息，请参阅文章[ActiveX 控件︰ 许可 ActiveX 控件](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)。  
  
 下表列出了用于声明和实现控件的类工厂以及为控件授权的几个宏和函数。  
  
### <a name="class-factories-and-licensing"></a>类工厂和许可  
  
|||  
|-|-|  
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|声明 OLE 控件或属性页的类工厂。|  
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|实现控件的 `GetClassID` 函数并声明类工厂的实例。|  
|[BEGIN_OLEFACTORY](#begin_olefactory)|开始任何授权函数的声明。|  
|[END_OLEFACTORY](#end_olefactory)|结束任何授权函数的声明。|  
|[AfxVerifyLicFile](#afxverifylicfile)|确认控件是否已获得在特定计算机上使用的授权。|  
  
##  <a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX  
 声明类工厂和`GetClassID`控件类的成员函数。  
  
```   
DECLARE_OLECREATE_EX(class_name)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 控件类的名称。  
  
### <a name="remarks"></a>备注  
 在控件类标头文件中的控件，不支持授权使用此宏。  
  
 请注意此宏提供下面的代码示例相同的目的︰  
  
 [!code-cpp[NVC_MFCAxCtl # 14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]  
  
### <a name="requirements"></a>要求  
  **标头**afxctl.h  
  
##  <a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX  
 实现控件的类工厂和[GetClassID](../../mfc/reference/colecontrol-class.md#getclassid)控件类的成员函数。  
  
```   
IMPLEMENT_OLECREATE_EX(
   class_name,   
    external_name,    
    l,   
    w1,   
    w2,   
    b1,   
    b2,   
    b3,   
    b4,   
    b5,   
    b6,   
    b7,
    b8)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 控件属性页类的名称。  
  
 *external_name*  
 向应用程序公开的对象名称。  
  
 *l、 w1、 w2、 b1、 b2、 b3、 b4、 b5、 b6、 b7、 b8*  
 类的组件**CLSID**。 有关这些参数的详细信息，请参阅备注[IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)。  
  
### <a name="remarks"></a>备注  
 此宏必须出现在任何使用的控件类的实现文件`DECLARE_OLECREATE_EX`宏或`BEGIN_OLEFACTORY`和`END_OLEFACTORY`宏。 外部名称是向其他应用程序公开 OLE 控件的标识符。 容器使用此名称请求此控件类的对象。  
  
### <a name="requirements"></a>要求  
  **标头**afxctl.h  
  
##  <a name="begin_olefactory"></a>BEGIN_OLEFACTORY  
 开始你的控件类的标头文件中类工厂的声明。  
  
``` 
BEGIN_OLEFACTORY(class_name)  
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 指定的控件类这是其类工厂的名称。  
  
### <a name="remarks"></a>备注  
 声明的授权函数的类工厂应开始后立即`BEGIN_OLEFACTORY`。  
  
### <a name="requirements"></a>要求  
  **标头**afxctl.h  
  
##  <a name="end_olefactory"></a>END_OLEFACTORY  
 结束控件的类工厂的声明。  
  
```  
END_OLEFACTORY(class_name)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 这是其类工厂的控件类名称。  
  
### <a name="requirements"></a>要求  
  **标头**afxctl.h  
  
##  <a name="afxverifylicfile"></a>AfxVerifyLicFile  
 调用此函数可验证通过名为的许可证文件`pszLicFileName`对 OLE 控件有效。  
  
```   
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,  
    LPCTSTR  pszLicFileName,  
    LPOLESTR  pszLicFileContents,  
    UINT cch = -1); 
```  
  
### <a name="parameters"></a>参数  
 `hInstance`  
 与授权控件关联的 DLL 的实例句柄。  
  
 `pszLicFileName`  
 指向以 null 结尾的字符串包含许可证文件名。  
  
 `pszLicFileContents`  
 指向一个字节序列，其中必须与许可证文件的开头处的顺序匹配。  
  
 `cch`  
 中的字符数`pszLicFileContents`。  
  
### <a name="return-value"></a>返回值  
 如果许可证文件存在且开始中的字符序列则不为`pszLicFileContents`; 否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`cch`为-1，此函数使用︰  
  
 [!code-cpp[NVC_MFC_Utilities # 36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]  

### <a name="requirements"></a>要求  
  **标头**afxctl.h  

## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

