[TOC]

# XML处理

## 相关链接

[lxml的使用入门](https://www.cnblogs.com/zhangxinqi/p/9210211.html)

## 简介

> python的一个解析库，支持HTML和XML的解析，支持XPath解析方式，而且解析效率非常高

### XPath

XPath，全称XML Path Language，即XML路径语言，它是一门在XML文档中查找信息的语言，它最初是用来搜寻XML文档的，但是它同样适用于HTML文档的搜索

XPath的选择功能十分强大，它提供了非常简明的路径选择表达式，另外，它还提供了超过100个内建函数，用于字符串、数值、时间的匹配以及节点、序列的处理等，几乎所有我们想要定位的节点，都可以用XPath来选择

XPath于1999年11月16日成为W3C标准，它被设计为供XSLT、XPointer以及其他XML解析软件使用

#### xpath 的规则

| 表达式            | 描述                                         |
| ----------------- | -------------------------------------------- |
| nodename          | 选取此节点的所有节点                         |
| /                 | 从当前节点选取直接子节点                     |
| //                | 从当前节点选取子孙节点                       |
| .                 | 选取当前节点                                 |
| ..                | 选取当前节点的父节点                         |
| @                 | 选取属性                                     |
| *                 | 通配符，选择所有元素节点和元素名             |
| @*                | 选取所有属性                                 |
| [@attrib]         | 选取给定属性的所有元素                       |
| [@attrib='value'] | 选取给定属性给定值的所有元素                 |
| [tag]             | 选取所有具有指定元素的直接子节点             |
| [tag='text']      | 选取所有具有指定元素并且文本内容是text的节点 |



## 使用

### 1. 解析

```python
fromstring():解析字符串
HTML():解析HTML对象
XML():解析XML对象
parse():解析文件类型对象
```

### 2. 打印

```python
etree.tostring(root)
```

### 3. 搜索

```
find():返回第一个匹配对象，并且xpath语法只能使用相对路径（以’.//’开头）；
findall():返回一个标签对象的列表，并且xpath语法只能使用相对路径（以’.//’开头）；
xpath()：返回一个标签对象的列表，并且xpath语法的相对路径和绝对路径。
```

### 保存

```python
xml_Stations = ET.Element('StationInfo')
for x in G.nodes:
    xml_Stations.append(rootLoc.find('./station[@name="%s"]'%x))
tree = ET.ElementTree(xml_Stations)
tree.write('output.xml', pretty_print=True, xml_declaration=True,   encoding="utf-8")
```

