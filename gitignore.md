### git ignore 적용 안될때

```bash
git rm -r --cached .
git add .
git commit -m "fixed untracked files"
```


### 예제

```bash
# # 로 시작하는 줄은 주석에 해당한다. 

# 'file.ext' 이라는 이름의 파일을 ignore 처리한다
file.ext 

# ignore 규칙을 정의하는 줄에 주석을 함께 섞어 쓰는 것은 허용되지 않는다 
# 아래 줄은 'file.ext # not a comment' 라는 이름의 파일을 ignore 처리할 것이다 
file.ext # not a comment 
# 전체 경로를 통해 파일 ignore 처리하기 # 파일명만 기술된 규칙은 최상위 디렉토리뿐만 아니라 모든 서브디렉토리에 동일하게 적용된다 # 예) otherfile.ext 파일은 하부의 디렉토리 어디에 있던 모두 ignore 처리될 것이다 dir/otherdir/file.ext otherfile.ext # 디렉토리 전체를 ignore 처리하기 # 디렉토리 자체와 디렉토리 내의 모든 내용물들이 ignore 처리된다 bin/ gen/ # Glob 패턴 형식을 사용하여 특정 문자를 포함하는 경로를 ignore 처리할 수 있다 # 예를 들어, 아래의 규칙은 build/ 와 Build/ 두가지 경로 모두에 해당한다 [bB]uild/ # / 로 끝나지 않는 경로의 경우에는, 해당 규칙이 기술된 이름을 갖는 파일과 디렉토리 모두에 적용된다 # 따라서, 아래 예제는 `gen` 이라는 이름을 가진 파일들 뿐만 아니라 # 동일한 이름의(`gen`) 디렉토리 및 해당 디렉토리의 내용물까지 모두 ignore 처리하게 된다 bin gen # 파일을 확장자 별로 ignore 처리하기 # 아래 기술된 확장자를 갖는 현재 디렉토리와 # 모든 서브디렉토리 내의 파일들이 ignore 처리될 것이다 *.apk *.class # 특정 디렉토리 지정과 특정 확장자 지정 규칙을 혼합하여 사용하는 것도 가능하다 # 아래에 기술된 규칙이 ignore 처리할 파일들은 # 위에서 지정한 규칙들이 ignore 처리하는 파일들과 중복된다 java/*.apk gen/*.class # 최상위 디렉토리에 존재하는 파일을 ignore 처리하되, # 서브디렉토리 내의 동일한 이름을 갖는 파일들은 제외하고 싶다면 `/` 를 앞에 붙인다 /*.apk /*.class # DirectoryA 라는 이름의 디렉토리가 저장소 내 어떤 위치에 존재하던 # 모두 ignore 처리하고 싶다면 ** 를 앞에 붙인다 # / 를 마지막에 붙이는 것을 잊지 말아야 한다 # 그렇지 않으면 DirectoryA 라는 이름의 디렉토리 뿐만 아니라 파일들까지 ignore 처리하게 된다 **/DirectoryA/ # 이 규칙은 다음 경로들을 ignore 처리할 것이다: # DirectoryA/ # DirectoryB/DirectoryA/ # DirectoryC/DirectoryB/DirectoryA/ # 이 규칙은 DirectoryA 라는 이름의 파일을 ignore 처리하지는 않는다 (해당 파일이 어느 위치에 존재하든 무관) # DirectoryA 라는 이름의 디렉토리 하부에 존재하는 DirectoryB 디렉토리를 ignore 처리하되 # 두 디렉토리 사이에 몇 단계의 다른 경로가 포함되어도 상관없이 ignore 하고 싶다면, # 두 디렉토리 경로 사이에 ** 문자열을 포함시켜 규칙을 작성할 수 있다 DirectoryA/**/DirectoryB/ # 이 규칙은 다음 경로들을 ignore 처리할 것이다: # DirectoryA/DirectoryB/ # DirectoryA/DirectoryQ/DirectoryB/ # DirectoryA/DirectoryQ/DirectoryW/DirectoryB/ # 위에서 이미 살펴 보았듯이, 특정 파일들을 한꺼번에 ignore 처리하리 위해서 규칙 명세에 와일드카드를 이용할 수 있다 # 이 때, '*' 하나를 단독으로 명시할 경우, .gitignore 까지 포함하여 폴더 내의 모든 파일들이 (의도치 않게) ignore 처리되게 된다 # 이렇듯 와일드카드를 사용하되 특정 파일은 ignore 처리하지 않으려면, ! 를 이용하여 예외 처리를 할 수 있다 # 이렇게 예외처리로 명시된 파일은 ignore 목록에서 제외될 것이다: !.gitignore # 파일 이름 중에 해시(#) 문자가 존재할 경우, 백슬래시를 escape 문자로 이용하여 표기할 수 있다 # (1.6.2.1 버전 이후부터 지원) \#*#
```


- 출처
https://jojoldu.tistory.com/307
https://nochoco-lee.tistory.com/46

