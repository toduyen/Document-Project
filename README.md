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
  <img width="460" height="200" src="https://images.viblo.asia/74e0e748-dff2-4790-a202-f80b29519951.gif">
</p>

# 2.1: Dom là cái gì
DOM giúp thao tác với dữ liệu theo mô hình hướng đối tượng do các phần tử trong DOM có cấu trúc được định nghĩa thành các đối tượng, phương thức, thuộc tính để có thể truy xuất dễ dàng. Chúng được coi như các node và được biểu diễn dưới dạng DOM Tree.

```
<html>                                                   -> document node
<head>                                                   -> element node - head
    <title>
        HTML DOM                                         -> text node
    </title>                                             -> element node - title
</head>                                                  
<body>                                                   -> element node - body
</body>                                                   
</html>   
```

## 2.2: DOM ngon vậy tại sao còn có visual DOM ?
Chúng ta có thể thấy hình ở trên, HTML DOM được cấu trúc dạng cây. Thực sự rất ngon vì có thể duyệt cây rất dễ dàng. Thật là đen, ở đây không phải cứ dễ là tốc độ nhanh.
<p align="center">
  <img width="460" height="200" src="https://images.viblo.asia/1a81fa13-edd6-4366-b47f-34d1f080ea4b.png">
</p>
Tuy nhiên đừng hiểu nhầm việc đọc và ghi vào DOM của trình duyệt là chậm. Điều này không đúng. DOM nhanh. Việc cập nhật các node trong DOM không mất nhiều thời gian hơn việc thiết lập một thuộc tính trên một đối tượng JavaScript. Đó là một hoạt động đơn giản.

## 2.3: The Diffing Algorithm và những điều nên biết

<p align="center">
  <img width="460" height="200" src="https://miro.medium.com/max/4000/1*wHAx1KnP7obeybFXsL7-NA.png">
</p>

When diffing two trees, React first compares the two root elements. The behavior is different depending on the types of the root elements.

### 2.3.1: Elements Of Different Types
Whenever the root elements have different types, React will tear down the old tree and build the new tree from scratch. 
Going from /* <a> to <img>, or from <Article> to <Comment>, or from <Button> to <div> */ - any of those will lead to a full rebuild.

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

