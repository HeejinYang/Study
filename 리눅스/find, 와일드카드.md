파일을 찾는 명령어 find

find 장소 조건 조건값
-name
-user
-group
-type
-ls
-exec 명령어 {} \;

근데 우선 find명령어를 이용하려면 , 와일드 카드를 이해해야한다

표현식 (조건)

bash shell의 wildcard

와일드카드는 os가 아닌 쉘에 따라 다르다

```
* : 모든 문자 및 문자열
? : 모든 한 글자

[] : 기호 내의 모든 한 글자
[123456], [abcde], [1-6], [a-e]
!가 있으면 !을 뺀 모든 한 글자를 나타냄
[!123]abc = 4abc 5abc 6abc zabc

{} : 기호 내의 모든 문자열을 나타냄, ','로 구분한다
{unix, linux}_file_system = unix_file_system, linux_file_system
{}에 한단어만 있거나 아무것도 안 들어있으면 그냥 문자 '{'  '}'로 취급된다

```



---

쉘의 명령어 처리 순서

```
쉘은 와일드카드, 환경변수, 특수기호가 있는지 먼저 확인한다
' '로 감싼 문자는 그냥 순수 문자열로 처리된다
" "로 감싼 문자열안의 $, `, \는 쉘이 인식하고 처리한다 (변수에 관련된 기호들)



find / -type d -name '?asdf?' -ls -exec rm -r {} \;

/에서 이름이 ?asdf? 인 디렉터리 파일을 찾아라
결과를 ls -l 형식으로 출력, 해당 결과는 {}로 들어가며 이 결과에 대해 rm -r 명령을 실행한다
;는 -exec가 실행하는 명령의 끝을 나타낸다

{}는 그냥 문자로 처리되기 때문에 '' 을 감쌀 필요가 없고
;는 쉘이 해석하지 않도록 \를 붙인다
'?asdf'도 마찬가지로 쉘이 해석하지 않도록 ''로 감싸서 find명령어의 값으로 들어간다
```


-name 조건의 조건 값은 한개만 들어간다

출처: https://mamu2830.blogspot.com/2019/12/find.html