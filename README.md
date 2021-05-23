# 1: TỔNG QUAN VỀ BÀI BÁO CÁO
xin chào các bạn mình tên là tuân là sinh viên ICTU mình tham gia GITHUB năm 2021 các dự án mình làm về Front end 

    if (name==="Tuân"){
      return true
    }
```
HỌ VÀ TÊN: Phan Kim Tuân
Lớp: KTPM;K15A
Địa chỉ: Chung cư Intracom2 cầu diễn
Kỹ năng: HTML,CSS,JS,REACTJS,Firebase
Job: Junior ReactJS developer
Công ty: ĂN MẶN ĐÁI KHAI
```
## 1.1: HIỆU SUẤT
![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=toduyen&show_icons=true&theme=radical)
# Những gì đã làm
- [x] Đã viết xong chương 1
- [x] Đã viết xong chương 2
- [x] Đã viết xong chương 3
- [x] Đã edit lại và chỉnh sửa
- [ ] update...
## 1.2: TIẾN ĐỘ
Chương trình | Tài liệu
------------ | -------------
hoàn thành 90% | Tài liệu hoàn thành 96%

















# 2: Nâng cao kỹ năng kỹ thuật chuyên ngành
<p align="center">
  <img width="500" height="500" src="https://images.viblo.asia/74e0e748-dff2-4790-a202-f80b29519951.gif">
</p>

# 2.1: Dom là cái gì
DOM helps to manipulate data in an object-oriented model because the components in the DOM have a structure defined as objects, methods, properties to be easily retrieved. They are treated as nodes and are performed as DOM Trees.

```
<html>                                                   -> document node
<head>                                                   -> element node - head
    <title>
        HTML DOM                                               -> text node
    </title>                                                   -> element node - title
</head>                                                  
<body>                                                   -> element node - body
</body>                                                   
</html>   
```

## 2.2: DOM ngon vậy tại sao còn có visual DOM ?
<p align="center">
  <img width="500" height="500" src="https://i0.wp.com/programmingwithmosh.com/wp-content/uploads/2018/11/lnrn_0201.png?fit=1173%2C785&ssl=1">
</p>
We can see the image above, HTML DOM is structured as a tree. It is really delicious because it is possible to browse trees very easily. It's black, it's not easy to be fast.
<p align="center">
  <img width="460" height="460" src="https://images.viblo.asia/1a81fa13-edd6-4366-b47f-34d1f080ea4b.png">
</p>
However, do not misunderstand that reading and recording to the DOM of the browser is slow. This is not true. Fast DOM. Updating nodes in dom doesn't take longer than setting an attribute on a JavaScript object. It's a simple operation.

## 2.3: The Diffing Algorithm và những điều nên biết

<p align="center">
  <img width="460" height="400" src="https://miro.medium.com/max/4000/1*wHAx1KnP7obeybFXsL7-NA.png">
</p>

When diffing two trees, React first compares the two root elements. The behavior is different depending on the types of the root elements.

### 2.3.1: Elements Of Different Types
Whenever the root elements have different types, React will tear down the old tree and build the new tree from scratch. 
Going from ```<a> to <img>, or from <Article> to <Comment>, or from <Button> to <div>``` - any of those will lead to a full rebuild.

When tearing down a tree, old DOM nodes are destroyed. Component instances receive componentWillUnmount(). When building up a new tree, new DOM nodes are inserted into the DOM. Component instances receive UNSAFE_componentWillMount() and then componentDidMount(). Any state associated with the old tree is lost.
```
 <div>
  <Counter />
</div>
<span>
  <Counter />
</span>
```
    
This will destroy the old Counter and remount a new one
  
### 2.3.2: DOM Elements Of The Same Type
When comparing two React DOM elements of the same type, React looks at the attributes of both, keeps the same underlying DOM node, and only updates the changed attributes. For example:
```
<div className="before" title="stuff" />

<div className="after" title="stuff" />
```
By comparing these two elements, React knows to only modify the className on the underlying DOM node.When updating style, React also knows to update only the properties that changed. For example

```
<div style={{color: 'red', fontWeight: 'bold'}} />

<div style={{color: 'green', fontWeight: 'bold'}} />
```
When converting between these two elements, React knows to only modify the color style, not the fontWeight.

## 2.4: Recursing On Children
For example, when adding an element at the end of the children, converting between these two trees works well:

```
<ul>
  <li>first</li>
  <li>second</li>
</ul>

<ul>
  <li>first</li>
  <li>second</li>
  <li>third</li>
</ul>
```
React will match the two ```<li>first</li> trees, match the two <li>second</li> trees, and then insert the <li>third</li>``` tree.If you implement it naively, inserting an element at the beginning has worse performance. For example, converting between these two trees works poorly:

```
<ul>
  <li>Duke</li>
  <li>Villanova</li>
</ul>

<ul>
  <li>Connecticut</li>
  <li>Duke</li>
  <li>Villanova</li>
</ul>
```

### 2.4.1: Keys
In order to solve this issue, React supports a key attribute. When children have keys, React uses the key to match children in the original tree with children in the subsequent tree. For example, adding a key to our inefficient example above can make the tree conversion efficient:
```
<ul>
  <li key="2015">Duke</li>
  <li key="2016">Villanova</li>
</ul>

<ul>
  <li key="2014">Connecticut</li>
  <li key="2015">Duke</li>
  <li key="2016">Villanova</li>
</ul>
```
Now React knows that the element with key '2014' is the new one, and the elements with the keys '2015' and '2016' have just moved.

> Keys should be stable, predictable, and unique. Unstable keys (like those produced by Math.random()) will cause many component instances and DOM nodes to be unnecessarily recreated, which can cause performance degradation and lost state in child components.
