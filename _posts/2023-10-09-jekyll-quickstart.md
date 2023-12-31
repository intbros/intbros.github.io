---
title: "jekyll 빠른 설치 방법"
date: "2023-10-09 20:36:01"
tags: ["jekyll"]
---
Jekyll은 정적 사이트 생성기입니다. 즐겨찾는 마크업 언어로 작성된 텍스트를 받아 레이아웃을 사용하여 정적 웹사이트를 생성합니다. 사이트의 모양과 느낌, URL, 페이지에 표시되는 데이터 등을 조정할 수 있습니다.

### jekyll 빠른 설치
```
  gem install bundler jekyll

  jekyll new my-awesome-site

  cd my-awesome-site

  bundle exec jekyll serve

# => Now browse to http://localhost:4000
```


### Jekyll 설치 요구사항

- Ruby version 2.5.0 or higher
- RubyGems
- GCC and Make

가이드 및 자세한 내용은 아래 사이트에서 참조하십시오.
https://jekyllrb.com/docs/installation/#requirements

1. 아래 요구 사항들을 전부 설치
- Ruby version 2.5.0 or higher, including all development headers (check your Ruby version using ruby -v)
- RubyGems (check your Gems version using gem -v)
- GCC and Make (check versions using gcc -v,g++ -v, and make -v)


2. jekyll과 bundler gems 설치
```
gem install jekyll bundler
```

3. 새폴더에 jekyll 설치 ./myblog
```
jekyll new myblog
```

4. 새 디렉토리로 이동
```
cd myblog
```
5. 사이트를 구축하고 로컬 서버 실행
```
bundle exec jekyll serve
```
6. 브라우저에서 http://localhost:4000 확인

> Ruby 버전 3.0.0 이상을 사용하는 경우 5단계가 실패할 수 있습니다. 의존성에 webrick을 추가하여 수정할 수 있습니다: bundle add webrick
{: .prompt-danger }

> 원본 파일을 변경할 때마다 페이지를 자동으로 새로 고치는 데 사용할 --livereload 옵션을 전달합니다. bundle exec jekyll serve --livereload 
{: .prompt-warning }

이 과정 중에 오류가 발생하면 요구 사항에 모든 필수 구성 요소를 설치했는지 확인합니다. 여전히 문제가 있는 경우 문제 해결을 참조하십시오.

> 설치 방법은 운영 체제에 따라 다릅니다. OS별 지침은 가이드를 참조하십시오.
https://jekyllrb.com/docs/installation/#guides 
{: .prompt-warning }