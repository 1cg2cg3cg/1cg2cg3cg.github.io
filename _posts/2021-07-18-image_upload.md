---
date: 2021-07-18
title: "github page에 이미지 추가하기"
excerpt: "github에서는 보이는데 github page에 안 보일 때"

tags: page image

categories: pagetip
#toc: true
#toc_sticky: true
---

상단 네비게이션 바(top navigation bar)를 수정하는 글을 작성하면서, 나중에 헷갈리지 않으려고 사진을 첨부하려고 했는데 생각보다 잘 안됐다.

시도했던 방법

### images 폴더를 만들고 그 안에 이미지 업로드 후 불러오기

![main](https://github.com/1cg2cg3cg/images/blob/main/page/image_upload/image_upload_main.png?raw=true)

우측 상단 ... 버튼을 눌러

![copy_path](https://github.com/1cg2cg3cg/images/blob/main/page/image_upload/copy_path.png?raw=true)

```
![before](images/top_nav_before.png)

![after](https://github.com/1cg2cg3cg/1cg2cg3cg.github.io/blob/b967bd157799a8bae3a3f819d56daf6157435074/images/top_nav_after.png)
```

before는 path로, after는 permalink를 사용해, markdown 문법을 사용해 이미지를 첨부했다.

before는 정상적으로 보이지만, after는 보이지 않았다.


![before_o_after_x](https://github.com/1cg2cg3cg/images/blob/main/page/image_upload/before_o_after_x.png?raw=true)

F12 관리자 도구를 사용해 이미지를 확인해보면,

```
<p>
  <img src="https://github.com/1cg2cg3cg/1cg2cg3cg.github.io/blob/b967bd157799a8bae3a3f819d56daf6157435074/images/top_nav_after.png" alt="after">
</p>
```

해당 링크로 이동하면, 원하는 사진이 잘 보이고 github에선 잘 보이는데 github page에서만 안 보인다면

브라우저 상단의 주소가 아니라 이미지 자체의 주소를 사용했는지 확인해야 한다. 이미지의 주소를 사용하면, 주소 뒤에 ?raw=true가 추가되고, 정상적으로 첨부된다.

![url_path](https://github.com/1cg2cg3cg/images/blob/main/page/image_upload/url_path.png?raw=true)

![image_path](https://github.com/1cg2cg3cg/images/blob/main/page/image_upload/copy_image_path.png?raw=true)


### 새로운 repository 만들어서, 동일한 방법 사용하기

pull 했을 때 이미지까지 딸려올 것 같아서, 앞으로는 image 저장을 위한 repository를 새로 만들어 정리하고 이미지 주소를 사용하는 방법을 사용할 것 같다.

검색에서 못봤는데 더 편한 방법으로(새로 추가된 것 같다) 파일을 드래그 앤 드롭하면, 자동으로 추가된다.

![drag_and_drop](https://user-images.githubusercontent.com/78636903/126053524-e05c071a-70a9-4322-b722-3d571c3304d7.png)

![attach](https://user-images.githubusercontent.com/78636903/126053530-20230def-d4a5-4b31-a4bf-e107027bc618.png)

사진이 다시 필요 없다면, 이 방법이 제일 편한 것 같다.
