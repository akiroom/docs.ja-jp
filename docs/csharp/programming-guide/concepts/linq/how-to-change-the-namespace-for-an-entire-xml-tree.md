---
title: '方法: XML ツリー全体の名前空間を変更する (C#)'
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: d046e01798c193ee0ea459f522a5c29187c697d7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487451"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a>方法: XML ツリー全体の名前空間を変更する (C#)
要素または属性の名前空間をプログラムで変更しなければならない場合があります。 LINQ to XML では、この操作を簡単に行うことができます。 <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> プロパティを設定できます。 <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> プロパティは設定できませんが、簡単に属性を <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> にコピーし、既存の属性を削除して、目的の新しい名前空間に含まれる新しい属性を追加できます。  
  
 詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコードは、名前空間に含まれない 2 つの XML ツリーを作成します。 次に、各ツリーの名前空間を変更して、1 つのツリーに結合します。  
  
```csharp  
XElement tree1 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XElement tree2 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace ad = "http://www.adatum.com";  
// change the namespace of every element and attribute in the first tree  
foreach (XElement el in tree1.DescendantsAndSelf())  
{  
    el.Name = aw.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));  
}  
// change the namespace of every element and attribute in the second tree  
foreach (XElement el in tree2.DescendantsAndSelf())  
{  
    el.Name = ad.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));  
}  
// add attribute namespaces so that the tree will be serialized with  
// the aw and ad namespace prefixes  
tree1.Add(  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")  
);  
tree2.Add(  
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")  
);  
// create a new composite tree  
XElement root = new XElement("Root",  
    tree1,  
    tree2  
);  
Console.WriteLine(root);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
