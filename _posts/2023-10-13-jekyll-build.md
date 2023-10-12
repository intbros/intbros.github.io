---
title: "jekyll build --- layout: home # Index page ---"
date: "2023-10-13 00:31:25"
tags: ["jekyll"]
---
### github 블로그 배포 - 화면이 안나올 경우 (jekyll, Chiry)
<br>
github 블로그 왜 했을까???? 그냥 네이버나 티스토리로 간단히 글이나 올릴껄 ...
<br>
현재 후회 중이면서도 도전 정신이라고 해야 하나 끝까지 가보자는 마음에 오늘도 구글링 중입니다.
<br>
저는 Chiry 테마를 사용하고 있는데 처음에 포스트를 github에 푸쉬하고 나서부터는 포스트가 화면에 안보이는 현상이 있었습니다.

심지어 모바일 브라우저에서는 화면은 안보이고 " --- layout: home # Index page --- "라는 문구만 나오는 현상이 있었습니다.

저는 아래와 같은 순서로 진행하여 해결하였습니다.
<br>
<br>
github에 로그인 > Actions > Build and Deploy > Run workfow > Branch:main > Run workfow 
<br><br>
<br>
빌드가 완성되면 gh-pages라는 새로운 브랜치가 만들어진다는데 저는 gh-pages 브랜치가 아니고 main 브랜치에서 작업하고 있습니다.
<br>

