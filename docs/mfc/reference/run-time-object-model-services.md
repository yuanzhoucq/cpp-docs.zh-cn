---
title: "运行时对象模型服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 986657681dabf1136b072f65b2df76b63f216504
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="run-time-object-model-services"></a>运行时对象模型服务
类[CObject](../../mfc/reference/cobject-class.md)和[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)封装多个对象服务，包括对运行时类信息、 序列化和动态对象创建的访问。 所有派生自 `CObject` 的类都继承此功能。  
  
 能够访问运行时类信息可让您在运行时确定有关对象的类的信息。 当需要对函数自变量进行额外的类型检查以及必须基于对象的类编写专用代码时很有用，能够在运行时确定对象的类很有用。 C++ 语言不直接支持运行时类信息。  
  
 序列化是在文件中写入或读取对象内容的过程。 当应用程序退出后，可以使用序列化来存储对象的内容。 对象随后可在应用程序重新启动时从文件中读取。 此类数据对象被称为“永久对象”。  
  
 动态对象创建支持在运行时创建指定类的对象。 例如，文档、视图和框架对象必须支持动态创建，因为框架需要以动态方式创建这些内容。  
  
 下表列出了支持运行时类信息、序列化和动态创建的 MFC 宏。  
  
 有关这些运行时对象服务和序列化的详细信息，请参阅文章[CObject 类： 访问运行时类信息](../../mfc/accessing-run-time-class-information.md)。  
  
### <a name="run-time-object-model-services-macros"></a>运行时对象模型服务宏  
  


|||  
|-|-|  
|[DECLARE_DYNAMIC](#declare_dynamic)|支持访问运行时类信息（必须在类声明中使用）。|  
|[DECLARE_DYNCREATE](#declare_dyncreate)|支持动态创建和访问运行时类信息（必须在类声明中使用）。|  
|[DECLARE_SERIAL](#declare_serial)|支持序列化和访问运行时类信息（必须在类声明中使用）。|  
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|支持访问运行时类信息（必须在类实现中使用）。|  
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|支持动态创建和访问运行时类信息（必须在类实现中使用）。|  
|[IMPLEMENT_SERIAL](#implement_serial)|允许序列化和访问运行时类信息（必须在类实现中使用）。|  
|[RUNTIME_CLASS](#runtime_class)|返回与命名类对应的 `CRuntimeClass` 结构。|  


 OLE 通常要求在运行时动态创建对象。 例如，OLE 服务器应用程序必须能够动态创建 OLE 项以响应来自客户端的请求。 同样，自动化服务器必须能够创建项以响应来自自动化客户端的请求。  
  
 Microsoft 基础类库提供了两个特定于 OLE 的宏。  
  
### <a name="dynamic-creation-of-ole-objects"></a>OLE 对象的动态创建  

 






|||  
|-|-|  
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|确定公共控件库是否实现了指定的 API。|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|确定公共控件库是否实现了指定的 API。|
|[DECLARE_OLECREATE](#declare_olecreate)|支持通过 OLE 自动化创建对象。|  
|[DECLARE_OLECTLTYPE](#declare_olectltype)|声明**GetUserTypeNameID**和`GetMiscStatus`控件类的成员函数。|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|声明 OLE 控件提供的属性页以显示其属性的列表。|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|支持由 OLE 系统创建对象。|  
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|实现**GetUserTypeNameID**和`GetMiscStatus`控件类的成员函数。|  
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|任一此宏或[IMPLEMENT_OLECREATE](#implement_olecreate)必须出现在使用任何类的实现文件`DECLARE_OLECREATE`。 |

## <a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS
确定公共控件库是否实现了指定的 API。  
   
### <a name="syntax"></a>语法  
  ```  
AFX_COMCTL32_IF_EXISTS(  proc );  
```
### <a name="parameters"></a>参数  
 `proc`  
 指向包含函数名的以 null 结尾的字符串的指针，或者指定函数的序号值。 如果此参数是序号值，则它必须在低序位字中；高序位字必须为零。 此参数必须采用 Unicode。  
   
### <a name="remarks"></a>备注  
 使用此宏来确定是否公共控件库函数指定`proc`(而不是调用[GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212)。  
   
### <a name="requirements"></a>惠?  
 afxcomctl32.h，afxcomctl32.inl  
   
### <a name="see-also"></a>请参阅  
 [隔离 MFC 公共控件库](../isolation-of-the-mfc-common-controls-library.md) [AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)
 
## <a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2
确定公共控件库是否实现指定的 API (这是 Unicode 版的[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists))。  
   
### <a name="syntax"></a>语法    
```  
AFX_COMCTL32_IF_EXISTS2( proc );  
```
### <a name="parameters"></a>参数  
 `proc`  
 指向包含函数名的以 null 结尾的字符串的指针，或者指定函数的序号值。 如果此参数是序号值，则它必须在低序位字中；高序位字必须为零。 此参数必须采用 Unicode。  
   
### <a name="remarks"></a>备注  
 使用此宏来确定是否公共控件库函数指定`proc`(而不是调用[GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212)。 此宏是 Unicode 版本的`AFX_COMCTL32_IF_EXISTS`。  
   
### <a name="requirements"></a>惠?  
 afxcomctl32.h，afxcomctl32.inl  
   
### <a name="see-also"></a>请参阅  
 [隔离 MFC 公共控件库](../isolation-of-the-mfc-common-controls-library.md) [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)



##  <a name="declare_dynamic"></a>DECLARE_DYNAMIC  
 添加了派生类时访问的对象类的运行时信息的功能`CObject`。  
  
```
DECLARE_DYNAMIC(class_name) 
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
### <a name="remarks"></a>备注  
 添加`DECLARE_DYNAMIC`宏为的标头 (.h) 模块的类，然后将该模块包含在需要访问此类的对象的所有.cpp 模块。  
  
 如果你使用**DECLARE**_**动态**和`IMPLEMENT_DYNAMIC`宏所述，你可以然后使用`RUNTIME_CLASS`宏和`CObject::IsKindOf`函数来确定你在运行的对象的类时间。  
  
 如果`DECLARE_DYNAMIC`包含在类声明中，然后`IMPLEMENT_DYNAMIC`必须包含在类实现。  
  
 有关详细信息`DECLARE_DYNAMIC`宏，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 请参阅示例[IMPLEMENT_DYNAMIC](#implement_dynamic)。  

### <a name="requirements"></a>惠?  
 **标头：** afx.h 

##  <a name="declare_dyncreate"></a>DECLARE_DYNCREATE  
 支持的对象`CObject`-派生类，以在运行时动态创建。  
  
```
DECLARE_DYNCREATE(class_name)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
### <a name="remarks"></a>备注  
 框架将使用此功能动态创建新对象。 例如，新创建的视图时打开一个新文档。 文档、 视图和框架类应支持动态创建，因为框架需要以动态方式创建它们。  
  
 添加`DECLARE_DYNCREATE`类，.h 模块中的宏然后将该模块包含在需要访问此类的对象的所有.cpp 模块。  
  
 如果`DECLARE_DYNCREATE`包含在类声明中，然后`IMPLEMENT_DYNCREATE`必须包含在类实现。  
  
 有关详细信息`DECLARE_DYNCREATE`宏，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
> [!NOTE]
>  `DECLARE_DYNCREATE`宏包含的所有功能`DECLARE_DYNAMIC`。  
  
### <a name="example"></a>示例  
 请参阅示例[IMPLEMENT_DYNCREATE](#implement_dyncreate)。  

### <a name="requirements"></a>惠?  
 **标头：** afx.h 

 
## <a name="declareolectltype"></a>DECLARE_OLECTLTYPE
声明**GetUserTypeNameID**和`GetMiscStatus`控件类的成员函数。  
   
### <a name="syntax"></a>语法    
```
DECLARE_OLECTLTYPE( class_name )  
```
### <a name="parameters"></a>参数  
 *class_name*  
 控件类的名称。  
   
### <a name="remarks"></a>备注  
 **GetUserTypeNameID**和`GetMiscStatus`是纯虚函数，在中声明`COleControl`。 因为这些函数是纯虚拟的它们必须被重写控件类中。 除了**DECLARE_OLECTLTYPE**，必须添加`IMPLEMENT_OLECTLTYPE`向控件类声明的宏。  
   
### <a name="requirements"></a>惠?  
 **标头：** afxctl.h  
   
### <a name="see-also"></a>请参阅  
 [IMPLEMENT_OLECTLTYPE](#implement_olectltype)
 

## <a name="declareproppageids"></a>DECLARE_PROPPAGEIDS
声明 OLE 控件提供的属性页以显示其属性的列表。  
   
### <a name="syntax"></a>语法    
```
DECLARE_PROPPAGEIDS( class_name )  
```
### <a name="parameters"></a>参数  
 *class_name*  
 拥有属性页的控件类名称。  
   
### <a name="remarks"></a>备注  
 使用`DECLARE_PROPPAGEIDS`宏在类声明的末尾。 然后，在定义类的成员函数的.cpp 文件，使用`BEGIN_PROPPAGEIDS`宏，为每个控件的属性页中，宏项和`END_PROPPAGEIDS`宏声明属性页列表的末尾。  
  
 属性页的详细信息，请参阅文章[ActiveX 控件： 属性页](../mfc-activex-controls-property-pages.md)。  
   
### <a name="requirements"></a>惠?  
 **标头：** afxctl.h  
   
### <a name="see-also"></a>请参阅   
 [BEGIN_PROPPAGEIDS](#begin_proppageids)   
 [END_PROPPAGEIDS](#end_proppageids)

##  <a name="declare_serial"></a>DECLARE_SERIAL  
 生成必需的 c + + 标头代码`CObject`-派生可序列化的类。  
  
```
DECLARE_SERIAL(class_name)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
### <a name="remarks"></a>备注  
 序列化是从文件写入或读取与对象的内容的过程。  
  
 使用`DECLARE_SERIAL`宏在.h 模块中，然后将该模块包含需要访问此类的对象的所有.cpp 模块中。  
  
 如果`DECLARE_SERIAL`包含在类声明中，然后`IMPLEMENT_SERIAL`必须包含在类实现。  
  
 `DECLARE_SERIAL`宏包含的所有功能`DECLARE_DYNAMIC`和`DECLARE_DYNCREATE`。  
  
 你可以使用**AFX_API**宏来自动导出`CArchive`提取运算符的类使用`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`宏。 尖括号 （位于.h 文件中） 替换为以下代码的类声明：  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 有关详细信息`DECLARE_SERIAL`宏，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]  
  
### <a name="requirements"></a>惠?  
 **标头：** afx.h 

##  <a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC  
 生成为动态所需的 c + + 代码`CObject`-派生的类名称和层次结构中的位置与运行时访问的类。  
  
```
IMPLEMENT_DYNAMIC(class_name, base_class_name)  
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
 `base_class_name`  
 基本类的名称。  
  
### <a name="remarks"></a>备注  
 使用`IMPLEMENT_DYNAMIC`.cpp 模块，然后链接生成的对象一次代码中的宏。  
  
 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]  

### <a name="requirements"></a>惠?  
 **标头：** afx.h 

##  <a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE  
 支持的对象`CObject`-派生类，以在运行，都会动态创建时间一起使用时`DECLARE_DYNCREATE`宏。  
  
```
IMPLEMENT_DYNCREATE(class_name, base_class_name)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
 `base_class_name`  
 基本类的实际名称。  
  
### <a name="remarks"></a>备注  
 框架将使用此功能时，创建新对象动态，例如，在序列化过程从磁盘读取对象。 添加`IMPLEMENT_DYNCREATE`类实现文件中的宏。 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
 如果你使用`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`宏，你可以然后使用`RUNTIME_CLASS`宏和`CObject::IsKindOf`成员函数以在运行时确定对象的类。  
  
 如果`DECLARE_DYNCREATE`包含在类声明中，然后`IMPLEMENT_DYNCREATE`必须包含在类实现。  
  
 请注意，此宏定义将调用你的类的默认构造函数。 如果由类显式实现非普通构造函数，它必须还可以显式实现默认构造函数。 默认构造函数可以添加到类的**私有**或**保护**以防止它被调用从外部类实现的成员部分。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]  

### <a name="requirements"></a>惠?  
 **标头：** afx.h 

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS
任一此宏或[IMPLEMENT_OLECREATE](#implement_olecreate)必须出现在使用任何类的实现文件`DECLARE_OLECREATE`。  
   
### <a name="syntax"></a>语法    
```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags, 
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
  
```
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
 *external_name*  
 向其他应用程序 （用引号引起来） 公开的对象名称。  
  
 `nFlags`  
 包含一个或多个以下的标志：  
  
-   `afxRegInsertable`允许在 OLE 对象的插入对象对话框中显示控件。    
-   `afxRegApartmentThreading`ThreadingModel 到注册表中设置线程模型 = 单元。    
-   **afxRegFreeThreading** ThreadingModel 到注册表中设置线程模型 = 免费。  
  
     你可以组合两个标志`afxRegApartmentThreading`和`afxRegFreeThreading`设置 ThreadingModel = Both。 请参阅[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)线程处理模型注册的详细信息的 Windows SDK 中。    
 *l*， *w1*， *w2*， *b1*， *b2*， *b3*， *b4*， *b5*， *b6*， *b7*， *b8*  
 类的组件**CLSID**。  
   
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  如果你使用`IMPLEMENT_OLECREATE_FLAGS`，你可以指定通过使用支持你的对象的线程模型`nFlags`参数。 如果你想要支持仅单线程模型，使用`IMPLEMENT_OLECREATE`。  
  
 外部名称是公开给其他应用程序的标识符。 客户端应用程序使用的外部名称从自动化服务器请求的此类对象。  
  
 OLE 类 ID 是对象的唯一 128 位标识符。 它由一个**长**、 两个**WORD**和八**字节**s，由表示*l*， *w1*， *w2*，和*b1*通过*b8*语法说明中。 应用程序向导和代码向导根据需要为你创建唯一的 OLE 类 Id。  
   
### <a name="requirements"></a>惠?  
 **标头：** afxdisp.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [DECLARE_OLECREATE](#declare_olecreate)   
 [CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)


## <a name="implement_olecreate"></a>IMPLEMENT_OLECTLTYPE
实现**GetUserTypeNameID**和`GetMiscStatus`控件类的成员函数。  
   
### <a name="syntax"></a>语法    
```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )  
```
### <a name="parameters"></a>参数  
 *class_name*  
 控件类的名称。  
  
 *idsUserTypeName*  
 包含控件的外部名称的字符串资源 ID。  
  
 *dwOleMisc*  
 包含一个或多个标志一个枚举。 此枚举的详细信息，请参阅[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) Windows SDK 中。  
   
### <a name="remarks"></a>备注  
 除了`IMPLEMENT_OLECTLTYPE`，必须添加**DECLARE_OLECTLTYPE**向控件类声明的宏。  
  
 **GetUserTypeNameID**成员函数将返回标识你的控件类的资源字符串。 `GetMiscStatus`返回**OLEMISC** bits 为您的控件。 此枚举指定设置说明杂项特征的控件的集合。 有关完整说明**OLEMISC**设置，请参阅[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) Windows SDK 中。  
  
> [!NOTE]
>  使用 ActiveX 控件向导的默认设置是： **OLEMISC_ACTIVATEWHENVISIBLE**， **OLEMISC_SETCLIENTSITEFIRST**， **OLEMISC_INSIDEOUT**， **OLEMISC_CANTLINKINSIDE**，和**OLEMISC_RECOMPOSEONRESIZE**。  
   
### <a name="requirements"></a>惠?  
 **标头：** afxctl.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [DECLARE_OLECTLTYPE](#declare_olectltype)

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL  
 生成为动态所需的 c + + 代码`CObject`-派生的类名称和层次结构中的位置与运行时访问的类。  
  
```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)  
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
 `base_class_name`  
 基本类的名称。  
  
 *wSchema*  
 A **UINT** "版本号"将以启用反序列化程序识别并处理所创建的数据的存档编码前面程序版本。 类的架构数字不能为-1。  
  
### <a name="remarks"></a>备注  
 使用`IMPLEMENT_SERIAL`.cpp 模块; 中的宏然后一次将链接生成对象代码。  
  
 你可以使用**AFX_API**宏来自动导出`CArchive`提取运算符的类使用`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`宏。 尖括号 （位于.h 文件中） 替换为以下代码的类声明：  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]  

### <a name="requirements"></a>惠?  
 **标头：** afx.h 

##  <a name="runtime_class"></a>RUNTIME_CLASS  
 从 c + + 类的名称获取运行时类结构。  
  
```
RUNTIME_CLASS(class_name)  
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 （未用引号引起来） 类的实际名称。  
  
### <a name="remarks"></a>备注  
 `RUNTIME_CLASS`返回一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)指定的类结构*class_name*。 仅`CObject`-派生类使用声明`DECLARE_DYNAMIC`， `DECLARE_DYNCREATE`，或`DECLARE_SERIAL`将返回指向`CRuntimeClass`结构。  
  
 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]  

### <a name="requirements"></a>惠?  
 **标头：** afx.h 
   
##  <a name="declare_olecreate"></a>DECLARE_OLECREATE  
 支持的对象`CCmdTarget`-派生类，以通过 OLE 自动化创建。  
  
```
DECLARE_OLECREATE(class_name) 
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
### <a name="remarks"></a>备注  
 此宏允许其他 OLE 启用应用程序创建此类型的对象。  
  
 添加`DECLARE_OLECREATE`类，.h 模块中的宏然后将该模块包含需要访问此类的对象的所有.cpp 模块中。  
  
 如果`DECLARE_OLECREATE`包含在类声明中，然后`IMPLEMENT_OLECREATE`必须包含在类实现。 类声明使用`DECLARE_OLECREATE`还必须使用`DECLARE_DYNCREATE`或`DECLARE_SERIAL`。  

### <a name="requirements"></a>惠?  
 **标头**: afxdisp.h  

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE  
 任一此宏或[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)必须出现在使用任何类的实现文件`DECLARE_OLECREATE`。  
  
```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 类的实际名称。  
  
 *external_name*  
 向其他应用程序 （用引号引起来） 公开的对象名称。  
  
 *l*， *w1*， *w2*， *b1*， *b2*， *b3*， *b4*， *b5*， *b6*， *b7*， *b8*  
 类的组件**CLSID**。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  如果你使用`IMPLEMENT_OLECREATE`，默认情况下，支持的单个线程处理模型。 如果你使用`IMPLEMENT_OLECREATE_FLAGS`，你可以指定通过使用支持你的对象的线程模型`nFlags`参数。  
  
 外部名称是公开给其他应用程序的标识符。 客户端应用程序使用的外部名称从自动化服务器请求的此类对象。  
  
 OLE 类 ID 是对象的唯一 128 位标识符。 它由一个**长**、 两个**WORD**和八**字节**s，由表示*l*， *w1*， *w2*，和*b1*通过*b8*语法说明中。 应用程序向导和代码向导根据需要为你创建唯一的 OLE 类 Id。  

### <a name="requirements"></a>惠?  
 **标头**: afxdisp.h 

## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

